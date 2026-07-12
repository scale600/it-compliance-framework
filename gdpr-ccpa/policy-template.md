# GDPR & CCPA Compliance Policy Template

> **Reference Implementation** — Manufacturing Environment  
> **Version**: 1.0 | **Classification**: Internal — Confidential  
> **Last Reviewed**: [Date] | **Next Review**: [Date + 1 Year]  
> **DPO / Privacy Contact**: [Name, Email, Phone]

---

## 1. Introduction & Scope

### 1.1 Purpose

This Global Data Privacy Policy establishes the framework for compliance with the **EU General Data Protection Regulation (GDPR)** and the **California Consumer Privacy Act / California Privacy Rights Act (CCPA/CPRA)** at [Company Name] ("the Company").

### 1.2 Applicability

This policy applies to all processing of Personal Data where:

- **GDPR Applies**: Processing of Personal Data of individuals located in the European Economic Area (EEA), regardless of the individual's nationality or residence, including employees, B2B customer contacts, and vendor representatives.
- **CCPA/CPRA Applies**: Processing of Personal Information of California residents that meets one or more statutory thresholds (≥$25M annual revenue, or buying/receiving/selling PI of ≥100,000 CA consumers/households, or deriving ≥50% revenue from selling PI).

### 1.3 Scope — Manufacturing Environment

| Domain | Covered Activities |
|--------|-------------------|
| **Employees & Workers** | HR records, payroll, biometric access control, safety training records, CCTV, worker performance logs |
| **B2B Customers** | Contact information for purchasing/engineering contacts, order specifications containing personal data, payment information |
| **Supply Chain / Vendors** | Vendor contacts, contract documents, financial information, shipping addresses |
| **Production / IoT** | Worker IDs linked to sensor data (location, time), quality inspection logs, wearable device data |
| **IT / OT Systems** | ERP, MES, CRM, HRIS, WMS, PLC/SCADA, IoT sensor networks, cloud platforms (AWS/Azure) |

---

## 2. Definitions

### 2.1 GDPR Definitions

| Term | Definition |
|------|------------|
| **Personal Data** | Any information relating to an identified or identifiable natural person ("Data Subject") — including name, email, IP address, location data, biometric data, and inferred data |
| **Special Categories of Personal Data** | Data revealing racial/ethnic origin, political opinions, religious beliefs, trade union membership, genetic data, biometric data (for identification), health data, sex life/orientation |
| **Processing** | Any operation performed on personal data (collection, storage, use, transfer, deletion, etc.) |
| **Controller** | Entity determining the purposes and means of processing |
| **Processor** | Entity processing personal data on behalf of the Controller |

### 2.2 CCPA/CPRA Definitions

| Term | Definition |
|------|------------|
| **Personal Information (PI)** | Information that identifies, relates to, describes, is reasonably capable of being associated with, or could reasonably be linked with a particular consumer or household (11 statutory categories) |
| **Sensitive Personal Information** | SSN, driver's license, financial account credentials, precise geolocation, racial/ethnic origin, biometric information, health data — subject to right to limit use |
| **Service Provider** | Entity processing PI on behalf of a business under a written contract with specific prohibitions |
| **Sale / Share** | Disclosing PI to a third party for monetary or other valuable consideration (sale) or for cross-context behavioral advertising (sharing) |

---

## 3. Data Collection & Processing

### 3.1 Processing Activities Register

The Company maintains a **Record of Processing Activities (RoPA)** as required by GDPR Article 30. Each processing activity is documented with: data categories, data subjects, purposes, lawful basis, sources, storage locations, retention periods, recipients, international transfers, and security measures.

> See [RoPA Template](./ropa-template.md) for the detailed tracking structure.

### 3.2 Lawful Bases for Processing (GDPR — Article 6)

