# Annual IT & OT Audit Checklist

> **Audit Period**: Q4 [Year] | **Audit Team**: [Names]  
> **Instructions**: Mark each item: ✅ Compliant | ⚠️ Partial/At Risk | ❌ Non-Compliant | N/A Not Applicable. Provide evidence reference for each.

---

## Domain 1: Governance & Policy

| # | Control | Status | Evidence Reference | Notes |
|---|---------|--------|-------------------|-------|
| 1.1 | All privacy and security policies reviewed and approved within last 12 months | ⬜ | | |
| 1.2 | Data Protection Officer / Privacy Officer role formally appointed and documented | ⬜ | | |
| 1.3 | Information Security roles and responsibilities documented (RACI) | ⬜ | | |
| 1.4 | Privacy Committee charter approved; quarterly meetings held for past 4 quarters | ⬜ | | |
| 1.5 | Annual compliance plan approved by executive leadership | ⬜ | | |
| 1.6 | Policy exceptions documented, approved, and time-limited | ⬜ | | |
| 1.7 | Regulatory change monitoring process documented | ⬜ | | |

---

## Domain 2: Data Inventory & RoPA Accuracy

| # | Control | Status | Evidence Reference | Notes |
|---|---------|--------|-------------------|-------|
| 2.1 | RoPA contains all processing activities (verify against system inventory) | ⬜ | | |
| 2.2 | RoPA fields complete: lawful basis, retention, recipients, transfers, security measures | ⬜ | | |
| 2.3 | RoPA reviewed and updated within last 6 months | ⬜ | | |
| 2.4 | System inventory includes all IT and OT assets that process PII | ⬜ | | |
| 2.5 | PII data classification (Tier 1/2/Sensitive) applied to all identified data stores | ⬜ | | |
| 2.6 | Data minimization principle enforced — sample 5 data collection points | ⬜ | | |
| 2.7 | New systems/projects have privacy review before go-live | ⬜ | | |
| 2.8 | Data flow diagrams current and match RoPA | ⬜ | | |

---

## Domain 3: Access Management

| # | Control | Status | Evidence Reference | Notes |
|---|---------|--------|-------------------|-------|
| 3.1 | RBAC roles defined with least-privilege principle for all PII systems | ⬜ | | |
| 3.2 | MFA enforced on all systems containing PII (IT and OT) | ⬜ | | |
| 3.3 | Privileged access (admin, root) reviewed and recertified quarterly | ⬜ | | |
| 3.4 | User offboarding: access revoked within 24 hours of termination | ⬜ | | |
| 3.5 | No shared/generic/non-personal accounts on PII systems | ⬜ | | |
| 3.6 | Password policy enforces: ≥14 chars, complexity, rotation, no reuse of last 10 | ⬜ | | |
| 3.7 | Failed login attempts trigger account lockout after 5 attempts | ⬜ | | |
| 3.8 | OT-specific: operator workstations use individual accounts (not shared) | ⬜ | | |
| 3.9 | Remote access requires MFA + VPN + jump host (no direct RDP/SSH to OT) | ⬜ | | |
| 3.10 | Emergency/break-glass access procedures defined and tested | ⬜ | | |

---

## Domain 4: Data Protection

| # | Control | Status | Evidence Reference | Notes |
|---|---------|--------|-------------------|-------|
| 4.1 | All PII databases encrypted at rest (AES-256 or equivalent) | ⬜ | | |
| 4.2 | All PII data in transit encrypted (TLS 1.2+, prefer 1.3) | ⬜ | | |
| 4.3 | DLP solution deployed and configured with PII detection rules | ⬜ | | |
| 4.4 | DLP alerts monitored and responded to within SLA | ⬜ | | |
| 4.5 | Data retention schedule enforced — verify automatic deletion for 3 categories | ⬜ | | |
| 4.6 | Backups encrypted and tested for recovery within last 6 months | ⬜ | | |
| 4.7 | Secure disposal: PII on decommissioned hardware/media securely wiped | ⬜ | | |
| 4.8 | OT-specific: sensor data streams pseudonymized where worker ID is linked | ⬜ | | |

---

## Domain 5: Vulnerability & Patch Management

| # | Control | Status | Evidence Reference | Notes |
|---|---------|--------|-------------------|-------|
| 5.1 | Vulnerability scans run monthly on all IT systems | ⬜ | | |
| 5.2 | Critical vulnerabilities patched within 48 hours of identification | ⬜ | | |
| 5.3 | High-severity vulnerabilities patched within 14 days | ⬜ | | |
| 5.4 | Patch compliance >95% across IT assets | ⬜ | | |
| 5.5 | OT systems: vulnerability assessment performed (passive/agent-based) | ⬜ | | |
| 5.6 | OT patching: documented maintenance windows; critical patches applied within vendor guidance | ⬜ | | |
| 5.7 | Annual third-party penetration test completed | ⬜ | | |
| 5.8 | Penetration test findings remediated and retested | ⬜ | | |
| 5.9 | End-of-life/unsupported software identified and remediation plan in place | ⬜ | | |

---

## Domain 6: Incident Response & Breach

