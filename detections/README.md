# Detection Ideas

These examples show how a SOC could detect the **type** of activity seen in a vendor breach. They are not based on logs from the incident.

**Status key:** `Untested example` means the query has not been run in a lab. Change this label to `Tested in lab` only after it has been run on real or sample data. Field names differ between environments and must be adjusted.

| # | Detection | Platform | ATT&CK | Status |
|---|---|---|---|---|
| 1 | Vendor account sign-in from a new country | Splunk SPL | T1078, T1199 | Untested example |
| 2 | Unusually large outbound data volume per user | Splunk SPL | T1567 | Untested example |
| 3 | Many failed sign-ins followed by a success | Splunk SPL | T1110, T1078 | Untested example |
| 4 | Repeated SSH failures from one source | Wazuh rule | T1110 | Untested example |

---

## 1. Vendor account sign-in from a new country

Goal: find vendor or service accounts that sign in from a country not seen in the previous 30 days.

```spl
index=azure sourcetype="azure:aad:signin" user="*vendor*" earliest=-30d
| eval country=coalesce('location.countryOrRegion', country)
| stats earliest(_time) as first_seen, values(src_ip) as src_ips by user, country
| where first_seen > relative_time(now(), "-1d")
| table user, country, src_ips, first_seen
```

Triage notes: confirm the sign-in with the vendor contact, check MFA result, and review what the account accessed afterward.

## 2. Unusually large outbound data volume per user

Goal: find users or service accounts whose outbound data volume is far above their normal level.

```spl
index=proxy earliest=-7d
| bin _time span=1d
| stats sum(bytes_out) as daily_bytes by user, _time
| eventstats avg(daily_bytes) as avg_bytes, stdev(daily_bytes) as sd_bytes by user
| where daily_bytes > avg_bytes + (3 * sd_bytes) AND daily_bytes > 500000000
| table _time, user, daily_bytes, avg_bytes
```

Triage notes: check the destination (file-sharing or unknown hosts), the time of day, and whether a scheduled export explains the volume.

## 3. Many failed sign-ins followed by a success

Goal: find possible password guessing or reuse of leaked credentials that ends in a successful sign-in.

```spl
index=azure sourcetype="azure:aad:signin" earliest=-1h
| eval result=if(status.errorCode=0,"success","failure")
| stats count(eval(result="failure")) as failures, count(eval(result="success")) as successes by user, src_ip
| where failures >= 10 AND successes >= 1
| table user, src_ip, failures, successes
```

Triage notes: after a public leak, compare the leaked email addresses with the organization's users and review their recent sign-ins.

## 4. Repeated SSH failures from one source (Wazuh)

Goal: raise an alert when one source fails SSH authentication many times in a short period.

```xml
<group name="local,authentication_failures,">
  <rule id="100100" level="10" frequency="8" timeframe="120">
    <if_matched_sid>5716</if_matched_sid>
    <same_source_ip />
    <description>Possible brute force: repeated SSH failures from one source.</description>
    <mitre>
      <id>T1110</id>
    </mitre>
  </rule>
</group>
```

Place the rule in `/var/ossec/etc/rules/local_rules.xml` and restart the Wazuh manager. Rule ID 5716 is the built-in "sshd: authentication failed" rule.

---

## Next additions

- Run each query in the lab and record the result and screenshots.
- Add a false-positive note and a tuning note for each detection.
