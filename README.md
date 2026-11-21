# SOC Incident Analysis Portfolio

This repository contains short, plain-language analyses of real security incidents, written from the point of view of a defensive (SOC) analyst. Each case separates **confirmed facts** from **unverified claims**, maps the activity to **MITRE ATT&CK**, and ends with **practical detection and prevention ideas**.


## Cases

| Date | Case | Type | Key lesson |
|---|---|---|---|
| Nov 2026 | [Vendor data leak affecting JPMorgan Chase, Visa and Mastercard](cases/2026-11-vendor-leak/README.md) | Third-party breach, data-theft extortion | Vendor access and shared data are part of the attack surface |

New cases are added on a regular schedule. Each case follows the same [template](templates/case-template.md).

---

## Repository map

| Folder | Purpose |
|---|---|
| `cases/` | Incident write-ups, one folder per case, with ATT&CK mapping and timeline |
| `detections/` | Example detection ideas in Splunk SPL and Wazuh, with a clear tested or untested label |
| `playbooks/` | One-page response checklists for common incident types |
| `templates/` | The standard case brief format |

---

## Method

1. Collect public reporting and official statements only.
2. Separate confirmed facts, company statements and attacker claims.
3. Build a timeline and state what is not known.
4. Map likely techniques to MITRE ATT&CK, with a confidence level for each.
5. Describe what an analyst would monitor, and what prevention would have reduced the risk.

## Honesty note

No private logs or internal company data are used. Where a detection query has not been tested in a lab, it is labeled as an example. Assessments are labeled as assessments.
