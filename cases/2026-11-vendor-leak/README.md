# Vendor Data Leak Affecting JPMorgan Chase, Visa and Mastercard: Incident Analysis

**Status date:** November 19, 2026
**Type:** Public-source incident analysis (no private logs or internal data were used)
**Author:** [Your name] | [LinkedIn link]

---

## Summary

On November 19, 2026, a ransomware group called **n0n** published stolen data that it linked to JPMorgan Chase, Visa and Mastercard. The three companies state that the data came from **third-party service providers**, not from their own payment systems. They also state that card numbers and payment data were not affected.

The exposed data appears to be **marketing and customer-program records**: mainly names and email addresses, with some phone numbers and account IDs. The direct financial risk is low. The main risk for customers is **phishing**, because attackers now have real contact details.

This case shows a common lesson in security: a company can have strong internal defenses and still be exposed through the vendors that hold its data.

---

## Timeline

| Date | Event |
|---|---|
| Sept 2026 | n0n is first observed as a new data-theft extortion group. |
| Nov 16 (Mon) | n0n lists Visa, Mastercard and JPMorgan Chase on its leak site and starts a 48-hour countdown. On the same day, Chase customers report slow transactions and account access problems. |
| Early in the week | Visa states that it is aware of a breach at one of its third-party providers. |
| Nov 19 (Thu) | The countdown ends and n0n publishes the data. JPMorgan and Mastercard each state that a third-party provider was attacked. Visa states that its own systems were not involved. |

JPMorgan states that the Monday outage is **not related** to this attack.

---

## What data was exposed

| Company | Reported exposure | Source of claim |
|---|---|---|
| JPMorgan Chase | About 16,000 customer email addresses, some with phone numbers and account IDs. JPMorgan states that vendors held marketing data, possibly including names and emails. | Media reports and JPMorgan statement |
| Mastercard | About 2,000 entries. Mastercard states that a limited amount of information from a subset of cardholders in a specific benefit program was exposed. One researcher believes the records may be test data. | Mastercard statement and researcher opinion |
| Visa | Visa states that no card numbers or payment data were affected and that its systems were not involved. | Visa statement |

**What was not reported as exposed:** card numbers, passwords, customer funds, or the payment networks themselves.

---

## How big was the impact?

- **People affected:** thousands. The JPMorgan figure is the largest, at about 16,000 records.
- **Financial loss to customers:** none reported.
- **Service impact:** none reported from the leak itself. The Monday Chase outage is stated to be unrelated.
- **Market reaction:** shares of the three companies fell during Thursday trading, by roughly 0.7% to 3% depending on the company and report. This is a small move for companies of this size.

The scale is limited, but the leak still matters. Exposed contact details can be used in targeted scams for a long time after the event.

---

## What caused the attack?

**The exact cause has not been made public.** None of the companies has named the affected vendors or explained how the attackers entered them. Any explanation below is an assessment based on how similar incidents usually happen, and it is not a confirmed finding.

What is known:

1. The attackers are a **data-theft extortion group**. This type of group steals data first and then threatens to publish it unless a payment is made.
2. The victims state that the **breach happened at vendors**, and that the vendors held marketing or program data.
3. The leak followed a **public deadline**, which is typical extortion behavior.

What is not known:

- How the vendors were accessed (stolen credentials, a vulnerability, phishing, or another method).
- How long the attackers were inside before the leak.
- Whether the three incidents involved the same vendor or separate vendors.
- Whether n0n's claims about holding more data are true.

One security report notes that the evidence does not establish that n0n breached Visa, Mastercard or JPMorgan Chase directly. This matches the companies' statements.

---

## MITRE ATT&CK mapping (assessed, not confirmed)

The techniques below are the most likely fit for the reported behavior. Each one is labeled with its level of confidence.

| Tactic | Technique | Why it may apply | Confidence |
|---|---|---|---|
| Initial Access | **T1199 Trusted Relationship** | The data was reportedly taken from vendors that have a trusted relationship with the companies. | High (matches company statements) |
| Initial Access | **T1078 Valid Accounts** | Stolen or weak vendor credentials are a common way into third-party systems. | Low (not reported) |
| Collection | **T1213 Data from Information Repositories** | Marketing and customer-program data is usually stored in shared repositories or platforms. | Low to medium |
| Exfiltration | **T1567 Exfiltration Over Web Service** | Stolen data was later published, so it was moved out of the vendor environment. | Medium |
| Impact | **T1657 Financial Theft** | The group used a deadline and a leak site to pressure victims for payment (extortion). | High (matches reported behavior) |
| Downstream risk | **T1566 Phishing** | Leaked emails and phone numbers can be used to target customers. | High as a risk to customers |