| Basis | Typical Manufacturing Application |
|-------|----------------------------------|
| **Contract** | Processing employee data for payroll; processing customer orders; fulfilling vendor agreements |
| **Legal Obligation** | Tax/social security reporting; workplace safety records (OSHA); export control documentation |
| **Legitimate Interest** | IT/OT system security monitoring; production analytics (anonymized); supply chain optimization |
| **Consent** | Biometric data for factory access; marketing communications; non-essential cookies |
| **Vital Interests** | Emergency medical information |
| **Public Task** | Regulatory reporting to government agencies |

### 3.3 CCPA Business Purposes

All PI processing is limited to the following business/commercial purposes:

- Order fulfillment and customer service
- Security and fraud prevention
- Quality assurance and production analytics
- Legal and regulatory compliance
- Workforce management and safety

---

## 4. Data Subject Rights

### 4.1 Rights Under GDPR

Data Subjects have the following rights:

1. **Right of Access** (Art. 15) — Obtain confirmation of processing and a copy of personal data
2. **Right to Rectification** (Art. 16) — Correct inaccurate personal data
3. **Right to Erasure** (Art. 17) — Request deletion ("Right to be Forgotten") subject to legal retention obligations
4. **Right to Restriction** (Art. 18) — Limit processing in specific circumstances
5. **Right to Data Portability** (Art. 20) — Receive data in a structured, machine-readable format
6. **Right to Object** (Art. 21) — Object to processing based on legitimate interest or direct marketing
7. **Rights re Automated Decision-Making** (Art. 22) — Not subject to solely automated decisions with legal effects

**Response Timeline**: Within one month (extendable by two months for complex requests).

### 4.2 Rights Under CCPA/CPRA

California residents have the following rights:

1. **Right to Know** — Request disclosure of PI collected, used, shared, or sold (12-month lookback)
2. **Right to Delete** — Request deletion of PI, subject to statutory exceptions
3. **Right to Opt-Out of Sale/Sharing** — The Company **does not sell** PI; this right is provided for transparency
4. **Right to Correct** — Request correction of inaccurate PI
5. **Right to Limit Use of Sensitive PI** — Limit use of sensitive PI to authorized business purposes

**Response Timeline**: 45 days (extendable by additional 45 days).

### 4.3 Submitting a Request

Data Subjects may submit requests via:

- **Email**: privacy@[company].com
- **Web Form**: [company].com/privacy-request
- **Toll-Free**: 1-800-XXX-XXXX
- **Mail**: Privacy Office, [Company Address]

**Verification**: All requests require identity verification (two-factor: email confirmation + knowledge-based verification or government ID for sensitive data).

> See [DSAR Procedure](./dsar-procedure.md) for the complete intake and fulfillment workflow.

---

## 5. Data Sharing & International Transfers

### 5.1 Third-Party Sharing

| Recipient Type | Categories Shared | Safeguards |
|---------------|-------------------|------------|
| **Service Providers** (cloud, payroll, logistics) | Employee data, customer orders, shipping info | DPA executed; audit rights; encryption |
| **Supply Chain Partners** | Vendor contacts, order specifications | DPA executed; data minimization |
| **Regulatory Authorities** | As required by law | Legal obligation basis; documentation retained |
| **No Sale**: The Company does **not** sell, share for cross-context behavioral advertising, or otherwise monetize Personal Data/PI. | | |

### 5.2 International Data Transfers

Where Personal Data is transferred outside the EEA or UK to the United States or other third countries, the Company implements the following safeguards:

- **EU-US Data Privacy Framework (DPF)**: Where the recipient is DPF-certified
- **Standard Contractual Clauses (SCC)**: EU SCCs (2021/914) incorporated into Data Processing Agreements
- **Transfer Impact Assessment (TIA)**: Conducted for each transfer to evaluate the legal regime of the destination country
- **Supplementary Measures**: Encryption at rest and in transit, access controls, data minimization

---

## 6. Data Retention

