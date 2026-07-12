# Audit Findings — Anonymized Examples

> **Note**: These findings are **representative examples** based on common manufacturing IT/OT audit findings. They demonstrate the structure and depth of real audit outputs without exposing any actual company data. All system names, dates, and specifics are fictionalized.

---

## Finding #001 — Critical

| Field | Detail |
|-------|--------|
| **Finding ID** | FIND-2025-001 |
| **Domain** | 3 — Access Management |
| **Risk Rating** | **Critical** |
| **Control Reference** | 3.3 — Privileged access reviewed quarterly |
| **Condition** | Review of the last 4 quarterly privileged access reviews revealed that the OT domain administrator group contained 7 accounts belonging to former contractors whose access was never revoked. Two of these accounts showed successful login activity to the MES system within the last 60 days. |
| **Criteria** | Company policy requires access revocation within 24 hours of termination and quarterly privileged access recertification. GDPR Art. 32 requires appropriate technical measures to ensure ongoing confidentiality. |
| **Cause** | The OT team did not have a formal offboarding workflow integrated with the contractor management system. Contractor departures were communicated via email and occasionally missed. Quarterly access reviews were being performed but used an incomplete account list. |
| **Impact / Risk** | 7 former contractors retained administrative access to the MES platform, which processes PII of approximately 2,500 employees (worker IDs, timestamps, production metrics). Two accounts showed recent activity, indicating actual unauthorized access risk. Potential GDPR notification obligation if access was misused. |
| **Recommendation** | 1. Immediately disable all 7 accounts. 2. Investigate login activity for the 2 active accounts — determine what was accessed and whether PII was exfiltrated. 3. Integrate contractor offboarding into the centralized IAM (Okta) workflow. 4. Automate privileged access review using IAM reports (not manual spreadsheets). |
| **Management Response** | Agreed. All 7 accounts disabled within 2 hours of finding. Forensic investigation of the 2 accounts initiated. IAM integration project added to Q1 roadmap. |
| **Due Date** | 30 days (permanent fix); immediate (account disablement) |

---

## Finding #002 — High

| Field | Detail |
|-------|--------|
| **Finding ID** | FIND-2025-002 |
| **Domain** | 8 — OT/IoT Security |
| **Risk Rating** | **High** |
| **Control Reference** | 8.4 — Default credentials changed on all OT/IoT devices |
| **Condition** | Passive network scan of the Factory B production line identified 12 IoT temperature sensors (Brand X, Model T-200) still using default manufacturer credentials (admin/admin). These sensors are connected to the MES platform via the OT network. |
| **Criteria** | Company OT security baseline requires all default credentials changed before production deployment. IEC 62443-3-3 SR 1.1 requires unique identification and authentication. |
| **Cause** | Sensors were deployed by a third-party integrator during a weekend maintenance window. The integrator's installation checklist did not include a credential-change step. Post-installation verification was not performed by internal OT team. |
| **Impact / Risk** | Unauthorized access to 12 sensors could allow: (a) falsified temperature readings compromising product quality, (b) lateral movement within the OT network segment, (c) denial of service against production monitoring. No PII directly exposed, but production disruption risk is high. |
| **Recommendation** | 1. Immediately change credentials on all 12 sensors. 2. Scan entire OT network for other default-credential devices. 3. Update third-party integrator installation checklist to include credential-change verification. 4. Implement post-installation OT security review for all third-party deployments. |
| **Management Response** | Agreed. Credentials changed within 4 hours. Full OT network scan scheduled. Integrator checklist updated. |
| **Due Date** | 30 days |

---

## Finding #003 — High

