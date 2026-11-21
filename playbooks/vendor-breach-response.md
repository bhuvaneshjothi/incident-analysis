# Playbook: Third-Party (Vendor) Breach Response

**Use when:** a vendor reports a breach, or a leak site or news report names the organization or a vendor that holds its data.
**Goal:** understand exposure quickly, limit harm and communicate clearly.

## 1. Detect and triage (first hours)
- [ ] Record the source of the alert and the time it was received.
- [ ] Separate facts (vendor notice, official statement) from claims (attacker posts).
- [ ] Open an incident record and name an incident lead.
- [ ] Identify which vendor and which data sets are involved.

## 2. Scope the exposure
- [ ] List the data the vendor holds for the organization (fields, number of records, date range).
- [ ] List all accounts, API keys and connections the vendor has into the organization.
- [ ] Ask the vendor for logs, an incident summary and a timeline.
- [ ] Check internal logs for vendor account activity and large data transfers.

## 3. Contain
- [ ] Rotate vendor credentials, API keys and tokens.
- [ ] Disable or restrict vendor access until the vendor confirms the issue is contained.
- [ ] Block known malicious indicators when they are shared.

## 4. Monitor for follow-on abuse
- [ ] Watch for phishing that uses leaked details and lookalike domains.
- [ ] Check whether leaked emails match internal users, and review their sign-ins.
- [ ] Monitor leak sites for new posts.

## 5. Communicate
- [ ] Involve legal, privacy and communications teams early.
- [ ] Review legal notification duties for affected people and regulators.
- [ ] Publish a plain statement: what happened, what data, what is not affected, what to do.
- [ ] Give customers one official contact route.

## 6. Recover and improve
- [ ] Restore vendor access only after verification.
- [ ] Reduce the data shared with the vendor.
- [ ] Update contracts: security requirements and breach notice deadlines.
- [ ] Write a short lessons-learned report.