---

## What could have been done better?

These points are general good practice. They are not claims that the companies failed to follow them.

1. **Vendor risk management.** Review the security of vendors before sharing data, and review it again on a regular schedule. Require security standards in contracts.
2. **Data minimization.** Share the least amount of data with vendors. Marketing partners rarely need account IDs or full contact records.
3. **Strong access control at vendors.** Require multi-factor authentication, limited privileges and short-lived access for every vendor account.
4. **Monitoring across the supply chain.** Track vendor activity and alerts, and watch leak sites and dark web sources for mentions of the company name.
5. **Fast breach notification rules.** Contracts should require vendors to report incidents within a short, fixed time.
6. **Clear public communication.** Early and plain statements reduce confusion. In this case, reports differed on how clearly each company confirmed its incident.
7. **Tested incident response.** Practice a vendor-breach scenario with legal, communications and security teams together.

---

## Key learnings

- **Third-party risk is a first-order risk.** Attackers often choose the weaker vendor instead of the stronger target.
- **Low-sensitivity data still has value.** Names and emails are enough to start a convincing phishing campaign.
- **Claims and facts must be separated.** Attackers exaggerate, and early reports contain errors. For example, one researcher questioned whether some leaked Mastercard records were real.
- **Timing can mislead.** The Chase outage happened on the same day as the leak-site listing, but the company states that the two events are unrelated. A SOC analyst should not link events without evidence.
- **Extortion deadlines are a signal.** A countdown on a leak site gives defenders a short window to investigate and prepare statements.

---

## What customers should be aware of

Customers of these companies should:

- **Expect phishing.** Emails, texts and calls that mention a bank or card brand may be scams that use leaked contact details.
- **Avoid links and attachments** in unexpected messages. Open the official app or type the official website address instead.
- **Never share** passwords, one-time codes or card numbers by email, text or phone, even if the caller knows personal details.
- **Turn on transaction alerts** and review statements for unfamiliar charges.
- **Use multi-factor authentication** on banking and email accounts, and use a unique password for each account.
- **Report suspicious messages** to the bank or card issuer using official contact details.

---

## Limitations of this analysis

- It uses public news reports and company statements only, as of November 19, 2026.
- Some details come from the attackers' own claims and are unverified.
- The vendors, the attack method and the full data set have not been disclosed.
- The ATT&CK mapping is an assessment and may change if more facts are published.

---

## Sources

- WTAE: Visa, Mastercard and JPMorgan Chase customer data reportedly compromised in cyberattack
  https://www.wtae.com/article/visa-mastercard-and-jpmorgan-chase-cyberattack/74478458
- ABC7: JPMorganChase, Mastercard, Visa report cyberattack on third-party service providers
  https://abc7news.com/story/jpmorganchase-reports-cyberattack-third-party-service-providers/20055320/
- Stockanalysis: Hackers leak data on thousands of Visa, Mastercard and JPMorgan Chase customers after attacks on vendors
  https://stockanalysis.com/news/jpmorgan-visa-mastercard-customer-data-leaked/
- Yahoo Finance: Visa, Mastercard, JPMorgan Hit By Reported Data Leak, Payment Information Not Affected
  https://finance.yahoo.com/technology/articles/visa-mastercard-jpmorgan-hit-reported-165341009.html
- The Cyber Security Guru: n0n leak-site claims against Visa, Mastercard and JPMorgan Chase, what is verified
  https://thecybersecguru.com/news/n0n-claims-visa-mastercard-jpmorgan-chase/
- World Today News: Ransomware group leaks JPMorgan Chase, Visa, Mastercard customer data
  https://www.world-today-news.com/ransomware-group-leaks-jpmorgan-chase-visa-mastercard-customer-data-firms-say-no-financial-info-compromised/
- MITRE ATT&CK: https://attack.mitre.org/