| Field | Detail |
|-------|--------|
| **Finding ID** | FIND-2025-003 |
| **Domain** | 7 — Privacy Controls |
| **Risk Rating** | **High** |
| **Control Reference** | 7.2 — GDPR DSAR response within 30 days (100% compliance) |
| **Condition** | Review of the DSAR tracker for the audit period found that 3 out of 47 DSARs (6.4%) exceeded the GDPR 30-day response window. Two requests were for former employees; one was for an EU-based customer contact. Response times were 38, 42, and 47 days respectively. |
| **Criteria** | GDPR Art. 12(3) requires response without undue delay and within one month. Internal SLA requires 100% compliance. |
| **Cause** | Former employee DSARs required data retrieval from archived HRIS backups (not in active system), which the HR team was not trained to perform. The customer DSAR was delayed due to confusion over whether B2B contact data fell within scope (it does, if the contact is an identifiable individual). |
| **Impact / Risk** | Non-compliance with GDPR Art. 12(3). Three Data Subjects could lodge complaints with supervisory authorities. While the delayed responses were eventually completed, the pattern indicates process gaps that could lead to regulatory scrutiny if uncorrected. |
| **Recommendation** | 1. Train HR team on archived data retrieval for former employee DSARs. 2. Create a DSAR runbook covering edge cases (former employees, B2B contacts, archived data). 3. Implement DSAR workflow automation with automated deadline reminders. 4. Notify the 3 affected Data Subjects of the delay and their right to complain (transparency). |
| **Management Response** | Agreed. HR training scheduled. Runbook development in progress. DSAR automation tool evaluation added to Q2 budget. |
| **Due Date** | 60 days |

---

## Finding #004 — Medium

| Field | Detail |
|-------|--------|
| **Finding ID** | FIND-2025-004 |
| **Domain** | 9 — Vendor / TPRM |
| **Risk Rating** | **Medium** |
| **Control Reference** | 9.1 — DPA executed for all vendors processing PII |
| **Condition** | Two Tier 2 vendors (a logistics analytics provider and an IT support vendor) were found to be processing limited PII (customer shipping addresses, employee email addresses) without an executed DPA. Both vendors had been engaged for >6 months. |
| **Criteria** | GDPR Art. 28 requires a contract (DPA) governing processing by a processor. CCPA requires a service provider contract with specific prohibitions. |
| **Cause** | Both vendors were onboarded during a period of rapid growth when the formal TPRM process was not consistently applied. Procurement did not flag data processing during the RFP because the data categories were not obviously PII (shipping addresses were considered "operational data"). |
| **Impact / Risk** | Processing without a DPA is a GDPR violation. Limited sensitivity of the PII involved reduces the risk. However, lack of contractual controls means no audit rights, breach notification obligations, or data deletion commitments. |
| **Recommendation** | 1. Execute DPAs with both vendors within 14 days. 2. Review all other vendors engaged in the same period for similar gaps. 3. Update procurement training to flag any vendor that receives contact/location data as potentially processing PII. |
| **Management Response** | Agreed. DPAs in negotiation. Retrospective review of vendor portfolio initiated. |
| **Due Date** | 30 days |

---

## Finding #005 — Medium

| Field | Detail |
|-------|--------|
| **Finding ID** | FIND-2025-005 |
| **Domain** | 5 — Vulnerability & Patch Management |
| **Risk Rating** | **Medium** |
| **Control Reference** | 5.5 — OT systems: vulnerability assessment performed |
| **Condition** | The OT vulnerability assessment program covers PLCs and SCADA systems but does not include the Factory A CCTV system (32 cameras, 2 NVRs). The CCTV NVRs were last patched 18 months ago. |
| **Criteria** | Company policy requires monthly vulnerability assessment for all networked devices. IEC 62443-3-3 requires security monitoring of all IACS components. |
| **Cause** | CCTV was managed by Facilities (not OT Engineering) and was not included in the OT asset inventory used for vulnerability scanning. Ownership ambiguity between Facilities and OT Engineering. |
| **Impact / Risk** | CCTV footage contains PII (video/images of employees). Unpatched NVRs could allow unauthorized access to stored footage. 18-month patch gap is significant. |
| **Recommendation** | 1. Add CCTV systems to OT asset inventory and vulnerability scanning scope. 2. Patch NVRs during next maintenance window. 3. Clarify ownership: OT Engineering for security; Facilities for physical maintenance. |
| **Management Response** | Agreed. Asset inventory updated. Patching scheduled. |
| **Due Date** | 45 days |

---

## Summary Statistics

| Metric | Count |
|--------|-------|
| Total Findings | 17 |
| Critical | 1 |
| High | 3 |
| Medium | 8 |
| Low | 5 |
| Average days to close (High/Critical) | 38 days |
| Recurring findings (from prior audit) | 2 |

---

**Note**: These are illustrative examples designed to demonstrate the audit finding format and depth. In practice, all findings are tracked in the CAP Tracker with owner assignments, due dates, and verification evidence.
