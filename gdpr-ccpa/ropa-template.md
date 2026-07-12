# Record of Processing Activities (RoPA) Template

> **Regulatory Basis**: GDPR Article 30 | CCPA Data Inventory  
> **Tool Recommendation**: Excel/Google Sheets → OneTrust, DataGrail for scale

---

## RoPA Structure

Each row represents one **Processing Activity**. All columns must be completed for GDPR compliance. Columns marked with `[CCPA]` are specific to CCPA data inventory requirements.

| # | Column | Description | Example (Manufacturing) |
|---|--------|-------------|--------------------------|
| 1 | **Processing Activity ID** | Unique identifier (e.g., PA-001) | PA-001 |
| 2 | **Processing Activity Name** | Descriptive name of the processing | "Factory Employee Time & Attendance via IoT Badge Readers" |
| 3 | **Department / Business Unit** | Owning department | Manufacturing Operations / HR |
| 4 | **System(s) Involved** | IT/OT systems used | Badge Reader HW → MES → HRIS (Workday) |
| 5 | **Data Subjects** | Categories of individuals | Employees, Contractors, Temporary Workers |
| 6 | **Categories of Personal Data** | Types of data processed | Name, Employee ID, Badge ID, Timestamp, Location (Zone), Shift Pattern |
| 7 | `[Sensitive]` **Special Category Data?** | GDPR Art. 9 or CCPA Sensitive PI? | Yes — Biometric (fingerprint template), potentially Health (if linked to safety) |
| 8 | **Purpose(s) of Processing** | Specific, explicit, legitimate purposes | (1) Attendance tracking for payroll (2) Factory zone access control (3) Safety compliance (evacuation accountability) |
| 9 | **Lawful Basis (GDPR)** | Art. 6/9 basis | (1) Contract (employment) (2) Legitimate Interest (security) (3) Legal Obligation (OSHA safety) |
| 10 | `[CCPA]` **Business Purpose** | CCPA statutory business purpose | Workforce management; security; safety compliance |
| 11 | **Source of Data** | How data is collected | Badge enrollment (HR onboarding); daily badge tap at zone readers |
| 12 | **Storage Location(s)** | Physical or logical location | On-prem SQL Server (Factory A); AWS us-east-1 (DR); Workday cloud |
| 13 | **Retention Period** | How long data is kept | Active: duration of employment. Attendance logs: 7 years (payroll legal). Badge access logs: 90 days. Biometric template: deleted within 30 days of termination |
| 14 | **Recipients** | Internal and external parties | Internal: HR, Line Managers, Facilities Security. External: Payroll Processor (ADP) |
| 15 | **Third-Party Transfers** | Any external sharing | ADP (Payroll Processor) — DPA executed |
| 16 | **International Transfers** | Cross-border data flows | EU badge data replicated to US DR — SCCs in place |
| 17 | **Security Measures** | Technical & organizational | Encryption at rest (AES-256), TLS 1.3 in transit, RBAC (Okta group), MFA, immutable audit logs, biometric data hashed (not stored in raw form) |
| 18 | **DPIA Required?** | High-risk processing trigger? | Yes — systematic monitoring of workers + biometric data at scale |
| 19 | **CCPA Sale/Share?** | Is this data sold or shared for cross-context advertising? | No |
| 20 | **Last Reviewed** | Date of last accuracy check | 2025-06-15 |
| 21 | **Reviewed By** | Name and role of reviewer | [Name], Privacy Officer |

---

## Manufacturing Processing Activity Examples

Below are representative processing activities for a US-based manufacturer with EU customers and CA employees.

### PA-001: Employee Time & Attendance via IoT Badge Readers

| Column | Detail |
|--------|--------|
| Data Subjects | Employees, Contractors |
| Categories | Name, Employee ID, Badge ID, Timestamp, Location Zone, Biometric Template |
| Purpose | Payroll, Access Control, Safety Evacuation |
| Lawful Basis | Contract + Legal Obligation + Legitimate Interest |
| Retention | Payroll: 7 years. Access logs: 90 days. Biometric: deleted 30 days post-termination |
| DPIA | Required — biometric + systematic monitoring |

### PA-002: Vendor Onboarding & Supply Chain Management

| Column | Detail |
|--------|--------|
| Data Subjects | Vendor Representative Contacts |
| Categories | Name, Business Email, Phone, Title, Company Address, Tax ID, Bank Details |
| Purpose | Vendor qualification, purchase order management, payment processing |
| Lawful Basis | Contract + Legal Obligation (tax reporting) |
| Retention | Contract duration + 7 years |
| Transfers | EU vendor data processed in US — SCCs + DPF |
| DPIA | Not required (B2B, limited sensitivity) |

### PA-003: Production Line IoT Sensor Monitoring

| Column | Detail |
|--------|--------|
| Data Subjects | Production Line Workers |
| Categories | Worker ID, Workstation ID, Timestamp, Throughput Count, Quality Metrics, Ergonomic Sensor Data |
| Purpose | Production efficiency analytics, quality control, ergonomic safety |
| Lawful Basis | Legitimate Interest + Legal Obligation (safety) |
| Retention | Raw data: 90 days. Aggregated/anonymized: 3 years |
| Sensitivity | Potentially sensitive if ergonomic data correlates to health |
| DPIA | Required if individual worker performance tracked |

### PA-004: B2B Customer Order Processing

| Column | Detail |
|--------|--------|
| Data Subjects | Customer Procurement/Engineering Contacts |
| Categories | Name, Business Email, Phone, Shipping Address, Order History, Payment Info |
| Purpose | Order fulfillment, invoicing, customer support |
| Lawful Basis | Contract |
| Retention | Contract duration + 5 years |
| CCPA Sale | No |
| DPIA | Not required |

### PA-005: On-Premises CCTV Surveillance

| Column | Detail |
|--------|--------|
| Data Subjects | Employees, Visitors, Contractors |
| Categories | Video footage, Timestamp, Location |
| Purpose | Physical security, theft prevention, incident investigation |
| Lawful Basis | Legitimate Interest |
| Retention | 30 days (looping overwrite) |
| Sensitivity | Indirect biometric if facial recognition used |
| DPIA | Required if facial recognition deployed; otherwise standard |

### PA-006: HR Recruitment & Applicant Tracking

| Column | Detail |
|--------|--------|
| Data Subjects | Job Applicants |
| Categories | Name, Email, Phone, Resume/CV, Work History, Education, References |
| Purpose | Recruitment, candidate evaluation, interview scheduling |
| Lawful Basis | Pre-contractual (Art. 6(1)(b)) + Consent (CV retention > application period) |
| Retention | Unsuccessful: 6 months post-decision (with consent for future roles) |
| Transfers | ATS hosted in US; EU applicants — SCCs |
| DPIA | Not required (standard processing) |

---

## RoPA Maintenance

| Activity | Frequency | Owner |
|----------|-----------|-------|
| New processing activity registration | Before processing begins | Business Unit Owner |
| Existing activity review | Quarterly spot-check; Full annual review | Privacy Officer |
| System change update | Within 30 days of change | IT/OT teams → Privacy Officer |
| Annual audit verification | Q4 | Internal Audit + CISO |

---

## Tooling Progression

| Maturity Level | Tool | Notes |
|---------------|------|-------|
| **Initial** | Excel / Google Sheets | Suitable for <50 processing activities. Use structured columns; avoid free-text. |
| **Growth** | DataGrail, OneTrust, Securiti | Automated data discovery, DSAR automation, DPIA workflows |
| **Enterprise** | OneTrust + ServiceNow GRC integration | End-to-end privacy management + audit trail |
