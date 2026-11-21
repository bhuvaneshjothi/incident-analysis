# ATT&CK Mapping and Detection Ideas: Vendor Data Leak (Nov 2026)

**Status date:** November 19, 2026
All techniques below are **assessments** based on public reporting. None is confirmed by the affected companies.

| Tactic | Technique | Confidence | Data sources a SOC would use | Detection idea |
|---|---|---|---|---|
| Initial Access | T1199 Trusted Relationship | High | Vendor access logs, VPN and SSO logs, API logs | Alert on vendor accounts used outside agreed hours, locations or systems |
| Initial Access | T1078 Valid Accounts | Low | Identity provider sign-in logs | Alert on new country, new device or impossible travel for vendor accounts |
| Collection | T1213 Data from Information Repositories | Low to medium | Application and database audit logs | Alert on large exports from marketing or customer data platforms |
| Exfiltration | T1567 Exfiltration Over Web Service | Medium | Proxy, firewall and cloud storage logs | Alert on unusual outbound volume to file-sharing services |
| Impact | T1657 Financial Theft | High | Threat intelligence, leak-site monitoring | Monitor for company names on leak sites and start the response plan early |
| Downstream risk | T1566 Phishing | High (customer risk) | Email gateway logs, customer reports | Watch for lookalike domains and a rise in phishing reports |

See [`detections/README.md`](../../detections/README.md) for example queries.
