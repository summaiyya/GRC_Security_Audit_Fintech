# GRC Security Audit — Fintech Platform (FinTrust United Africa)

> **Academic peer audit conducted as part of a GRC programme.** All systems audited were test instances. No real customer data was involved.

---

## Overview

This repository documents a full **IT General Controls (ITGC) security audit** of a simulated fintech platform — FinTrust United Africa — a cross-border mobile money application designed for payments across Nigeria, Kenya, and Ghana.

The audit was conducted as a structured peer engagement, simulating a real-world GRC consultancy assignment. The platform was approaching its launch date and required an independent assessment of its security posture and control environment before going live.

**Audit Outcome:** The platform was assessed as **NOT READY for commercial launch**. 17 of 20 IT controls failed, with 7 classified as Critical risk.

---

## My Role

- GRC Analyst — Team G
- Responsible for control testing documentation, evidence collection, risk scoring, and production of all audit deliverables
- Collaborated with penetration testers (SOC analysts and ethical hackers) to translate technical findings into structured GRC outputs

---

## Frameworks Applied

| Framework | Application |
|---|---|
| **ISO/IEC 27001:2022** | Control mapping and audit scope |
| **NIST Cybersecurity Framework (CSF)** | Risk categorisation and control alignment |
| **PCI-DSS v4.0** | Payment card data handling requirements |
| **NDPR (Nigeria Data Protection Regulation)** | Data privacy compliance considerations |

---

## Audit Scope — Controls Tested

| Domain | Controls Tested |
|---|---|
| Access Control (AC) | AC-01 through AC-04 |
| Identity & Authentication (ID) | ID-01, ID-02 |
| Cryptography (CR) | CR-01, CR-02 |
| Input & Injection Controls (IN) | IN-01, IN-02 |
| Business Logic (BL) | BL-01, BL-02, BL-03 |
| Log Management (LM) | LM-01, LM-02 |
| Configuration Management (CM) | CM-01, CM-02 |
| Resilience & Availability (RA) | RA-01 |
| Governance (GV) | GV-01, GV-02 |

---

## Key Findings Summary

| Severity | Count | Examples |
|---|---|---|
| 🔴 Critical | 7 | Unauthenticated API access, SQL injection, plaintext card storage |
| 🟠 High | 6 | Race condition exploits, account takeover, FX rate manipulation |
| 🟡 Medium | 4 | Session management failures, verbose error disclosure |
| 🟢 Low / Informational | 3 | Minor configuration gaps |

### Critical Highlights

- **Unauthenticated GraphQL API** — Full customer database accessible without login. Testers escalated privileges to admin, set arbitrary balances, and bypassed KYC — all without credentials.
- **SQL Injection** — Entire user email and password hash database extracted via a single unsanitised input field.
- **Broken Object Level Authorisation (BOLA/IDOR)** — Any logged-in user could access another customer's full profile, card numbers, CVV codes, and transaction history by changing one parameter in a request.
- **Race Condition (Fund Transfer & Bill Payment)** — Simultaneous requests caused the system to process payments before registering deductions, resulting in negative account balances.
- **Plaintext Card Storage** — Full PAN and CVV stored unencrypted in the database — a direct PCI-DSS violation.
- **No TLS/HTTPS** — All API traffic transmitted in plaintext over HTTP.

---

## Deliverables Produced

| Deliverable | Description |
|---|---|
| `ITGC_Audit_Matrix.xlsx` | 20-control testing matrix with results, evidence references, and findings |
| `Risk_Register.xlsx` | 20 risks scored by likelihood and impact (5×5 matrix), with remediation owners |
| `Evidence_Working_Paper.docx` | Full evidence documentation with 99 embedded screenshots mapped to controls |
| `Board_Risk_Report.docx` | One-page executive brief written for a non-technical board audience |
| `Audit_Presentation.pptx` | Findings presentation deck |

---

## Risk Scoring Methodology

Risks were scored using a **5×5 likelihood × impact matrix**:

- **Score 20–25** → Critical
- **Score 15–19** → High
- **Score 10–14** → Medium
- **Score 1–9** → Low

---

## Remediation Priorities

| Timeframe | Action |
|---|---|
| **Within 48 hours** | Enforce HTTPS. Block unauthenticated API access. |
| **Within 2 weeks** | Fix IDOR/BOLA across all endpoints. Remove CVV storage. |
| **Within 60 days** | Implement parameterised queries. Fix race conditions. Strengthen KYC. |
| **Within 90 days** | Deploy security monitoring. Commission independent re-test. |

---

## Skills Demonstrated

`GRC` `ITGC Auditing` `Risk Assessment` `ISO 27001` `NIST CSF` `PCI-DSS` `NDPR` `Evidence Documentation` `Risk Register` `Control Testing` `Executive Reporting` `Penetration Test Review` `OWASP Top 10` `SQL Injection` `IDOR` `API Security` `Race Conditions`

---

## Disclaimer

This audit was conducted in a controlled academic environment on a test instance of
