# Data Subject Access Request (DSAR) Procedure

> **Applicable Regulations**: GDPR Articles 15–22 | CCPA/CPRA §§ 1798.100–1798.130  
> **Version**: 1.0 | **Owner**: Privacy Office  
> **Response SLA**: GDPR — 30 calendar days | CCPA — 45 calendar days

---

## 1. Overview

This procedure defines the end-to-end process for receiving, verifying, fulfilling, and documenting Data Subject Access Requests (DSARs) — also referred to as Data Subject Rights Requests (DSRRs) — from individuals exercising their privacy rights under GDPR and CCPA/CPRA.

---

## 2. Acceptable Submission Channels

Data Subjects may submit requests through any of the following channels:

| Channel | Details | Monitored By |
|---------|---------|-------------|
| **Email** | privacy@[company].com | Privacy Office (daily) |
| **Web Form** | [company].com/privacy-request | Automated → Privacy Office ticketing |
| **Toll-Free Phone** | 1-800-XXX-XXXX | Customer Service → route to Privacy Office |
| **Mail** | Privacy Office, [Company Address] | Privacy Office (weekly) |
| **In Person** | HR Office (employees only) | HR → Privacy Office |

All requests, regardless of channel, must be logged in the **DSAR Tracker** within 1 business day of receipt.

---

## 3. DSAR Intake & Logging

### Step 1: Acknowledge Receipt

- **Within 48 hours** of receipt, send an acknowledgment to the Data Subject confirming:
  - Date of receipt
  - Summary of the request as understood
  - Expected response timeline
  - Note that identity verification will be required
  - A unique **DSAR Reference Number** (format: DSAR-YYYY-NNNN)

### Step 2: Log in DSAR Tracker

| Field | Description |
|-------|-------------|
| DSAR ID | Auto-generated: DSAR-YYYY-NNNN |
| Date Received | Date of initial contact |
| Submission Channel | Email / Web Form / Phone / Mail / In Person |
| Requester Name | Full name as provided |
| Requester Type | Employee / Customer / Vendor / Applicant / Other |
| Jurisdiction | GDPR (EU/EEA) / CCPA (California) / Both |
| Rights Requested | Access / Deletion / Rectification / Portability / Restriction / Objection / Opt-Out / Limit Use |
| Description | Summary of what the Data Subject is requesting |
| Assigned To | Privacy Office team member |
| Status | Received → Verifying → In Progress → Responded → Closed |
| Response Deadline | Calculated based on jurisdiction and receipt date |

---

## 4. Identity Verification

**All requests require identity verification** before any data is disclosed, deleted, or modified.

### Verification Methods

| Requester Type | Primary Verification | Secondary (if needed) |
|---------------|---------------------|----------------------|
| **Current Employee** | Verify with HRIS (Employee ID + email match) | Request government ID copy |
| **Former Employee** | Verify with HRIS archive + last known email | Request government ID copy + signed affidavit |
| **Customer** | Verify against CRM (email + order number match) | Knowledge-based questions (last order date, amount) |
| **Vendor Contact** | Verify against ERP vendor record | Email verification from registered domain |
| **Unknown / Website Visitor** | Two-factor: email verification + knowledge-based | Government ID copy |
| **Authorized Agent (CCPA)** | Verify agent's identity + signed authorization from consumer | Direct confirmation from consumer |

### Verification Rules

- **Do not disclose any Personal Data** during the verification process itself
- If identity cannot be verified after two reasonable attempts, close the request and document the reason
- Record the verification method and date in the DSAR Tracker

---

## 5. Fulfillment Process

### 5.1 Right of Access / Right to Know

1. **Determine scope**: What systems contain the Data Subject's information? Consult RoPA.
2. **Search across systems**: ERP, CRM, HRIS, MES, IoT databases, email archives, file shares (as applicable based on requester type)
3. **Compile response package**:
   - List of categories of Personal Data collected
   - Specific pieces of Personal Data (unless exempt)
   - Sources of collection
   - Business/commercial purpose for collection
   - Categories of third parties with whom data is shared
   - Applicable retention periods
4. **Redact third-party data**: Remove any Personal Data of other individuals from the response
5. **Format**: Provide in a commonly used electronic format (PDF, CSV, JSON) unless the Data Subject requests otherwise

### 5.2 Right to Deletion / Right to Erasure

1. **Verify eligibility**: Confirm the request is not subject to statutory/legal exceptions:
   - Legal retention obligations (tax, OSHA, etc.)
   - Ongoing contract or service relationship
   - Security and fraud prevention
   - Freedom of speech/expression
   - Internal uses reasonably aligned with consumer expectations
2. **Identify all systems** containing the Data Subject's data
3. **Execute deletion** in all identified systems
4. **Notify all recipients** (Service Providers) to delete their copies (if data was shared)
5. **Document exceptions**: If any data cannot be deleted, document the specific legal basis for retention

### 5.3 Right to Rectification / Right to Correct

1. Verify the accuracy of the correction requested
2. Update all systems containing the inaccurate data
3. Notify any recipients who received the inaccurate data
4. Confirm correction to the Data Subject

### 5.4 Right to Data Portability

1. Extract the Data Subject's data from relevant systems
2. Format in a structured, commonly used, machine-readable format (JSON, CSV)
3. Transmit directly to the Data Subject (or to another controller, if technically feasible)

### 5.5 Right to Opt-Out (CCPA) / Right to Object (GDPR)

