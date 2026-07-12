# OT/IoT Security Audit — IEC 62443 Integration Notes

> **Applicable Standard**: IEC 62443 (Industrial Automation and Control Systems Security)  
> **Audit Domain**: Domain 8 — OT/IoT Security  
> **Version**: 1.0

---

## 1. Overview

Manufacturing environments integrate Operational Technology (OT) — MES, PLCs, SCADA, IoT sensors, CCTV, access control — with IT systems. Traditional IT audit frameworks (ISO 27001, NIST 800-53) do not fully address OT-specific risks. **IEC 62443** provides the standard for Industrial Automation and Control Systems (IACS) security.

This document provides OT-specific audit considerations aligned with IEC 62443, supplementing the main [Annual Audit Program](./annual-audit-program.md) and [Audit Checklist](./audit-checklist.md).

---

## 2. IEC 62443 Framework Quick Reference

IEC 62443 is organized into four parts with multiple sub-standards:

| Part | Focus | Relevance to Audit |
|------|-------|-------------------|
| **62443-1** | General concepts, terminology, models | Foundation for understanding IACS |
| **62443-2** | Policies & procedures (e.g., 2-1: Security program requirements) | Governance domain |
| **62443-3** | System-level security (e.g., 3-3: System security requirements) | Technical controls |
| **62443-4** | Component-level security (e.g., 4-2: Component security requirements) | Device-level controls |

### Maturity Levels (IEC 62443-2-1)

| Level | Name | Description |
|-------|------|-------------|
| **ML 1** | Initial | Ad-hoc, reactive security |
| **ML 2** | Managed | Documented processes, basic controls |
| **ML 3** | Defined (Practiced) | Formal, consistent processes across organization |
| **ML 4** | Improving | Continuous improvement, metrics-driven |

**Target for Manufacturing**: ML 3–4 for critical systems, ML 2 minimum for all OT.

---

## 3. Key OT Audit Challenges

| Challenge | Impact on Audit |
|-----------|----------------|
| **Availability-first systems** | Cannot take production systems offline for scanning; must use passive monitoring or scheduled maintenance windows |
| **Legacy/unsupported devices** | PLCs and sensors running Windows XP, proprietary RTOS — no patches available; must rely on compensating controls |
| **Proprietary protocols** | Modbus, PROFINET, EtherNet/IP — not understood by IT security tools; need OT-aware IDS |
| **Long lifecycles** | 15–20 year equipment life vs. 3–5 year IT refresh cycle |
| **Vendor lock-in** | Patches and security updates controlled by equipment vendor; limited ability to self-patch |
| **Safety integration** | Safety Instrumented Systems (SIS) share network — security changes must not compromise safety |
| **Air-gap myths** | "We're air-gapped" is rarely true; USB, vendor laptops, remote support connections create paths |

---

## 4. Audit Test Procedures — OT Specific

### 4.1 Network Segmentation Verification

| Test | Procedure | Expected Result |
|------|-----------|-----------------|
| IT→OT connectivity test | Attempt to connect from IT workstation to OT device IP | Blocked by firewall (except allowed DMZ flows) |
| OT VLAN verification | Review switch configs; verify OT devices are on dedicated VLANs | OT VLAN isolated; no trunking to IT VLAN |
| DMZ inspection | Review DMZ firewall rules; sample 5 rules | Only documented, justified rules present |
| Wireless OT network | Scan for rogue wireless access points on factory floor | No unauthorized APs; OT WiFi separate SSID with WPA3-Enterprise |

### 4.2 OT Device Inventory Accuracy

| Test | Procedure | Expected Result |
|------|-----------|-----------------|
| Inventory completeness | Passive network scan + compare to inventory | <5% discrepancy |
| Critical device attributes | Sample 20 devices: check firmware version, patch level, EOL date fields | All fields complete and accurate |
| Rogue device detection | Compare active devices against authorized inventory | No unauthorized devices |

### 4.3 OT Access Control

