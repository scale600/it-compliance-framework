# Annual IT & OT Security and Privacy Audit Program

> **Version**: 2.0 | **Classification**: Internal — Confidential  
> **Audit Owner**: CISO + Privacy Officer  
> **Last Updated**: [Date] | **Next Audit Cycle**: Q4 [Year]

---

## 1. Purpose & Objectives

This document defines the **Annual IT & OT Security and Privacy Audit Program** for [Company Name]. The program provides a structured methodology to:

1. **Verify** compliance with GDPR, CCPA/CPRA, and internal security policies
2. **Identify** control gaps, risks, and areas for improvement
3. **Validate** the effectiveness of technical and organizational security measures
4. **Provide** evidence of ongoing compliance for regulatory inquiries and customer audits
5. **Drive** continuous improvement through a structured Corrective Action Plan (CAP) process

---

## 2. Scope

### 2.1 In-Scope Systems

| Domain | Systems |
|--------|---------|
| **Enterprise IT** | ERP (SAP/Oracle), CRM (Salesforce), HRIS (Workday), WMS, Email (O365), Identity (Okta), Endpoint (Intune) |
| **Operational Technology (OT)** | MES, PLC/SCADA, IoT sensor networks, CCTV, Access control, Data historians |
| **Cloud Infrastructure** | AWS (us-east-1, us-west-2), Azure (East US) |
| **Data Flows** | All cross-border transfers (EU-US, US-APAC), IT/OT integration points |
| **Vendors** | High-risk Tier 1 processors (payroll, cloud, logistics) — sampled |
| **Physical Security** | Data centers, factory floor access, server rooms |

### 2.2 Out of Scope (Unless Triggered)

- Financial / SOX ITGC audits (separate audit)
- Product quality audits (FDA/ISO — separate process)
- Environmental health & safety audits (separate)

---

## 3. Audit Frequency & Triggers

| Type | Frequency | Trigger |
|------|-----------|---------|
| **Scheduled Annual Audit** | Q4 each fiscal year | Per annual calendar |
| **Ad-Hoc Audit** | As needed | Major system implementation, Security Incident, regulatory change, M&A activity |
| **Vendor Audit** | Annual (Tier 1), Biannual (Tier 2) | Per TPRM schedule |

---

## 4. Audit Methodology

### 4.1 Approach

The audit follows a **risk-based** approach combining:

| Method | Description |
|--------|-------------|
| **Document Review** | Review of policies, RoPA, DPA, incident reports, training records, previous audit findings |
| **Interviews & Walkthroughs** | Process walkthroughs with system owners, HR, Supply Chain, Production teams |
| **Technical Testing** | Vulnerability scans, configuration reviews, access control testing, penetration testing (annual) |
| **Sampling** | Statistical sampling of DSAR responses (10 most recent), access reviews (quarterly), PII records (random) |

### 4.2 Audit Standards & Frameworks

| Framework | Application |
|-----------|-------------|
| **NIST SP 800-53** | Primary security control framework; mapped to GDPR/CCPA |
| **ISO 27001** | Information Security Management System reference |
| **IEC 62443** | OT/IoT security controls |
| **GDPR Art. 32** | Security of processing |
| **CCPA § 1798.100(e)** | Reasonable security procedures |

---

## 5. Audit Domains & Control Areas

### Domain 1: Governance & Policy

| Control | Test Procedure | Evidence |
|---------|---------------|----------|
| Policies current and approved | Review policy version dates and approval records | Signed policies; meeting minutes |
| Roles & responsibilities documented | Interview CISO, Privacy Officer, system owners | Org charts; RACI matrices |
| Annual review cycle maintained | Check review dates for all policies | Review logs |
| Privacy Committee active | Review quarterly meeting minutes and attendance | Meeting minutes |

### Domain 2: Data Inventory & RoPA Accuracy

