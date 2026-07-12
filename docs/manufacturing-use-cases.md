# Manufacturing-Specific Compliance Use Cases

> **Purpose**: Illustrate how the IT Compliance Framework addresses real-world manufacturing scenarios that differ materially from generic corporate compliance contexts.

---

## Use Case 1: Employee Biometric Time & Attendance

### Scenario

A manufacturing plant with 1,200 factory workers implements a biometric (fingerprint) time clock system integrated with the MES and HRIS. Workers badge in at zone entry points; attendance data flows to payroll.

### Compliance Challenges

| Challenge | Framework Response |
|-----------|-------------------|
| Biometric data = GDPR Special Category + CCPA Sensitive PI | [GDPR/CCPA Policy](../gdpr-ccpa/policy-template.md) Section 2.1 — Special Category handling |
| Worker consent must be freely given — power imbalance | Policy requires documented consent process with no employment penalty for refusal (provide alternative: PIN code) |
| Data flows across OT (badge reader) → IT (HRIS) boundary | [Data Mapping](../gdpr-ccpa/data-mapping-example.md) — OT-IT convergence diagram |
| Retention: how long to keep biometric templates? | RoPA entry PA-001: deleted within 30 days of termination |
| DPIA required | Triggered because: biometric + systematic monitoring of workers at scale |

### Audit Verification (from [Audit Checklist](../it-audit/audit-checklist.md))

- 8.9: Biometric systems — templates stored as hashes, access strictly controlled
- 7.5: Consent records maintained with timestamp, scope, method
- 4.1: PII databases encrypted at rest

---

## Use Case 2: Global Supply Chain — EU Vendor Data

### Scenario

The company sources components from 45 EU-based vendors. Vendor contacts (name, email, phone), contract documents, and bank details are stored in the US-based ERP (SAP). Logistics partners in APAC receive shipping data for customs clearance.

### Compliance Challenges

| Challenge | Framework Response |
|-----------|-------------------|
| EU vendor personal data transferred to US | [Cross-border transfer mechanism](../gdpr-ccpa/data-mapping-example.md) — SCC + DPF required |
| Transfer Impact Assessment needed | [DPA Template](../gdpr-ccpa/dpa-template.md) Section 5 — TIA conducted |
| Logistics partners in APAC receive EU data | Sub-processor flows documented; APAC partner under SCC |
| Data minimization: does logistics need all vendor contact data? | RoPA specifies only shipping-relevant data shared |

### Audit Verification

- Domain 1 (Governance): Cross-border transfer mechanisms current
- Domain 9 (Vendor): DPA executed for logistics partners

---

## Use Case 3: IoT Sensor Data and Worker Privacy

### Scenario

The company deploys 500 IoT sensors across three production lines. Sensors track: machine temperature/vibration (no PII), workstation occupancy (worker ID linked), throughput per worker, and ergonomic data (posture/repetitive motion via wearables).

### Compliance Challenges

| Challenge | Framework Response |
|-----------|-------------------|
| Worker ID linked to sensor data = PII | [Data Mapping](../gdpr-ccpa/data-mapping-example.md) — Production Line IoT flow |
| Ergonomic data may reveal health information | Potential Special Category data — DPIA required |
| Analytics cloud processes worker productivity data | Pseudonymization required before data leaves OT network |
| Worker consent vs. legitimate interest for production analytics | Legitimate Interest Assessment (LIA) documented; opt-out provided |
| Data retention: raw vs. aggregated | RoPA: raw data 90 days; aggregated/anonymized 3 years |

### Audit Verification

- 8.2: OT network segmentation verified
- 4.8: Sensor data streams pseudonymized where worker ID linked
- 7.8: DPIA completed for high-risk processing

---

## Use Case 4: B2B Customer Data — GDPR Applicability

### Scenario

The company sells industrial equipment to EU-based manufacturers. The CRM contains: purchasing manager names, business emails, phone numbers, order history, and occasionally personal notes in order specifications. Sales team argues "it's just B2B — GDPR doesn't apply."

### Compliance Challenges

| Challenge | Framework Response |
|-----------|-------------------|
| B2B contacts are identifiable individuals—GDPR applies | [GDPR/CCPA Policy](../gdpr-ccpa/policy-template.md) — B2B explicitly in scope |
| Lawful basis: Contract (order fulfillment) | RoPA entry PA-004 |
| EU customers have DSAR rights | [DSAR Procedure](../gdpr-ccpa/dsar-procedure.md) — B2B contacts are data subjects |
| CCPA: B2B exemption is limited and excludes certain rights | Policy notes B2B partial exemption under CCPA |

