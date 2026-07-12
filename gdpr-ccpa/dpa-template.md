# Data Processing Agreement (DPA)

> **Parties**: [Controller Name] ("Controller") and [Processor Name] ("Processor")  
> **Effective Date**: [Date]  
> **Incorporated by Reference into**: [Master Services Agreement / Contract Reference]

---

## 1. Definitions

Terms used in this DPA shall have the meanings set forth in this DPA. Capitalized terms not otherwise defined herein shall have the meaning given to them in the Agreement.

| Term | Definition |
|------|------------|
| **Controller** | The entity that determines the purposes and means of the Processing of Personal Data. |
| **Processor** | The entity that Processes Personal Data on behalf of the Controller. |
| **Data Subject** | The identified or identifiable natural person to whom Personal Data relates. |
| **Personal Data** | Any information relating to a Data Subject (GDPR) / Personal Information (CCPA). |
| **Processing** | Any operation performed on Personal Data (collection, storage, use, transfer, deletion, etc.). |
| **Sub-Processor** | Any third party engaged by Processor to Process Personal Data on behalf of Controller. |
| **SCC** | Standard Contractual Clauses (EU 2021/914) for international data transfers. |
| **Security Incident** | Any breach of security leading to accidental or unlawful destruction, loss, alteration, unauthorized disclosure of, or access to, Personal Data. |

---

## 2. Scope of Processing

### 2.1 Subject Matter and Duration

| Item | Detail |
|------|--------|
| **Subject Matter** | [e.g., Cloud hosting of ERP data, Payroll processing, IoT analytics platform] |
| **Duration** | For the term of the Agreement, plus [30] days for data return/deletion |
| **Nature and Purpose** | [e.g., Hosting and processing employee attendance data for payroll calculation] |
| **Categories of Data Subjects** | [e.g., Employees, Contractors, B2B customer contacts] |
| **Categories of Personal Data** | [e.g., Name, Employee ID, Timestamp, Location Zone, Shift Data] |
| **Sensitive Data** | [Yes/No — if Yes, specify: Biometric templates, Health records] |

### 2.2 Processing Instructions

Processor shall Process Personal Data **only** on documented instructions from Controller, including with regard to transfers of Personal Data to a third country or international organization, unless required to do so by applicable law. In such case, Processor shall inform Controller of that legal requirement before Processing, unless prohibited by law.

---

## 3. Processor Obligations

### 3.1 Compliance with Laws

Processor shall comply with all applicable data protection laws, including GDPR and CCPA/CPRA. Processor shall not:

- **Sell** or **share** Personal Data (as defined by CCPA)
- Retain, use, or disclose Personal Data for any purpose other than the specific business purpose specified in this DPA
- Retain, use, or disclose Personal Data outside the direct business relationship between Controller and Processor
- Combine Personal Data received from Controller with Personal Data from other sources, except as permitted by law

### 3.2 Confidentiality

Processor shall ensure that persons authorized to Process Personal Data have committed themselves to confidentiality or are under an appropriate statutory obligation of confidentiality.

### 3.3 Security Measures

Processor shall implement appropriate technical and organizational measures to ensure a level of security appropriate to the risk, including:

| Category | Required Measures |
|----------|-------------------|
| **Encryption** | AES-256 at rest; TLS 1.3 in transit |
| **Access Control** | RBAC with least privilege; MFA enforced; quarterly access review |
| **Logging** | Immutable audit logs; SIEM monitoring; anomaly detection |
| **Vulnerability Management** | Monthly vulnerability scans; critical patch deployment within 48 hours |
| **Business Continuity** | Documented DR plan; RTO ≤ 4 hours; RPO ≤ 1 hour |
| **Physical Security** | SOC 2 Type II certified data center; biometric access control |

### 3.4 Sub-Processors

Processor shall not engage any Sub-Processor without Controller's prior **written authorization**. The Controller provides general authorization for the Sub-Processors listed in **Schedule A**. Processor shall:

1. Inform Controller of any intended changes concerning the addition or replacement of Sub-Processors at least [15] days in advance
2. Impose the same data protection obligations on Sub-Processors as set forth in this DPA
3. Remain fully liable to Controller for the performance of Sub-Processor obligations

### 3.5 Data Subject Rights

Processor shall, to the extent legally permitted, promptly notify Controller if it receives a request from a Data Subject to exercise their rights under applicable data protection law. Processor shall not respond to such request directly without Controller's prior written consent, unless legally obligated. Processor shall assist Controller by appropriate technical and organizational measures, insofar as possible, for the fulfillment of Controller's obligation to respond to Data Subject requests.

### 3.6 Security Incident Notification