| Control | Test Procedure | Evidence |
|---------|---------------|----------|
| RoPA complete and current | Sample 10 processing activities; trace to actual systems | RoPA; system screenshots |
| New processing activities captured | Review change management records for last 12 months | Change tickets; RoPA updates |
| PII classification accurate | Sample 5 data stores; verify classification tier | Data store configs; classification tags |
| Data minimization enforced | Review 5 data collection forms/processes | Collection forms; retention schedules |

### Domain 3: Access Management

| Control | Test Procedure | Evidence |
|---------|---------------|----------|
| RBAC implemented | Review role definitions; sample 10 users | Okta group membership; role definitions |
| MFA enforced for PII systems | Test 5 PII-containing systems for MFA prompt | MFA configuration; login screenshots |
| Privileged access reviewed quarterly | Review last 4 quarterly access reviews | Review logs; manager sign-offs |
| Offboarding revokes access promptly | Sample 5 terminated employees (last 3 months) | Termination tickets; access logs |
| No shared/generic accounts | Scan for generic accounts; review justification | Account inventory |

### Domain 4: Data Protection

| Control | Test Procedure | Evidence |
|---------|---------------|----------|
| Encryption at rest (AES-256) | Sample 5 databases/storage buckets | Encryption configuration |
| Encryption in transit (TLS 1.3) | Test 5 endpoints; review certificate configs | SSL Labs scan; certificate inventory |
| DLP rules active | Review DLP policy; test with sample PII pattern | DLP console; test results |
| Retention enforced | Sample 10 records across categories; verify deletion | Retention logs; deletion confirmations |
| Backups encrypted and tested | Review backup config; test restore of 1 backup | Backup config; restore test log |

### Domain 5: Vulnerability & Patch Management

| Control | Test Procedure | Evidence |
|---------|---------------|----------|
| Monthly vulnerability scans | Review last 12 scan reports | Scan reports; issue tracker |
| Critical patch SLA (48 hours) | Sample 5 critical vulnerabilities from last year | Patch tickets; timelines |
| OT device patching | Review OT patch log (last 6 months) | Patch logs; maintenance windows |
| Penetration test (annual) | Review most recent pen test report | Pen test report; remediation log |

### Domain 6: Incident Response & Breach

| Control | Test Procedure | Evidence |
|---------|---------------|----------|
| IR plan current and tested | Table-top exercise within last 12 months | Exercise report; lessons learned |
| Breach notification SLA tested | Simulated breach: time to notification | Exercise timeline; notifications |
| GDPR 72-hour notification flow | Test notification to supervisory authority | Exercise documentation |
| Incident log maintained | Review incident tracker for completeness | Incident log |
| Root cause analysis for all P1/P2 | Sample 3 incidents | RCA documents |

### Domain 7: Privacy Controls

| Control | Test Procedure | Evidence |
|---------|---------------|----------|
| DSAR process functional | Submit 3 test DSARs (Access, Delete, Correct) | DSAR tracker; responses |
| DSAR response within SLA | Check response times for last 10 DSARs | DSAR tracker; timestamps |
| Consent records maintained | Sample 10 consent records | Consent database; timestamps |
| Cookie consent banner functional | Test website cookie banner | Screenshots; cookie scan |
| DPIA completed for high-risk | Verify DPIA exists for all high-risk processing | DPIA documents; RoPA |

### Domain 8: OT/IoT Security (Manufacturing Specific)

| Control | Test Procedure | Evidence |
|---------|---------------|----------|
| OT network segmentation | Review network diagrams; test segmentation | Network diagrams; firewall rules |
| IoT device inventory current | Sample 20 IoT devices against inventory | Device inventory; discovery scan |
| OT change management | Review 5 OT change records | Change tickets; approvals |
| OT remote access controlled | Test OT remote access: MFA, jump host only | Access config; session logs |
| OT security monitoring | Check if OT traffic analyzed by SIEM | SIEM config; alert rules |

### Domain 9: Vendor / TPRM

| Control | Test Procedure | Evidence |
|---------|---------------|----------|
| DPA executed for all PII processors | Sample 10 vendors; check for DPA | DPA documents |
| Vendor risk assessments current | Review Tier 1 vendor assessments | Risk assessment documents |
| Annual vendor audits performed | Check audit schedule and completion | Audit reports |
| Contract audit clauses exercised | Review whether audit rights were used | Audit records |