- **CCPA Opt-Out of Sale/Sharing**: The Company does not sell or share PI for cross-context advertising. Respond within 15 business days confirming this and noting that no action is required.
- **GDPR Right to Object**: Evaluate the objection against the Company's legitimate interests. If the objection is valid, cease processing for the objected purpose.

### 5.6 Right to Limit Use of Sensitive PI (CCPA)

If a Data Subject requests limitation of sensitive PI use beyond authorized business purposes, cease such use within 15 business days and confirm.

---

## 6. Response Communication

### Response Content

All DSAR responses must include:

1. DSAR Reference Number
2. Summary of action taken
3. The response data (for access requests) or confirmation (for deletion/rectification)
4. Explanation of any data that could not be provided/deleted and the legal basis for the exception
5. Instructions for appeal (CCPA) or complaint to supervisory authority (GDPR)

### Response Method

- Deliver through the same channel as the original request, unless the Data Subject specifies otherwise
- Encrypt all email responses containing Personal Data; send decryption key separately
- Do not send sensitive data (SSN, biometric) via email — use secure portal or registered mail

---

## 7. Timeline Management

| Jurisdiction | Standard Response Time | Extension Possible? | Max Total |
|-------------|----------------------|---------------------|-----------|
| **GDPR** | 30 calendar days | Yes (+60 days for complex/multiple requests) | 90 days |
| **CCPA** | 45 calendar days | Yes (+45 days) | 90 days |

### Extension Procedure

If an extension is needed:

1. Notify the Data Subject **before** the original deadline expires
2. Explain the reason for delay
3. Provide the new expected response date
4. Log the extension in the DSAR Tracker

---

## 8. Exemptions & Refusals

A request may be refused (in whole or in part) only in limited circumstances:

| Grounds for Refusal | Applicable Law | Documentation Required |
|--------------------|---------------|----------------------|
| Manifestly unfounded or excessive (repetitive) | GDPR Art. 12(5) | Document frequency and nature of previous requests |
| Identity cannot be verified | Both | Document verification attempts |
| Would adversely affect rights of others | GDPR Art. 15(4) | Document the conflicting rights |
| Legal obligation to retain | Both | Cite specific law/regulation (e.g., IRS 7-year retention) |
| Request is for the second time in a 12-month period (CCPA Access) | CCPA | Document prior response date |

**All refusals must be documented with the specific reason and approved by the Privacy Officer or Legal counsel.**

---

## 9. DSAR Metrics & Reporting

Monthly metrics tracked:

| Metric | Target |
|--------|--------|
| Total DSARs received | — |
| Within deadline response rate | 100% |
| Average response time | <15 days |
| Verification failure rate | <5% |
| Deletion requests fulfilled (vs. partial/refused) | Track ratio |
| Repeat requests from same individual | Flag if >2/year |

Quarterly report to Privacy Committee.

---

## 10. Roles & Responsibilities

| Role | Responsibility |
|------|---------------|
| **Privacy Office** | Overall DSAR process owner; intake logging; complex request handling; regulatory reporting |
| **HR** | Employee DSAR intake; HRIS data retrieval; biometric data coordination |
| **IT / OT Teams** | System-level data search; deletion execution; access log retrieval |
| **Customer Service** | Customer request intake and routing |
| **Legal** | Exemption determinations; appeal handling; regulatory complaint response |
| **CISO** | Security-related exceptions; audit log support |

---

## 11. Related Documents

- [GDPR & CCPA Policy Template](./policy-template.md)
- [RoPA Template](./ropa-template.md)
- [Annual IT Audit Checklist](../it-audit/audit-checklist.md) (includes DSAR testing)
- [Breach Response Plan](./breach-response-plan.md)

---

## Appendix A: DSAR Tracker Template (Excel Columns)

| Column | Type | Description |
|--------|------|-------------|
| DSAR ID | Text | Auto-generated |
| Date Received | Date | Request receipt date |
| Channel | Dropdown | Email / Web / Phone / Mail / In Person |
| Requester Name | Text | Full name |
| Requester Type | Dropdown | Employee / Former Employee / Customer / Vendor / Applicant / Other |
| Jurisdiction | Dropdown | GDPR / CCPA / Both |
| Rights Requested | Multi-select | Access / Deletion / Rectification / Portability / Restriction / Objection / Opt-Out / Limit Use |
| Verification Method | Dropdown | HRIS / CRM / Email / KBA / Government ID / Agent Authorization |
| Verification Date | Date | Date identity confirmed |
| Status | Dropdown | Received / Verifying / In Progress / Responded / Closed |
| Assigned To | Text | Team member |
| Response Deadline | Date | Calculated based on jurisdiction |
| Extension Requested? | Yes/No | |
| Extended Deadline | Date | If applicable |
| Response Date | Date | Date response sent |
| Data Provided? | Yes/No/Partial | |
| Deletion Executed? | Yes/No/Partial | |
| Exemptions Applied | Text | Legal basis for any withheld data |
| Notes | Text | Free text |

## Appendix B: Response Letter Templates

### Access Request Response (GDPR)

```
Subject: Response to Your Data Access Request — DSAR-YYYY-NNNN

Dear [Name],

We refer to your request dated [Date] to access your Personal Data under Article 15 of 
the General Data Protection Regulation (GDPR).

Please find attached the Personal Data we hold about you in a portable electronic format. 
[OR] We confirm that after a thorough search of our systems, we do not hold Personal Data 
about you beyond what was used to process this request.

[If partial:] We have not provided [categories] because [legal basis for withholding].

You have the right to lodge a complaint with [Supervisory Authority Name] if you are not 
satisfied with our response.

Sincerely,
Privacy Office
[Company Name]
```
