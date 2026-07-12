# Compliance Dashboard — Example Design

> **Note**: This is a conceptual design for a compliance dashboard. The actual implementation would be built in a GRC platform (ServiceNow, OneTrust) or BI tool (Power BI, Tableau). All metrics below are **representative examples** based on manufacturing compliance program design.

---

## Dashboard Overview

The Compliance Dashboard provides executive leadership and the Privacy Committee with an at-a-glance view of the organization's compliance posture across three pillars: Privacy, Audit, and Vendor Risk.

---

## Panel 1: Overall Compliance Health

| Metric | Current | Target | Trend |
|--------|---------|--------|-------|
| Overall Compliance Score | 87% | ≥85% | ↑ +5% YoY |
| Open Audit Findings | 12 | ≤15 | ↓ -3 |
| Critical/High Findings | 3 | 0 | → |
| Overdue CAP Items | 1 | 0 | ↓ -2 |

---

## Panel 2: Privacy Metrics (GDPR/CCPA)

| Metric | Current Period | Prior Period | SLA |
|--------|---------------|-------------|-----|
| DSARs Received | 47 | 38 | — |
| DSARs Responded Within SLA | 47 (100%) | 37 (97.4%) | 100% |
| Avg Response Time (days) | 12 | 16 | GDPR ≤30 / CCPA ≤45 |
| Consent Records Active | 2,847 | 2,610 | — |
| DPIA Completed (high-risk) | 8/8 (100%) | 6/6 (100%) | 100% |
| RoPA Activities Tracked | 34 | 31 | All identified |
| Breach Incidents (PII) | 0 | 1 | 0 |

---

## Panel 3: IT & OT Audit Findings by Domain

| Domain | Open | Closed (12 mo) | Avg Closure (days) |
|--------|------|---------------|---------------------|
| Governance & Policy | 1 | 3 | 22 |
| Data Inventory & RoPA | 2 | 2 | 35 |
| Access Management | 1 | 5 | 18 |
| Data Protection | 1 | 4 | 28 |
| Vulnerability & Patch | 3 | 6 | 41 |
| Incident Response | 0 | 2 | 15 |
| Privacy Controls | 1 | 3 | 25 |
| OT/IoT Security | 2 | 4 | 52 |
| Vendor / TPRM | 1 | 3 | 38 |
| Logging & Monitoring | 0 | 2 | 30 |
| **Total** | **12** | **34** | **Avg: 30.4** |

---

## Panel 4: Vendor Risk (TPRM)

| Metric | Current | Target |
|--------|---------|--------|
| Total Active Vendors | 87 | — |
| Vendors Processing PII | 34 | — |
| Tier 1 (High-Risk) | 8 | — |
| Tier 2 (Medium-Risk) | 19 | — |
| Tier 3 (Low-Risk) | 60 | — |
| DPA Coverage (PII Vendors) | 32/34 (94%) | 100% |
| Vendors with Expired Assessments | 2 | 0 |
| Avg Vendor Compliance Score | 84/100 | ≥80 |

---

## Panel 5: Key Risk Indicators (KRIs)

| KRI | Threshold | Current | Status |
|-----|-----------|---------|--------|
| Critical vulnerabilities unpatched >48 hrs | 0 | 0 | 🟢 |
| Privileged access not reviewed >90 days | 0 | 0 | 🟢 |
| DSAR overdue | 0 | 0 | 🟢 |
| DPA expired >30 days | 0 | 2 | 🔴 |
| OT devices with default credentials | 0 | 3 | 🟡 |
| Audit CAP overdue >90 days | 0 | 1 | 🟡 |

---

## Panel 6: Training & Awareness

| Metric | Current |
|--------|---------|
| Privacy training completion rate | 94% |
| Security awareness training completion | 91% |
| Phishing simulation click rate | 4.2% (↓ from 7.8%) |
| Vendor-facing team training | 100% |

---

## Trend: Compliance Score (12-Month)

```
Month    Score
Jan      79%
Feb      80%
Mar      81%
Apr      82%
May      83%
Jun      84%
Jul      85%
Aug      84%
Sep      86%
Oct      87%  ← Current
Nov      —
Dec      —
```

---

**Dashboard Refresh**: Metrics are refreshed monthly from GRC platform, SIEM, DSAR tracker, and vendor management system. The Privacy Committee reviews the dashboard quarterly; executive leadership reviews summary monthly.