| Data Category | Retention Period | Basis |
|--------------|------------------|-------|
| Employee payroll/tax records | 7 years | Legal obligation (IRS/state) |
| Employee safety/training records | Duration of employment + 5 years | OSHA requirements |
| Biometric access logs | 90 days active; purged after 1 year | Legitimate interest (security) |
| IoT/sensor production data | 90 days (raw); 3 years (aggregated/anonymized) | Legitimate interest (quality analytics) |
| Customer order data | Contract duration + 5 years | Contract; tax requirements |
| Vendor contracts | Contract duration + 7 years | Legal obligation |
| CCTV footage | 30 days | Legitimate interest (security) |
| Marketing data | Until consent withdrawal | Consent |

**Automatic Deletion**: Data exceeding retention periods is automatically flagged and securely deleted per the Company's Data Retention Schedule, enforced through the Data Loss Prevention (DLP) system.

---

## 7. Security Measures

### 7.1 Technical Measures

- **Encryption**: AES-256 at rest; TLS 1.3 in transit
- **Access Control**: Role-Based Access Control (RBAC) with Okta SSO; Multi-Factor Authentication (MFA) enforced for all systems containing PII
- **Logging & Monitoring**: SIEM (Splunk/Azure Sentinel) with immutable audit trails
- **Vulnerability Management**: Monthly vulnerability scans; critical patch SLA: 48 hours
- **Data Loss Prevention (DLP)**: Endpoint DLP with PII detection rules
- **OT Network Segmentation**: IT/OT network separation per IEC 62443; jump hosts for OT access

### 7.2 Organizational Measures

- Annual privacy and security training for all employees
- Background checks for personnel with PII access
- Privacy by Design and Default (GDPR Art. 25) in all new systems/projects
- Data Protection Impact Assessment (DPIA) for high-risk processing
- Confidentiality agreements for all employees and contractors

---

## 8. Breach Response

### 8.1 GDPR Breach Notification

- **Internal Escalation**: Any suspected breach must be reported to the Privacy Office within 2 hours of discovery
- **Supervisory Authority Notification**: Within **72 hours** of becoming aware (Art. 33)
- **Data Subject Notification**: Without undue delay if high risk to individuals (Art. 34)
- **Documentation**: All breaches documented in the Breach Register, including facts, effects, and remedial actions

### 8.2 CCPA Breach Notification

- Notification to affected CA residents "in the most expedient time possible and without unreasonable delay"
- California Attorney General notification if ≥500 CA residents affected

> See [Breach Response Plan](./breach-response-plan.md) for full procedures.

---

## 9. Vendor & Processor Obligations

All third-party vendors and processors handling Personal Data/PI must:

- Execute a **Data Processing Agreement (DPA)** prior to processing
- Adhere to documented processing instructions only
- Implement appropriate technical and organizational measures
- Notify the Company of any sub-processor engagement (with prior approval)
- Report security incidents within 24–48 hours
- Submit to annual compliance audits (Company or independent auditor)
- Return or delete all data upon contract termination

> See [DPA Template](./dpa-template.md) and [TPRM Framework](../tprm/tprm-framework.md).

---

## 10. Accountability & Governance

### 10.1 Roles & Responsibilities

| Role | Responsibility |
|------|---------------|
| **Data Protection Officer (DPO)** / **Privacy Officer** | Overall compliance oversight; RoPA maintenance; regulatory contact |
| **CISO / IT Security** | Technical controls; incident response; audit execution |
| **Business Unit Owners** (HR, Supply Chain, Production) | Data mapping accuracy; process adherence; training compliance |
| **Legal** | Regulatory interpretation; DPA review; breach notification decisions |
| **All Employees** | Policy compliance; mandatory training; incident reporting |

### 10.2 Review Cycle

- **Annual Policy Review**: Full review by Q4 each year (aligned with Annual IT Audit findings)
- **Trigger-Based Review**: Upon regulatory change, significant system change, or breach incident
- **Stakeholder Approval**: Privacy Officer, CISO, and Legal

---

## 11. Policy Updates & Contact

This policy is reviewed annually. Material changes will be communicated to all employees and published on the Company intranet/website.

**Contact**:
- Privacy Office: privacy@[company].com
- DPO: [Name], [Email], [Phone]
- Mailing: [Company Address]

---

**Document Control**

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | [Date] | [Author] | Initial release |