Processor shall notify Controller **without undue delay, and in any event within [24-48] hours** after becoming aware of a Security Incident. The notification shall:

1. Describe the nature of the Security Incident, including categories and approximate number of Data Subjects and Personal Data records concerned
2. Communicate the name and contact details of the Processor's data protection officer or other contact point
3. Describe the likely consequences of the Security Incident
4. Describe the measures taken or proposed to address the Security Incident, including measures to mitigate adverse effects

Processor shall cooperate with Controller and take reasonable steps to investigate, mitigate, and remediate each Security Incident.

### 3.7 Data Protection Impact Assessment (DPIA)

Processor shall provide reasonable assistance to Controller with any Data Protection Impact Assessments and prior consultations with supervisory authorities, as required by GDPR Article 35 and 36.

---

## 4. Audit Rights

### 4.1 Audit Frequency

Controller (or its designated independent auditor) may audit Processor's compliance with this DPA:

- **Annually** (scheduled audit, minimum 30 days' notice)
- **For Cause** (in the event of a Security Incident or reasonable suspicion of non-compliance, minimum 48 hours' notice)

### 4.2 Audit Scope

Audits may include review of:

- Security policies and procedures
- Access control logs
- Vulnerability and penetration test reports
- Sub-Processor agreements
- Physical security controls
- Employee training records

### 4.3 Audit Reports

Processor shall provide a summary of its most recent SOC 2 Type II or ISO 27001 audit report upon Controller's request (annually). If such report demonstrates compliance, Controller may accept it in lieu of an on-site audit for that year.

---

## 5. International Data Transfers

### 5.1 Transfer Mechanism

Where Personal Data is transferred from the EEA/UK to a country not recognized as providing an adequate level of protection, the parties shall rely on:

- The **EU Standard Contractual Clauses (SCC)** — Module 2 (Controller to Processor) or Module 3 (Processor to Sub-Processor), as applicable, attached as **Schedule B**
- The **UK International Data Transfer Addendum** (where UK GDPR applies)
- Any successor or additional mechanism recognized under applicable law

### 5.2 Transfer Impact Assessment

Processor shall cooperate with Controller's Transfer Impact Assessment (TIA) and shall implement supplementary measures as reasonably requested by Controller to address identified risks.

---

## 6. Data Return and Deletion

Upon termination of the Agreement or upon Controller's written request, Processor shall, at Controller's election:

1. **Return** a complete copy of all Personal Data in a standard, machine-readable format, or
2. **Securely Delete** all Personal Data (including all copies and backups)

within **[30] calendar days**. Processor shall provide Controller with a **Certificate of Deletion** confirming completion. Any retention beyond this period is permitted only where required by applicable law, and Processor shall inform Controller of such requirement.

---

## 7. Liability and Indemnification

### 7.1 Allocation of Liability

Each party's liability arising out of or related to this DPA shall be subject to the limitations and exclusions set out in the Agreement. Notwithstanding the foregoing, **Processor shall indemnify and hold harmless Controller** against all claims, fines, penalties, damages, and costs (including reasonable legal fees) arising from:

- Processor's breach of this DPA
- Processor's violation of applicable data protection law
- Processor's unauthorized Processing, sale, or sharing of Personal Data

### 7.2 Insurance

Processor shall maintain Cyber Liability Insurance with a minimum coverage of **$5,000,000** per occurrence and shall provide evidence of such coverage upon request.

---

## 8. Miscellaneous

### 8.1 Governing Law

This DPA shall be governed by the laws of [State/Country], without regard to conflicts of law principles.

### 8.2 Severability

If any provision of this DPA is held invalid or unenforceable, the remaining provisions shall continue in full force and effect.

### 8.3 Order of Precedence

In the event of any conflict between this DPA and the Agreement, this DPA shall prevail with respect to data protection and privacy obligations. For international transfers, the SCC shall prevail.

### 8.4 Amendments

No amendment to this DPA shall be effective unless in writing and signed by both parties.

---

## Schedule A — Approved Sub-Processors

| Sub-Processor | Service Provided | Location | Transfer Mechanism |
|--------------|------------------|----------|-------------------|
| [Name] | [e.g., Cloud hosting] | [Country] | SCC |
| [Name] | [e.g., Monitoring/APM] | [Country] | SCC |

---

## Schedule B — Standard Contractual Clauses

*[Attach executed EU SCC (2021/914) — Module 2 (C→P) or Module 3 (P→SP) as applicable]*

---

**Signatures**

| Controller | Processor |
|------------|-----------|
| Name: | Name: |
| Title: | Title: |
| Date: | Date: |
| Signature: | Signature: |
