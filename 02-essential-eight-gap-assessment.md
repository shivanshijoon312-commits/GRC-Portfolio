# 02 · Essential Eight Gap Assessment (Maturity Level 1): Northside Allied Health

> **Practice exercise. Fictional organisation.** All names, systems and findings are invented. Based on the ASD Essential Eight Maturity Model. Check the latest version on cyber.gov.au before reusing.

[← Back to portfolio](../README.md)

## Scope & approach

- **Target:** Maturity Level 1 (ML1), the right starting point for a small clinic facing opportunistic, commodity attacks
- **In scope:** 22 Windows PCs, 3 laptops, Microsoft 365 tenant, cloud practice management system (PMS)
- **Method:** (simulated) interview with the Practice Manager and the managed IT provider, review of M365 admin settings, and a sample check of 5 PCs
- **Status key:** ✅ Met · 🟡 Partially met · ❌ Not met

## Summary

| Strategy | Status | Priority |
|---|---|---|
| 1. Patch applications | 🟡 Partial | High |
| 2. Patch operating systems | 🟡 Partial | High |
| 3. Multi-factor authentication | ❌ Not met | **Critical** |
| 4. Restrict administrative privileges | ❌ Not met | High |
| 5. Application control | ❌ Not met | Medium |
| 6. Restrict Microsoft Office macros | ✅ Met | — |
| 7. User application hardening | 🟡 Partial | Medium |
| 8. Regular backups | ❌ Not met | **Critical** |

**Overall: Maturity Level 0.** One strategy meets ML1 and three partly meet it. Fixing MFA and backups first would remove the two most serious exposures.

## Detailed assessment

### 3. Multi-factor authentication ❌ (Critical)
| | |
|---|---|
| **ML1 intent** | Stop stolen passwords alone from giving access to internet-facing services |
| **Evidence expected** | MFA enforced (e.g. Conditional Access or Security Defaults) for all M365 users; MFA on the PMS |
| **Observed gap** | Security Defaults turned off; 4 of 25 users have enrolled MFA voluntarily; the PMS supports MFA but it isn't enabled |
| **Recommendation** | Turn on Security Defaults (or a Conditional Access policy) for all users; enable MFA in the PMS; brief staff before the rollout |
| **Linked risk** | R1, R3 |

### 8. Regular backups ❌ (Critical)
| | |
|---|---|
| **ML1 intent** | Important data can be recovered after ransomware, deletion or failure |
| **Evidence expected** | Backups done and kept to a defined schedule; restores tested; unprivileged accounts can't change or delete backups |
| **Observed gap** | Monthly manual copy to one USB drive at reception; never test-restored; M365 data not backed up separately |
| **Recommendation** | Automated daily backup of M365 and file data; a copy kept offline or immutable; documented quarterly test restores |
| **Linked risk** | R2, R5. See [audit finding 04](04-audit-finding.md) |

### 4. Restrict administrative privileges ❌ (High)
| | |
|---|---|
| **ML1 intent** | Limit what an attacker can do if a user account is compromised |
| **Evidence expected** | Staff use standard accounts day to day; admin rights only for staff who need them, through separate admin accounts |
| **Observed gap** | All 5 sampled PCs had the daily user as local administrator; the Practice Manager's everyday M365 account is a Global Admin |
| **Recommendation** | Remove local admin rights from staff; create separate admin accounts used only for admin tasks |
| **Linked risk** | R2, R3 |

### 1 & 2. Patch applications / operating systems 🟡 (High)
| | |
|---|---|
| **ML1 intent** | Close known vulnerabilities quickly, especially on internet-facing systems |
| **Evidence expected** | Patches for internet-facing services and common applications applied within 2 weeks (48 hours where an exploit exists); unsupported software removed |
| **Observed gap** | Windows Update is on, but staff often defer restarts. 2 PCs were 3 months behind. One reception PC runs an unsupported PDF reader |
| **Recommendation** | Have the MSP manage patching centrally with forced restarts out of hours; remove unsupported software; report patch status monthly |
| **Linked risk** | R2 |

### 5. Application control ❌ (Medium)
| | |
|---|---|
| **Observed gap** | No application control; users can run any executable from Downloads |
| **Recommendation** | Start with reception and shared PCs: allow only approved applications (e.g. WDAC or AppLocker, managed by the MSP) |

### 7. User application hardening 🟡 (Medium)
| | |
|---|---|
| **Observed gap** | Browsers up to date, but Internet Explorer 11 is still turned on and browser security settings aren't centrally managed |
| **Recommendation** | Turn off IE11; apply baseline browser settings through Intune |

### 6. Restrict Microsoft Office macros ✅
Macros from the internet are blocked by M365 defaults, and no business process needs macros. **No action. Keep monitoring.**

## Suggested roadmap

| Timeframe | Actions |
|---|---|
| **Next 2 weeks** | MFA for M365 and the PMS · start automated backups |
| **Within 30 days** | Remove local admin rights · managed patching · first test restore |
| **Within 90 days** | Application control on shared PCs · browser hardening · reassess against ML1 |
