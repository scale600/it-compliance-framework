# Audit Findings Report Template

> **Audit Period**: Q4 [Year] | **Report Date**: [Date]  
> **Classification**: Confidential  
> **Prepared By**: [Audit Team Lead] | **Reviewed By**: [CISO / Privacy Officer]

---

## 1. Executive Summary

### Overall Assessment

| Metric | Result |
|--------|--------|
| Overall Compliance Maturity Score | [XX]% |
| Previous Audit Score (if applicable) | [XX]% |
| Change | [+/-XX%] |
| Total Findings | [N] |
| Critical | [N] |
| High | [N] |
| Medium | [N] |
| Low | [N] |

### Key Observations

*[2–3 paragraph narrative summarizing the overall state of compliance, significant improvements since last audit, and top risks requiring management attention.]*

**Example**:
> The Q4 [Year] IT & OT Audit demonstrates an overall compliance maturity of 82%, an improvement of 6% from the previous audit cycle. Key improvements include full MFA deployment across IT systems and completion of the OT device inventory. However, three high-risk findings require immediate attention: (1) incomplete DSAR response tracking for former employees, (2) OT firmware patching gaps on legacy PLCs, and (3) two Tier 1 vendor DPAs that have expired without renewal.

---

## 2. Audit Scope & Methodology

### 2.1 Scope

| Dimension | Detail |
|-----------|--------|
| Audit Period | [Start Date] to [End Date] |
| Systems Audited | [List key systems] |
| Locations | [On-prem data centers, factories, cloud regions] |
| Frameworks Applied | NIST SP 800-53, ISO 27001, IEC 62443, GDPR Art. 32, CCPA § 1798.100 |

### 2.2 Methodology

- Document Review: [N] policies/procedures reviewed
- Interviews: [N] stakeholders across [N] departments
- Technical Testing: Vulnerability scans, configuration reviews, access control testing
- Sampling: [N] DSAR records, [N] access reviews, [N] vendor assessments

---

## 3. Domain Summary

| Domain | Score | Critical | High | Medium | Low | Trend |
|--------|-------|----------|------|--------|-----|-------|
| 1. Governance & Policy | [X/7] | [N] | [N] | [N] | [N] | [↑/↓/→] |
| 2. Data Inventory & RoPA | [X/8] | [N] | [N] | [N] | [N] | [↑/↓/→] |
| 3. Access Management | [X/10] | [N] | [N] | [N] | [N] | [↑/↓/→] |
| 4. Data Protection | [X/8] | [N] | [N] | [N] | [N] | [↑/↓/→] |
| 5. Vulnerability & Patch Mgmt | [X/9] | [N] | [N] | [N] | [N] | [↑/↓/→] |
| 6. Incident Response & Breach | [X/9] | [N] | [N] | [N] | [N] | [↑/↓/→] |
| 7. Privacy Controls | [X/10] | [N] | [N] | [N] | [N] | [↑/↓/→] |
| 8. OT/IoT Security | [X/10] | [N] | [N] | [N] | [N] | [↑/↓/→] |
| 9. Vendor / TPRM | [X/7] | [N] | [N] | [N] | [N] | [↑/↓/→] |
| 10. Logging & Monitoring | [X/7] | [N] | [N] | [N] | [N] | [↑/↓/→] |
| **TOTAL** | **[X/85]** | **[N]** | **[N]** | **[N]** | **[N]** | |

---

## 4. Detailed Findings

### Finding #001

| Field | Detail |
|-------|--------|
| **Finding ID** | FIND-[Year]-[NNN] |
| **Domain** | [Domain Name] |
| **Risk Rating** | [Critical / High / Medium / Low] |
| **Control Reference** | [e.g., 3.3 — Privileged access quarterly review] |
| **Condition** | *[What was observed? Be specific and factual.]* |
| **Criteria** | *[Which policy, standard, or regulation was violated? Cite the specific section.]* |
| **Cause** | *[Root cause analysis: why did this happen?]* |
| **Impact / Risk** | *[What is the potential consequence? Quantify if possible (e.g., "affects PII of ~500 employees")]* |
| **Recommendation** | *[Specific, actionable remediation steps.]* |
| **Management Response** | *[To be completed by management: agree/disagree, action plan, owner, due date.]* |
| **Evidence Attached** | [Screenshots, logs, interview notes — reference file names] |

---

### Finding #002

*[Repeat for each finding — Critical and High findings first]*

---

## 5. Positive Observations

*[Highlight areas of strong performance or significant improvement. Recognizing what's working builds credibility and morale.]*

**Example**:
> - MFA deployment reached 100% coverage across all IT and OT systems containing PII, up from 73% in the prior audit.
> - The Privacy Office processed all 47 DSARs received in the audit period within the required SLAs, with an average response time of 12 days.
> - OT device inventory was completed for all three factory locations, a significant milestone for the OT security program.

---

## 6. Prior Audit Findings — Status

| Finding ID | Description | Prior Rating | Current Status | Notes |
|------------|-------------|-------------|----------------|-------|
| FIND-2024-001 | [Description] | High | ✅ Closed | Retested on [Date] |
| FIND-2024-002 | [Description] | Medium | ⏳ In Progress | Extended to [Date] |
| FIND-2024-003 | [Description] | Low | ❌ Not Started | — |

---

## 7. Corrective Action Plan (CAP) Summary

*Detailed CAP tracking in [CAP Tracker](./cap-tracker.md).*

| Finding ID | Rating | Remediation Action | Owner | Due Date | Status |
|------------|--------|-------------------|-------|----------|--------|
| FIND-[Year]-001 | [Rtg] | [Action] | [Name] | [Date] | Open |
| FIND-[Year]-002 | [Rtg] | [Action] | [Name] | [Date] | Open |

---

## 8. Appendices

| Appendix | Description |
|----------|-------------|
| A | Audit Checklist (completed) |
| B | Evidence Index (list of all evidence collected) |
| C | Interview Log (date, participant, topics) |
| D | Vulnerability Scan Summary |
| E | DSAR Sample Test Results |
| F | Vendor Audit Summary |

---

## 9. Report Sign-Off

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Audit Team Lead | | | |
| CISO | | | |
| Privacy Officer | | | |
| CEO / Executive Sponsor | | | |

---

**Distribution**: CISO, Privacy Officer, CEO, Audit Committee, Legal Counsel  
**Retention**: 7 years per document retention policy
