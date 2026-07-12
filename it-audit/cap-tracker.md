# Corrective Action Plan (CAP) Tracker

> **Audit Period**: Q4 [Year] | **Last Updated**: [Date]  
> **Owner**: CISO / Privacy Officer  
> **Review Cadence**: Biweekly for Critical/High; Monthly for Medium/Low

---

## Active CAP Items

| CAP ID | Finding ID | Risk | Domain | Finding Summary | Remediation Action | Owner | Opened | Target Close | Actual Close | Status | Evidence |
|--------|------------|------|--------|-----------------|-------------------|-------|--------|-------------|-------------|--------|----------|
| CAP-[Year]-001 | FIND-[Year]-001 | Critical | [Domain] | [Summary] | [Action] | [Name] | [Date] | [Date] | | 🔴 Open | [Link] |
| CAP-[Year]-002 | FIND-[Year]-002 | High | [Domain] | [Summary] | [Action] | [Name] | [Date] | [Date] | | 🟡 In Progress | [Link] |
| CAP-[Year]-003 | FIND-[Year]-003 | Medium | [Domain] | [Summary] | [Action] | [Name] | [Date] | [Date] | | 🟢 On Track | [Link] |

---

## CAP Item Detail Template

### CAP-[Year]-NNN

| Field | Detail |
|-------|--------|
| **CAP ID** | CAP-[Year]-NNN |
| **Linked Finding** | [FIND ID] |
| **Risk Rating** | [Critical / High / Medium / Low] |
| **Finding Summary** | [Brief description of the issue] |
| **Root Cause** | [Why the issue exists] |
| **Remediation Plan** | [Step-by-step plan. Be specific about what will be done, by whom, and when.] |
| **Milestone 1** | [Description] — Due: [Date] — Status: [ ] |
| **Milestone 2** | [Description] — Due: [Date] — Status: [ ] |
| **Milestone 3** | [Description] — Due: [Date] — Status: [ ] |
| **Owner** | [Name / Role] |
| **Target Close Date** | [Date] |
| **Verification Method** | [How will closure be verified? E.g., retest by audit team, evidence review, external assessment] |
| **Risk Accepted?** | [Yes/No] If Yes — [Acceptance rational and approver] |
| **Status Updates** | |
| [Date] | [Update] |
| [Date] | [Update] |

---

## Status Definitions

| Status | Symbol | Definition |
|--------|--------|------------|
| **Open** | 🔴 | Not yet started or awaiting resources |
| **In Progress** | 🟡 | Remediation actively underway |
| **On Track** | 🟢 | Progressing per plan; expected to meet target date |
| **At Risk** | 🟠 | Behind schedule; target date at risk without intervention |
| **Overdue** | 🔴🔴 | Past target close date; escalation triggered |
| **Closed** | ✅ | Remediation complete and verified |
| **Risk Accepted** | ⬜ | Management accepted the risk without remediation |

---

## Escalation Matrix

| Condition | Escalation | Who |
|-----------|-----------|-----|
| Critical finding not started within 48 hours | Immediate | CEO + Board |
| Critical finding overdue by >7 days | Immediate | CEO + Board |
| High finding overdue by >14 days | Biweekly review | CISO → CEO |
| 3+ Medium findings overdue by >30 days | Monthly review | CISO |
| Pattern of missed targets by same owner | Quarterly review | CISO → HR |

---

## Quarterly CAP Summary

### Q[N] [Year]

| Metric | Count |
|--------|-------|
| CAPs opened this quarter | [N] |
| CAPs closed this quarter | [N] |
| CAPs overdue (past target close) | [N] |
| Average time to close (days) | [N] |
| Critical CAPs average closure | [N] days |
| High CAPs average closure | [N] days |

### Aging Report

| Age Bucket | Critical | High | Medium | Low | Total |
|------------|----------|------|--------|-----|-------|
| 0–30 days | [N] | [N] | [N] | [N] | [N] |
| 31–60 days | [N] | [N] | [N] | [N] | [N] |
| 61–90 days | [N] | [N] | [N] | [N] | [N] |
| >90 days (overdue) | [N] | [N] | [N] | [N] | [N] |

---

## Evidence Requirements for Closure

All CAP closures require the following:

| Risk Rating | Minimum Evidence |
|-------------|-----------------|
| **Critical** | Retest by independent auditor + CISO sign-off |
| **High** | Retest by audit team + documented evidence (screenshots, config exports, logs) |
| **Medium** | Self-attestation with evidence + spot check by audit team |
| **Low** | Self-attestation (verified at next audit cycle) |

**No CAP shall be closed without documented evidence. Email confirmations are not sufficient.**