### Audit Verification

- 7.1: DSAR process tested for all subject types, including B2B
- 2.1: RoPA includes B2B processing activities

---

## Use Case 5: OT Legacy Systems — Patching Challenges

### Scenario

The factory floor has 15 PLCs running Windows XP Embedded (EOL 2014) controlling critical production equipment. These PLCs cannot be patched. The OT network is "air-gapped" from IT — but engineers occasionally connect laptops for diagnostics.

### Compliance Challenges

| Challenge | Framework Response |
|-----------|-------------------|
| Unpatchable legacy systems | [OT/IEC 62443 Notes](../it-audit/ot-iec62443-notes.md) — compensating controls required |
| "Air gap" is not a control — laptop connections create path | Audit tests for unauthorized IT-OT connectivity |
| No patches available → compensating controls | Micro-segmentation, IDS rules specific to PLC protocols, restricted physical access, USB disabled |
| Safety constraint: cannot disrupt production | Audit testing scheduled during maintenance windows; passive scanning only |

### Audit Verification

- 8.1: OT network segmentation verified by active test
- 5.5: Unpatchable devices have documented compensating controls
- 8.10: IEC 62443 maturity assessment

---

## Use Case 6: Software Developer Partner — Offshore Development

### Scenario

The company engages an India-based software development firm to build a custom MES integration module. Developers need access to: source code repository, CI/CD pipeline, and occasionally test data (which contains PII-mimicking but not production PII). The vendor uses a US-based cloud IDE (GitHub Codespaces).

### Compliance Challenges

| Challenge | Framework Response |
|-----------|-------------------|
| Offshore developer access to systems containing PII architecture | [TPRM Framework](../tprm/tprm-framework.md) — Tier 1 classification |
| Sub-processor: cloud IDE in US | [Due Diligence Questionnaire](../tprm/due-diligence-questionnaire.md) Section 2.10-2.11 — Sub-processor disclosure |
| Test data with PII-like structure | [Software Developer Checklist](../tprm/software-developer-checklist.md) Section 4 — synthetic data only |
| Source code access from offshore | DPA: no PII leaves authorized locations; developer session logging |
| Code ownership and IP protection | [DPA Template (TPRM)](../tprm/standard-dpa-template.md) Section 3 — IP assignment clause |

### Audit Verification

- 9.3: Vendor audit schedule maintained
- 9.7: Software developer partners — secure SDLC verified
- 2.7 (Access): Off-shore developer access logged and reviewed

---

## Use Case 7: Mergers & Acquisitions — Due Diligence

### Scenario

The company acquires a smaller manufacturer. The acquired company has: no formal privacy program, an Excel-based customer list with EU contacts, a legacy ERP with weak access controls, and no vendor DPAs.

### Compliance Challenges

| Challenge | Framework Response |
|-----------|-------------------|
| Inherited compliance debt | Immediate gap assessment using [Audit Checklist](../it-audit/audit-checklist.md) |
| No RoPA for acquired systems | Data mapping sprint using [RoPA Template](../gdpr-ccpa/ropa-template.md) |
| No vendor DPAs | [TPRM Framework](../tprm/tprm-framework.md) — vendor inventory + priority DPA execution |
| Integration: merging IT systems | DPIA for any new processing created by integration |
| Timeline: GDPR requires compliance from Day 1 | Risk acceptance documented for integration period; prioritized remediation |

### Framework Application

The entire framework serves as the **integration playbook** — audit checklist identifies gaps, RoPA template captures new processing, TPRM triages vendor risk, and the CAP tracker manages remediation.

---

## Key Takeaways

1. **B2B is not exempt**: In manufacturing, GDPR applies to vendor contacts, customer contacts, and anyone identifiable in "business" data.
2. **OT/IoT is unique**: Traditional IT compliance frameworks miss OT-specific risks (safety constraints, legacy systems, proprietary protocols). IEC 62443 integration is essential.
3. **Supply chain = data chain**: Every vendor, logistics partner, and customs broker in the supply chain is a data processor or sub-processor.
4. **Biometric data is proliferating**: Factory floor biometrics (access, time tracking, wearables) trigger the highest compliance obligations — Special Category data under GDPR, Sensitive PI under CCPA.
5. **"Air gap" is a myth**: Every USB stick, vendor laptop, and remote support session creates a path. Defense in depth is the only viable OT security strategy.
