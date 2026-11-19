# 01 · Risk Register: Northside Allied Health

> **Practice exercise. Fictional organisation.** All names, systems and figures are invented.

[← Back to portfolio](../README.md)

## Context

| Item | Detail |
|---|---|
| Organisation | Northside Allied Health (fictional), 25 staff, 2 Melbourne clinics |
| Key information assets | ~8,000 patient records (health information) in a cloud practice management system (PMS); Microsoft 365 email and SharePoint; card payments through an integrated terminal |
| Legal / regulatory | Privacy Act 1988 (health information is *sensitive information*), Notifiable Data Breaches (NDB) scheme, Health Records Act 2001 (Vic) |
| Risk owner (overall) | Practice Manager |
| Assessment date | Practice exercise, 2026 |

## Scoring method

**Risk rating = Likelihood (1–5) × Consequence (1–5)**

| Score | Rating | Expected response |
|---|---|---|
| 15–25 | **Extreme** | Treat immediately; report to owners |
| 10–14 | **High** | Treat within 30 days |
| 5–9 | **Medium** | Treat within 90 days |
| 1–4 | **Low** | Accept and monitor |

Likelihood: 1 Rare · 2 Unlikely · 3 Possible · 4 Likely · 5 Almost certain
Consequence: 1 Insignificant · 2 Minor · 3 Moderate · 4 Major · 5 Severe (e.g. notifiable breach of health data, clinics unable to operate)

## Register

| ID | Risk | NIST CSF | Existing controls | L | C | Inherent | Recommended treatment | Owner | Target (residual) |
|---|---|---|---|---|---|---|---|---|---|
| R1 | **Phishing leads to compromised M365 account**: an attacker reads patient emails and uses the account to send invoice fraud | PR.AA, PR.AT | Default spam filtering; no phishing training | 4 | 4 | **16 Extreme** | Enforce MFA for all M365 accounts; quarterly phishing awareness session; turn on external-sender tagging | Practice Manager | L2 × C4 = 8 Medium |
| R2 | **Ransomware encrypts clinic PCs and file shares**, stopping bookings and billing | PR.PS, RC.RP | Consumer antivirus on PCs; patches applied "when prompted" | 3 | 5 | **15 Extreme** | Centrally managed patching (Essential Eight ML1); application control on reception PCs; tested offline backups (see R5) | IT Provider (MSP) | L2 × C4 = 8 Medium |
| R3 | **Unauthorised access to patient records** through shared or leftover PMS logins (e.g. former staff) | PR.AA | Individual logins exist, but reception shares one account; no offboarding checklist | 3 | 4 | **12 High** | Remove shared accounts; offboarding checklist with same-day access removal; quarterly user access review | Practice Manager | L1 × C4 = 4 Low |
| R4 | **Lost or stolen laptop** used for home telehealth exposes patient data | PR.DS | Windows password only | 3 | 4 | **12 High** | BitLocker full-disk encryption; Intune remote wipe; screen-lock policy | IT Provider (MSP) | L3 × C2 = 6 Medium |
| R5 | **Backups fail when needed**: SharePoint and local files are not recoverable after an incident | RC.RP, PR.DS | Monthly backup to a USB drive kept at reception; never test-restored | 3 | 4 | **12 High** | Automated daily backups with one copy offline/immutable; quarterly test restore with results recorded (see [finding 04](04-audit-finding.md)) | IT Provider (MSP) | L1 × C3 = 3 Low |

## Heat map (inherent risk)

| Likelihood ↓ / Consequence → | 1 Insignificant | 2 Minor | 3 Moderate | 4 Major | 5 Severe |
|---|---|---|---|---|---|
| **5 Almost certain** | | | | | |
| **4 Likely** | | | | 🟥 R1 | |
| **3 Possible** | | | | 🟧 R3, R4, R5 | 🟥 R2 |
| **2 Unlikely** | | | | | |
| **1 Rare** | | | | | |

🟥 Extreme · 🟧 High

## Key takeaways for the Practice Manager

1. **Turn on MFA this week.** It's the cheapest, fastest control and cuts the top-rated risk (R1) the most.
2. **R2 and R5 are linked.** Ransomware becomes survivable once backups are automated, kept partly offline, and *proven* to restore.
3. **Health information is sensitive under the Privacy Act.** A breach affecting patients is likely to be notifiable to the OAIC and to patients, so access control (R3) and encryption (R4) also protect the clinic's legal position.
4. Review this register **every quarter** and after any incident or major system change.
