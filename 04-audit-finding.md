# 04 · Audit-Style Finding: Backups Not Tested

> **Practice exercise. Fictional organisation.** All details are invented.

[← Back to portfolio](../README.md)

| Field | Detail |
|---|---|
| **Finding ID** | NAH-2026-01 |
| **Title** | Backups are taken but never tested for restoration |
| **Rating** | 🟧 **High** |
| **Control area** | Essential Eight: Regular backups · NIST CSF 2.0: RC.RP (Incident Recovery Plan Execution), PR.DS-11 (Backups) |
| **Owner** | IT Provider (MSP), with Practice Manager oversight |

## Condition (what we found)

Practice files and exported PMS reports are copied by hand to a single USB hard drive about once a month. The drive is kept in an unlocked drawer at the main clinic's reception. Staff could not remember any attempt to restore data from it, and there are no records of a test restore. Microsoft 365 data (email, SharePoint, OneDrive) isn't backed up separately.

## Criteria (what should be happening)

- **ASD Essential Eight, ML1:** backups of important data are done and kept according to business continuity requirements, and **restoration is tested** as part of disaster recovery exercises.
- **Privacy Act 1988, APP 11:** take reasonable steps to protect personal information from misuse, interference and loss.
- **Good practice (3-2-1):** three copies of data, on two types of media, with one copy offsite or offline.

## Cause (why it happened)

- No one has formally been made responsible for backups.
- The backup process was set up in 2020 and hasn't been reviewed since.
- People assumed "we have a backup" meant "we can recover".

## Risk (why it matters)

If ransomware, hardware failure or accidental deletion hits the clinic, it may find out *during the incident* that its backups are incomplete, damaged or up to 30 days old. The likely result is days of disruption to bookings and billing, permanent loss of clinical notes, and a possible notifiable data breach if patient records can't be accessed or restored. Having a single drive in a public area also means it could be stolen or damaged.

**Linked risks:** R2 (Ransomware) and R5 (Backup failure) in the [Risk Register](01-risk-register.md).

## Recommendation

1. **Within 2 weeks:** formally make the MSP responsible for backups, with the Practice Manager as risk owner.
2. **Within 30 days:** set up **automated daily backups** of file data and M365, keeping **one copy offline or immutable**.
3. **Within 30 days:** carry out and **document a first test restore** (sample files, a mailbox and a PMS export).
4. **Ongoing:** test restores **every quarter**, record the results, and report any failures to the Practice Manager.
5. Move the USB drive to a locked location while the old process is phased out.

## Management response (example)

> *"Agreed. The MSP will start automated M365 and file backups by 15 December, with the first documented test restore by 31 December. The Practice Manager will review results quarterly."*