| Test | Procedure | Expected Result |
|------|-----------|-----------------|
| Shared account check | Review operator workstation login records | All individual accounts; no shared "operator" accounts |
| Remote access validation | Attempt remote access without VPN + MFA + jump host | Access denied |
| Vendor remote access | Review vendor remote access logs for last 90 days | All sessions logged; time-limited access; MFA enforced |
| Privileged access review | Sample 5 OT admin accounts; check review cadence | Reviewed quarterly; no stale accounts |

### 4.4 OT Patching Assessment

| Test | Procedure | Expected Result |
|------|-----------|-----------------|
| Patch gap analysis | Compare device firmware versions against vendor latest | Critical/security patches applied within vendor guidance |
| Compensating controls | For unpatchable devices: verify compensating controls (micro-segmentation, IDS rules, restricted access) | Compensating controls documented and tested |
| Patch testing | Review last 3 OT patches: tested in dev environment? | All patches tested before production |

### 4.5 OT Security Monitoring

| Test | Procedure | Expected Result |
|------|-----------|-----------------|
| OT traffic visibility | Check if OT network traffic is ingested into SIEM | OT switch span ports or TAPs sending to SIEM |
| OT-specific alert rules | Verify alerts for: Modbus function code anomalies, unauthorized CIP connections, firmware changes | Alerts configured and tested |
| Alert response | Trigger test alert from OT network; measure response time | Alert received and acknowledged within SLA |

---

## 5. OT-Specific PII Considerations

OT systems process PII in specific scenarios that must be audited:

| Scenario | PII Involved | Audit Check |
|----------|-------------|-------------|
| Badge/access control | Employee ID, biometric template, location, timestamp | Biometric data hashed? Access logs retained per policy? |
| IoT worker tracking | Worker ID, workstation, productivity metrics | Pseudonymized for analytics? Individual tracking justified by LIA? |
| CCTV footage | Video/images of individuals | Retention 30 days? Access logged? Facial recognition deployed (→ DPIA required)? |
| Quality inspection logs | Worker ID linked to inspected units | Retention aligned with product liability + privacy? |

---

## 6. OT Audit Prerequisites

Before starting OT audit fieldwork:

- [ ] Obtain production schedule — plan testing during maintenance windows if active scanning required
- [ ] Review safety incident procedures — ensure audit activities will not trigger safety systems
- [ ] Coordinate with OT Engineering Lead — they must be present for all OT testing
- [ ] Obtain vendor contact list — for firmware version verification
- [ ] Review prior OT risk assessments
- [ ] Confirm passive scanning tools are OT-safe (no active probing unless approved)

---

## 7. Common OT Findings

Based on industry data, the most common OT audit findings in manufacturing:

| Rank | Finding | Frequency |
|------|---------|-----------|
| 1 | Incomplete or outdated OT device inventory | Very High |
| 2 | Default/shared credentials on OT devices | High |
| 3 | Lack of OT network segmentation from IT | High |
| 4 | Unmanaged remote vendor access | High |
| 5 | No OT security monitoring (SIEM blind spot) | Medium-High |
| 6 | Unpatched known vulnerabilities on legacy devices | Medium-High |
| 7 | USB ports not disabled on operator workstations | Medium |
| 8 | No OT-specific incident response procedures | Medium |

---

## 8. IEC 62443-2-1 Self-Assessment (Abbreviated)

Use this simplified maturity assessment during audit scoping:

| Foundational Requirement (FR) | Current ML (1-4) | Target ML | Gap |
|------------------------------|-----------------|-----------|-----|
| FR 1 — Identification & Authentication Control | | | |
| FR 2 — Use Control | | | |
| FR 3 — System Integrity | | | |
| FR 4 — Data Confidentiality | | | |
| FR 5 — Restricted Data Flow | | | |
| FR 6 — Timely Response to Events | | | |
| FR 7 — Resource Availability | | | |

---

## 9. References

- IEC 62443-2-1: Security program requirements for IACS asset owners
- IEC 62443-3-3: System security requirements and security levels
- NIST SP 800-82 Rev 3: Guide to OT Security (2023)
- [Annual Audit Program](./annual-audit-program.md)
- [Audit Checklist — Domain 8](./audit-checklist.md)
