# Playbook: Major Cloud Service Outage (SOC Triage)

**Use when:** a core cloud service (email, identity, collaboration) is unavailable for many users.
**Goal:** confirm whether the outage is a technical failure or an attack, keep communication working, and watch for abuse of the confusion.

## 1. Confirm the scope (first 15 minutes)
- [ ] Check the vendor's official health page and status channels.
- [ ] Record the incident IDs and the first and latest update times.
- [ ] Confirm whether the problem is vendor-side or local (network, DNS, identity, one tenant).
- [ ] Open an internal incident record with a named lead.

## 2. Check for signs of attack
- [ ] Review sign-in logs for unusual locations, spikes in failures or new devices.
- [ ] Check for denial-of-service indicators on the organization's own network edge.
- [ ] Review recent changes: patches, configuration, certificate or DNS changes.
- [ ] Compare vendor statements with internal evidence. Record any difference.

## 3. Keep communication working
- [ ] Switch to the out-of-band channel (phone tree, alternative messaging, status page hosted elsewhere).
- [ ] Send a short staff notice: what is affected, what is not, next update time.
- [ ] Tell staff that delayed email is expected and that important messages should be confirmed another way.

## 4. Watch for abuse of the outage
- [ ] Alert staff to phishing that claims to restore access or fix the outage.
- [ ] Monitor for lookalike domains and a rise in phishing reports.
- [ ] Watch for unusual sign-ins after service returns.

## 5. Recover and review
- [ ] Confirm services work for a sample of users in each location.
- [ ] Review queued or failed mail for critical messages.
- [ ] Keep a timeline of vendor statements and internal actions.
- [ ] Review service credit options and contract terms.
- [ ] Write a short lessons-learned report and update the continuity plan.