| # | Control | Status | Evidence Reference | Notes |
|---|---------|--------|-------------------|-------|
| 6.1 | Incident Response Plan current (reviewed within 12 months) | ⬜ | | |
| 6.2 | Table-top exercise conducted within last 12 months | ⬜ | | |
| 6.3 | Breach notification workflow tested: internal escalation → DPO → supervisory authority within GDPR 72 hours | ⬜ | | |
| 6.4 | Incident log maintained with all P1/P2 incidents and root cause analysis | ⬜ | | |
| 6.5 | Incident classification matrix defined (P1-P4) with response SLAs | ⬜ | | |
| 6.6 | CCPA breach notification to CA AG tested (≥500 residents threshold) | ⬜ | | |
| 6.7 | Forensics retainer or internal capability confirmed | ⬜ | | |
| 6.8 | OT-specific: OT incident response procedures integrated with IT IR plan | ⬜ | | |
| 6.9 | OT-specific: safe shutdown/isolation procedures documented for critical OT systems | ⬜ | | |

---

## Domain 7: Privacy Controls

| # | Control | Status | Evidence Reference | Notes |
|---|---------|--------|-------------------|-------|
| 7.1 | DSAR process documented and tested — sample last 10 DSARs for SLA compliance | ⬜ | | |
| 7.2 | GDPR DSAR response within 30 days (100% compliance) | ⬜ | | |
| 7.3 | CCPA DSAR response within 45 days (100% compliance) | ⬜ | | |
| 7.4 | Identity verification performed for all DSARs | ⬜ | | |
| 7.5 | Consent records maintained with timestamp, scope, and method | ⬜ | | |
| 7.6 | Cookie consent banner deployed on all public-facing websites | ⬜ | | |
| 7.7 | Cookie consent: pre-checked boxes NOT used; opt-in for non-essential | ⬜ | | |
| 7.8 | DPIA completed for all high-risk processing activities (per RoPA) | ⬜ | | |
| 7.9 | Privacy Notice current and published on website | ⬜ | | |
| 7.10 | CCPA "Do Not Sell My Personal Information" link present on homepage (if applicable) | ⬜ | | |

---

## Domain 8: OT/IoT Security (Manufacturing-Specific)

| # | Control | Status | Evidence Reference | Notes |
|---|---------|--------|-------------------|-------|
| 8.1 | OT network physically or logically segmented from IT network | ⬜ | | |
| 8.2 | OT-IT DMZ implemented with firewall rules allowing only required traffic | ⬜ | | |
| 8.3 | OT device inventory current and includes firmware version, patch level, EOL date | ⬜ | | |
| 8.4 | Default credentials changed on all OT/IoT devices | ⬜ | | |
| 8.5 | OT change management: all changes tested in dev environment before production | ⬜ | | |
| 8.6 | OT remote access: MFA + VPN + jump host + session recording | ⬜ | | |
| 8.7 | OT security monitoring: network traffic analyzed by SIEM/IDS | ⬜ | | |
| 8.8 | CCTV system: access logged, footage retention per policy, encryption for stored video | ⬜ | | |
| 8.9 | Biometric systems: templates stored as hashes (not raw); access strictly controlled | ⬜ | | |
| 8.10 | IEC 62443 maturity assessment completed | ⬜ | | |

---

## Domain 9: Vendor / Third-Party Risk Management (TPRM)

| # | Control | Status | Evidence Reference | Notes |
|---|---------|--------|-------------------|-------|
| 9.1 | DPA executed for all vendors processing PII (verify 10 high-risk) | ⬜ | | |
| 9.2 | Vendor risk assessments current for all Tier 1 vendors (within 12 months) | ⬜ | | |
| 9.3 | Vendor audit schedule maintained; audits completed per schedule | ⬜ | | |
| 9.4 | Sub-processor approval process documented and followed | ⬜ | | |
| 9.5 | Vendor incident notification SLA tested (sample 3 vendor notification processes) | ⬜ | | |
| 9.6 | Offboarded vendors: data deletion certificates obtained and verified | ⬜ | | |
| 9.7 | Software developer partners: secure SDLC verification (code review, pen test) | ⬜ | | |

---

## Domain 10: Logging & Monitoring

| # | Control | Status | Evidence Reference | Notes |
|---|---------|--------|-------------------|-------|
| 10.1 | SIEM operational: all critical systems forwarding logs | ⬜ | | |
| 10.2 | PII access logged: who, what, when, from where | ⬜ | | |
| 10.3 | Audit logs immutable: write-once or append-only storage | ⬜ | | |
| 10.4 | Log retention ≥ 1 year (online) + 3 years (archive) | ⬜ | | |
| 10.5 | Alert rules configured for: multiple failed logins, privileged access, bulk data export | ⬜ | | |
| 10.6 | Alerts responded to within SLA (Tier 1: 15 min, Tier 2: 1 hour, Tier 3: 24 hours) | ⬜ | | |
| 10.7 | OT-specific: OT network traffic monitored for anomalies | ⬜ | | |

---

## Scoring Summary

| Domain | Max Score | Actual Score | % |
|--------|-----------|-------------|---|
| 1. Governance & Policy | 7 | | |
| 2. Data Inventory & RoPA | 8 | | |
| 3. Access Management | 10 | | |
| 4. Data Protection | 8 | | |
| 5. Vulnerability & Patch Management | 9 | | |
| 6. Incident Response & Breach | 9 | | |
| 7. Privacy Controls | 10 | | |
| 8. OT/IoT Security | 10 | | |
| 9. Vendor / TPRM | 7 | | |
| 10. Logging & Monitoring | 7 | | |
| **TOTAL** | **85** | | |

**Scoring**: ✅ = 1 point | ⚠️ = 0.5 points | ❌ = 0 points | N/A = excluded from total

**Maturity Rating**:
- **90–100%**: Leading — Strong compliance posture
- **75–89%**: Established — Minor gaps exist
- **60–74%**: Developing — Material gaps require attention
- **Below 60%**: At Risk — Significant remediation required