### Domain 10: Logging & Monitoring

| Control | Test Procedure | Evidence |
|---------|---------------|----------|
| SIEM operational and tuned | Review SIEM dashboard; sample alert handling | SIEM console; alert logs |
| Audit logs immutable | Verify log integrity controls | Log config; access restrictions |
| Log retention ≥ 1 year | Check log archive; verify oldest logs available | Log archive; retention config |
| PII access logged | Generate PII access report; verify completeness | Access logs; audit trail |

---

## 6. Audit Execution Timeline

### Q4 Annual Audit Schedule

| Week | Activity | Participants |
|------|----------|-------------|
| W-4 | Audit planning: scope confirmation, resource allocation, checklist review | CISO, Privacy Officer, Internal Audit |
| W-3 | Document request sent to system owners | Audit Team |
| W-2 to W-1 | Document review + Interviews | Audit Team + System Owners |
| W1 to W2 | Technical testing (scans, config reviews, sampling) | IT Security + Audit Team |
| W3 | Findings analysis and risk rating | Audit Team |
| W4 | Draft report + Management review | Audit Team, CISO, Privacy Officer |
| W4+1 | Final report issuance + CAP assignment | Executive Leadership |

---

## 7. Audit Team

| Role | Responsibility |
|------|---------------|
| **CISO** | Audit sponsor; technical oversight; CAP sign-off |
| **Privacy Officer** | Privacy domain lead; RoPA/DSAR verification |
| **Internal Audit Manager** | Methodology; independence; report quality |
| **IT Security Lead** | Technical testing; evidence collection |
| **OT Engineering Lead** | OT domain testing; IEC 62443 expertise |
| **HR, Legal, Supply Chain Reps** | Domain SME interviews; evidence provision |
| **External Auditor** (optional, every 2-3 years) | Independent verification; specialized OT testing |

---

## 8. Reporting

### 8.1 Report Structure

1. **Executive Summary** (1 page)
2. **Audit Scope & Methodology**
3. **Overall Assessment** (Compliance Maturity Rating)
4. **Findings by Domain** — see [Audit Report Template](./audit-report-template.md)
5. **Corrective Action Plan (CAP)** — see [CAP Tracker](./cap-tracker.md)
6. **Appendices**: Test evidence, interview notes, raw scan data

### 8.2 Risk Rating Criteria

| Rating | Definition | Response Timeline |
|--------|-----------|-------------------|
| **Critical** | Immediate threat to data subjects or regulatory non-compliance with significant fine exposure | 24 hours — emergency remediation |
| **High** | Significant control gap with likely exploitation or material non-compliance | 30 days — prioritized CAP |
| **Medium** | Control weakness requiring improvement but not immediately exploitable | 90 days — scheduled remediation |
| **Low** | Minor issue; best practice enhancement | Next audit cycle or continuous improvement |

---

## 9. Follow-Up & Remediation

### 9.1 CAP Process

1. Each finding receives a CAP entry with owner and due date
2. High/Critical findings reviewed biweekly until closure
3. Closure verified through re-testing (not self-attestation)
4. CAP tracker published to executive leadership monthly

### 9.2 Escalation

- Critical findings: reported to CEO and Board within 24 hours
- High findings not remediated by due date: escalated to CISO → CEO
- Pattern of medium findings across domains: presented at Privacy Committee

---

## 10. Policy Integration

Audit findings drive updates to:

- [GDPR & CCPA Policy](../gdpr-ccpa/policy-template.md) — within 30 days of report
- [RoPA](../gdpr-ccpa/ropa-template.md) — updated for any new/changed processing
- [TPRM Framework](../tprm/tprm-framework.md) — vendor findings trigger contract reviews
- [Incident Response Plan](../gdpr-ccpa/breach-response-plan.md) — lessons learned from table-top exercises

---
