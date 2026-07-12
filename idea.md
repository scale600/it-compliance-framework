# IT Compliance Framework — US Manufacturing GDPR/CCPA, IT Audit, TPRM Policy Design & GitHub Publication Strategy

> **Wonhee Richard Lee** | Senior Cloud Systems Administrator
>
> A practical methodology document based on IPO support, Annual IT/OT Audit design, and Bose Project TPRM experience at Sena Technologies. This document serves as the design basis for the `scale600/it-compliance-framework` GitHub Repository, with the ultimate goal of providing publicly verifiable evidence for the GDPR/CCPA, IT Audit, and TPRM experience listed on my resume.
>
> Legal professional (attorney/DPO) review required. This document is a general guide and must be customized to company-specific circumstances.

---

## Table of Contents

1. [GDPR & CCPA Policy Design](#1-gdpr--ccpa-policy-design)
2. [Annual IT Audit Policy Design](#2-annual-it-audit-policy-design)
3. [TPRM Policy Design](#3-tprm-policy-design)
4. [Integrated Operations & Maintenance](#4-integrated-operations--maintenance)
5. [GitHub Repository Strategy](#5-github-repository-strategy)

---

## Manufacturing Characteristics & Key PII Flows

US manufacturing (automotive, machinery, electronics, consumer goods, etc.) involves complexly interconnected IT (ERP, CRM, HRIS) + OT (production lines, IoT sensors, PLC/SCADA) systems. Key PII flows:

| Domain | Data Types | Key Systems |
|--------|-----------|-------------|
| Employees/Workers | Name, SSN, biometric (fingerprint/facial recognition), health/safety records, work logs, CCTV | HRIS (Workday), Payroll, Access Control Systems |
| Customers (B2B) | Procurement/engineering contact details, order specifications, payment information | CRM (Salesforce), ERP (SAP/Oracle) |
| Supply Chain/Vendors | Contact details, contract documents, financial information, shipping addresses | ERP, WMS, Vendor Portals |
| Production/IoT | Worker ID + sensor data (location/time), quality inspection records | MES, PLC/SCADA, IoT Sensors |
| Other | IP/device ID, inferred data (production efficiency analytics) | Web/Portals, Analytics |

Due to global supply chains, EU data (exports/customers) and CA resident data may be intermingled, requiring simultaneous consideration of GDPR + CCPA/CPRA.

---

## 1. GDPR & CCPA Policy Design

### 1.1 System Architecture Discovery (1-2 weeks)

**Cross-functional team composition:** IT/OT, HR, Supply Chain, Legal, Production team participation.

**Asset inventory items:**

| Category | System Examples |
|----------|----------------|
| IT Systems | ERP (SAP/Oracle), CRM (Salesforce), HRIS (Workday), WMS (Logistics) |
| OT/Production | MES, PLC/SCADA, IoT Sensors (temperature/vibration/worker tracking), CCTV |
| Third-Party Services | Cloud (AWS/Azure), Logistics Partners (FedEx/UPS API), Vendor Portals, Analytics (Google Analytics) |
| Offline | Paper documents, USB drives, email attachments |

**Tools:** Excel/Google Sheets + Visio/draw.io for system diagrams.
**Reference Standards:** NIST, IEC 62443.

### 1.2 PII Definition & Classification (1 week)

| Regulation | Definition |
|------------|------------|
| **GDPR** | All information relating to an "identified or identifiable natural person." Special Category (health, race, trade union membership, etc.) separately protected. |
| **CCPA/CPRA** | "Personal Information" — information directly or indirectly associated with a consumer/household (11 categories). Sensitive PI (SSN, geolocation, health, biometrics, etc.) separately protected. Includes household data. |

**Classification Matrix:**

| Tier | Type | Examples | Protection Level |
|------|------|----------|-----------------|
| Tier 1 | Direct Identifiers | Name, SSN, Email | Highest |
| Tier 2 | Quasi-identifiers | IP, Employee ID | High |
| Sensitive | Special Categories | Biometric, Health, Precise Geolocation | Highest + separate consent |

**Data Minimization Principle:** Immediately delete or anonymize unnecessary data.

### 1.3 Data Flow Mapping / RoPA (2-4 weeks)

Core of GDPR Article 30 Record of Processing Activities (RoPA) and CCPA data inventory.

**RoPA Template Columns:**

| Field | Description |
|-------|-------------|
| Processing Activity | Activity name (e.g., "Employee Time Tracking via IoT") |
| Data Subjects | Subject categories (Employees, Contractors) |
| Categories of Personal Data | Data types (Name, Employee ID, Timestamp, Location) |
| Purposes | Processing purpose (Payroll, Safety Compliance) |
| Lawful Basis | GDPR: Contract / Legitimate Interest / Consent; CCPA: Business Purpose |
| Sources | Collection path (HR System, Badge Reader, Sensors) |
| Storage | Storage location (On-prem Server / AWS us-east-1) |
| Retention | Retention period (Payroll 7 years, Sensor logs 90 days) |
| Recipients | Recipients (Internal HR, Payroll Processor, Insurance) |
| Transfers | International transfers (EU-US: SCC + DPF) |
| Security Measures | Encryption (at-rest/transit), RBAC, MFA, Audit Logs |
| Risks & Mitigation | DPIA required? |

**Manufacturing-specific data flow examples:**

```
Supply Chain: Vendor → ERP → Logistics Partner (International Transfer)
Production: IoT Sensor → MES → Cloud Analytics (OT-IT Convergence)
HR: Onboarding → HRIS → Payroll (Sensitive Data)
B2B: Customer Order → CRM/ERP → Fulfillment
```

**Methodology:** Departmental interviews → Visual diagrams (draw.io) → Evaluate automation tools (OneTrust, DataGrail). Review annually or upon system changes.

### 1.4 Policy Documentation (2-4 weeks)

**Required Document List:**

| Document | Description |
|----------|-------------|
| Privacy Policy / Notice | Integrated policy for website publication (GDPR + CCPA) |
| Notice at Collection | Data collection point notice (web forms, onboarding) |
| Data Processing Agreement (DPA) | Execute with all Processors/Vendors |
| Records of Processing Activities (RoPA) | Record all processing activities |
| Data Subject Rights Procedure (DSAR) | Access, Deletion, Opt-out, Portability process |
| Breach Response Plan | GDPR 72 hours, CCPA prompt notification |
| DPIA/PIA Template | Impact assessment for high-risk processing |
| Vendor/Supply Chain Assessment | Supply chain vendor assessment |
| Employee Training Policy | Annual privacy training |

**Privacy Policy Structure (15-25 pages):**

1. Introduction & Controller Info: Company name, address, DPO/Privacy Contact
2. Personal Information Collected: CCPA category table + GDPR description
3. Sources & Purposes: Collection paths and processing purposes
4. Sharing/Selling: "We do not sell" statement, Service Providers only
5. International Transfers: SCC/DPF description
6. Retention Periods: Per-category retention periods
7. Your Rights: Access, Delete, Opt-out, Correct, etc. and submission methods (email, web form)
8. Security Measures: Encryption, audits
9. Updates & Contact

**CCPA Category Table Example:**

| Category | Collected | Purpose | Disclosed | Sold |
|----------|-----------|---------|-----------|------|
| Identifiers | Yes | Order fulfillment, Security | Service Providers (Logistics) | No |
| Sensitive PI | Yes (Biometric) | Factory access control | No | No |
| Commercial Info | Yes | Order processing | Service Providers | No |

### 1.5 Legal Bases & Specialized Areas

- **GDPR Lawful Basis:** Contract (most common for orders/employment), Legitimate Interest (analytics), Consent (biometric), Legal Obligation.
- **IoT/OT:** Prioritize sensor data pseudonymization; anonymize when unnecessary.
- **HR:** Separate protection for biometric/health records; explicit consent.
- **Supply Chain:** Limit vendor data sharing; DPA mandatory.
- **Cross-border:** EU-US Data Privacy Framework (DPF) or SCC + TIA.

### 1.6 Implementation Timeline

| Period | Activity |
|--------|----------|
| Week 1-4 | Applicability Assessment + Gap Analysis + Data Inventory |
| Week 5-8 | Full Data Mapping & RoPA Build |
| Week 9-12 | Policy Draft + Stakeholder Review |
| Month 4 | Training + Notice Deployment (website, onboarding) |
| Ongoing | Annual Review (linked to Q4 IT Audit) |

---

## 2. Annual IT Audit Policy Design

### 2.1 Overview

**Policy Document:** "Annual IT & OT Security and Privacy Audit Policy" (10-15 pages)

**Objective:** Demonstrate GDPR/CCPA compliance, identify risks, verify control effectiveness, drive continuous improvement.

**Scope:** All IT/OT systems, data flows, PII processing, Vendor/TPRM.

### 2.2 Audit Program (Annual Checklist)

| Domain | Check Items |
|--------|------------|
| **Governance** | Policies current? Roles & Responsibilities clear? |
| **Data Inventory & RoPA** | RoPA matches actual data flows? All PII assets identified? |
| **Access Management** | RBAC/MFA 100% deployed? Privileged access quarterly review? |
| **Data Protection** | Encryption (at-rest/transit) applied? DLP solution operational? Retention auto-deletion? |
| **Vulnerability Management** | Monthly scans performed? Critical patch SLA (48 hours) met? |
| **Incident & Breach** | Annual table-top exercise? GDPR 72hr / CCPA prompt notification tested? |
| **Privacy Controls** | DSAR accuracy/timeliness (sample of 10)? Consent records maintained? |
| **OT/IoT Specific** | Network segmentation? Device inventory current? Firmware updated? |
| **Vendor/TPRM** | High-risk vendor sample audit? DPA compliance verified? |
| **Logging & Monitoring** | Audit trail immutable? SIEM alerting functional? |

### 2.3 Execution Methodology

| Phase | Content |
|-------|---------|
| **Planning** | 1 month prior: scope confirmation, team formation (CISO + Privacy Officer led) |
| **Fieldwork** | 2-4 weeks (remote + on-site factory), Document Review + Interviews + Technical Testing |
| **Reporting** | Executive Summary + Detailed Findings (Risk Rating: Critical/High/Medium/Low) + CAP Template |
| **Follow-up** | Remediation review within 90 days; High risk resolved within 30 days |

### 2.4 Organization & Deliverables

**Lead:** CISO-led, reporting to Audit Committee/Board.

**Participating Departments:** IT, OT, HR, Legal, Business Units. Independent reviewer: Internal Audit or External Auditor.

**Deliverable Templates:**
- Audit Checklist (Excel, with Evidence column)
- Findings Report Template (Issue | Evidence | Risk | Recommendation | Owner | Due Date)
- CAP Tracker (Corrective Action Plan)

### 2.5 Integration

Audit results → Privacy Policy / RoPA / TPRM update (within 30 days). Annual cycle: Q4 Full Audit → Q1 Policy Update.

---

## 3. TPRM Policy Design

### 3.1 Overview

**Policy Document:** "Third-Party Risk Management (TPRM) Policy" (15-20 pages) + Vendor Playbook

**Objective:** Select and manage Trusted Software Developer Partners, fulfill data protection obligations (DPA execution, Audit Rights), minimize supply chain risk.

**Scope:** All Vendors. Especially Software Developers (onshore/offshore, SaaS, custom development). High-risk: PII access, OT/IT integration, cloud hosting.

### 3.2 Vendor Lifecycle

#### A. Selection & Due Diligence

**Trusted Partner Criteria:**
- ISO 27001, SOC 2 Type II, GDPR/CCPA certification or equivalent
- Privacy & Security Program evidence (DPO appointed, Breach Notification SLA ≤ 48 hours)
- Manufacturing experience (OT/IoT security, IEC 62443)
- Financial stability + Cyber Liability Insurance

**Due Diligence Checklist:**
- Questionnaire: Data processing scope, Sub-processor list, Breach history
- Technical Review: Code security practices (SAST/DAST), Encryption, Access controls
- Legal Review: DPA readiness, Governing Law (US + EU)
- Risk Scoring (0-100): PII exposure (40%), Security maturity (30%), Financial (10%), Reputation (20%)

#### B. Contracting

**DPA Mandatory Clauses:**
- Processing only on documented instructions (GDPR Art. 28)
- CCPA: Prohibit Sale/Share as "Service Provider"; Limited Use
- Audit Rights: Annual + For-Cause (Company or delegate)
- Sub-processor: Prior written approval + equivalent protection level
- Breach Notification: Within 24-48 hours
- Data Return/Deletion: Delete with evidence within 30 days of contract termination
- Liability & Indemnification: Compensation for breach-related fines
- International Transfers: SCC/DPF applied
- Insurance: Cyber Liability minimum $5M

**Software Developer-Specific:**
- Secure SDLC required (OWASP, Privacy by Design)
- Code ownership, IP protection, Backdoor prohibition
- Access Logging (developer access to PII)

#### C. Ongoing Monitoring

| Tier | Target | Monitoring Frequency |
|------|--------|---------------------|
| Tier 1 (High-risk) | PII/OT access Software Partners | Quarterly Security Reports + Annual On-site/Remote Audit + Continuous Monitoring |
| Tier 2 (Medium) | General Vendors | Biannual + Continuous Monitoring (security scorecard) |

**KPI:** Uptime ≥99.9%, Incident resolution <4 hours, Zero unauthorized PII access.

**Software Developer-Specific:**
- Code Review / Penetration Testing results sharing
- Access Logging (developer access to PII)
- Privacy Impact Assessment (PIA) upon Change Management
- Code escrow (critical systems)

#### D. Offboarding

- Access Revocation (all accounts, API keys, shared repos)
- Data Deletion Certificate receipt
- Post-termination Audit (within 6 months)

### 3.3 Organization & Governance

- **Lead:** CISO/Privacy Officer + Procurement + Legal
- **TPRM Committee:** Quarterly Meeting — High-risk Vendor Review
- **Tools:** GRC Platform (OneTrust, BitSight, ServiceNow GRC)
- **Training:** Vendor-facing teams (Procurement, IT) — annual

### 3.4 Implementation Timeline

| Period | Activity |
|--------|----------|
| Month 1 | Existing Vendor Inventory + Risk Tiering (Software Partners first) |
| Month 2 | Standardize Questionnaire & DPA Template |
| Month 3-4 | High-risk Contracts Renegotiation |
| Month 5+ | Monitoring Process Rollout + IT Audit Integration |
| Annual | Full TPRM Effectiveness Review |

---

## 4. Integrated Operations & Maintenance

### 4.1 Governance Framework

- **Privacy Committee:** DPO/CISO/Legal-led, Quarterly Meeting
- **Integration Matrix:** Privacy Policy ↔ Audit Findings ↔ TPRM Contracts
- **Document Management:** Central Repository (SharePoint/GRC), Retention 7 years
- **Escalation:** Material findings → Executive Leadership within 7 days

### 4.2 Annual Cycle

| Quarter | Activity |
|---------|----------|
| Q1 | Privacy Training + Policy Review |
| Q2-Q3 | Monitoring & Evidence Collection |
| Q4 | Integrated Audit (IT/OT + Privacy + TPRM) |
| Post-Audit | Remediation tracking → Policy updates |

### 4.3 Overall Implementation Timeline (6-9 months)

| Period | Activity |
|--------|----------|
| Month 1-2 | Assessment & Drafts (Gap Analysis, policy drafts) |
| Month 3-5 | Data Mapping, Contracts Renegotiation, First Audit |
| Month 6+ | Rollout, Training, Monitoring, Annual Cycle entry |

### 4.4 Key Performance Indicators (KPIs)

- RoPA coverage: Target 100%
- Audit findings closure rate: Target 95%+ within 90 days
- Vendor compliance score: Tier 1 average 80+/100
- DSAR response time: GDPR 30 days / CCPA 45 days compliance rate 100%

---

## 5. GitHub Repository Strategy

### 5.1 Objective

Provide the GDPR/CCPA, IT Audit, and TPRM experience listed on my resume in a **publicly verifiable form**. Enable recruiters/hiring managers to review actual policies, templates, and methodologies.

**Repo:** `scale600/it-compliance-framework`

### 5.2 Repository Structure

```
it-compliance-framework/
├── README.md                       # Main landing page
├── LICENSE                         # MIT or CC-BY
├── gdpr-ccpa/
│   ├── policy-template.md          # Full Policy Template
│   ├── ropa-template.md            # RoPA column descriptions and examples
│   ├── data-mapping-example.md     # Manufacturing data flow diagrams (Mermaid)
│   ├── privacy-notice.md           # Website-facing Privacy Notice
│   ├── dpa-template.md             # Standard Data Processing Agreement
│   └── dsar-procedure.md           # Data Subject Access Request procedure
├── it-audit/
│   ├── annual-audit-program.md     # Audit Program details
│   ├── audit-checklist.md          # Domain-level checklist
│   ├── audit-report-template.md    # Findings Report format
│   ├── cap-tracker.md              # Corrective Action Plan Tracker
│   └── ot-iec62443-notes.md        # OT/IoT audit considerations
├── tprm/
│   ├── tprm-framework.md           # Vendor Lifecycle 4-phase details
│   ├── vendor-tiering-matrix.md    # Risk Tier criteria and scoring
│   ├── due-diligence-questionnaire.md  # Vendor assessment questionnaire (20+ items)
│   ├── standard-dpa-template.md    # TPRM-specific DPA
│   └── software-developer-checklist.md # Secure SDLC, Code Review checklist
├── evidence/                       # Anonymized artifacts (critical)
│   ├── bose-tprm-summary.md        # Bose TPRM case study (anonymized)
│   ├── compliance-dashboard.md     # Compliance dashboard example
│   └── audit-findings-example.md   # Audit Findings sample
├── resources/
│   ├── glossary.md                 # Terminology definitions
│   └── references.md               # Reference standards and resources
└── docs/
    ├── overview.md                 # Overall framework overview
    └── manufacturing-use-cases.md  # Manufacturing-specific use cases
```

### 5.3 README.md Key Content

```markdown
# IT Compliance Framework — Manufacturing

**Wonhee Richard Lee** | Senior Cloud Systems Administrator

This repository publicly documents the GDPR/CCPA Compliance, Annual IT & OT Audit,
and TPRM (Third-Party Risk Management) frameworks built at Sena Technologies.

### Key Achievements
- **GDPR/CCPA Framework**: Designed and implemented the full compliance architecture during IPO preparation
- **Annual IT Audit**: Designed and operated integrated IT/OT audit programs
- **TPRM**: Led Vendor Security Assessment for Bose Project → Achieved "Trusted Developer" status

### Repository Sections
- [GDPR & CCPA](./gdpr-ccpa/) — Policies, RoPA, Data Mapping, DPA
- [Annual IT Audit](./it-audit/) — Checklist, Report Template, OT Security
- [TPRM](./tprm/) — Vendor Lifecycle, Software Developer Partners focus

### Manufacturing Focus Areas
- IoT / OT Environment Privacy & Security
- Global Supply Chain Data Flow
- Zero-Trust + Intune + Okta Integration
- Cloud Cost Optimization while maintaining Compliance

**Live Portfolio**: [project.techcloudup.com](https://project.techcloudup.com)
**Contact**: wonhee.eng@gmail.com
```

### 5.4 Implementation Notes

- **Anonymization mandatory:** Company name → "Global Manufacturing Company"; fictionalize data/figures.
- **Format:** Actively use Markdown tables and Mermaid diagrams. Use Markdown tables instead of Excel.
- **GitHub Pages activation:** Publish as website at `https://scale600.github.io/it-compliance-framework`.
- **Resume integration:** Add statement: "Detailed IT Compliance frameworks publicly documented at: github.com/scale600/it-compliance-framework".
- **Pin repo on LinkedIn/GitHub Profile.**

### 5.5 Evidence Folder Importance

The `evidence/` folder is the most critical section determining this repository's credibility. Templates alone do not differentiate from ICO/IAPP materials that anyone can download. Include at least one of the following:

- Actual Audit Findings examples (anonymized)
- Compliance Dashboard configuration example
- Bose TPRM project summary (outcome-focused, excluding confidential information)
- Pre/post-implementation comparison data

---

## Appendix: Key Reference Standards & Tools

| Domain | Standards/Tools |
|--------|----------------|
| Privacy | GDPR, CCPA/CPRA |
| Information Security | ISO 27001, NIST SP 800-53, SOC 2 Type II |
| OT/IoT Security | IEC 62443 |
| Data Mapping | Excel, OneTrust, DataGrail |
| GRC | OneTrust, ServiceNow GRC, RSA Archer |
| Vendor Risk | BitSight, Security Scorecard |
