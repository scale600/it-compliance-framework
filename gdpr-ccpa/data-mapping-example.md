# Manufacturing Data Flow Examples

> **Purpose**: Visualize key PII data flows in a manufacturing environment from collection through processing, storage, and sharing — including IT/OT convergence points.
> **Tooling**: Diagrams rendered in Mermaid (GitHub-compatible). Export to PNG via draw.io for presentations.

---

## 1. Supply Chain Data Flow

```mermaid
flowchart LR
    subgraph Vendor["Vendor (EU)"]
        V[Vendor Contacts<br/>Contract Docs<br/>Bank Details]
    end

    subgraph Company["Manufacturing Company (US)"]
        direction TB
        ERP[ERP System<br/>SAP/Oracle]
        WMS[Warehouse Mgmt<br/>WMS]
        AP[Accounts Payable]
    end

    subgraph Logistics["Logistics Partners"]
        L1[FedEx API]
        L2[UPS API]
        L3[Freight Forwarder]
    end

    V -->|"SCC/DPF<br/>(Intl Transfer)"| ERP
    ERP -->|Order Data| WMS
    ERP -->|Invoice Data| AP
    WMS -->|Shipping Info| L1
    WMS -->|Shipping Info| L2
    ERP -->|"Shipping Docs<br/>(Contact Data)"| L3
```

**Key Compliance Points**:
- EU vendor data enters US ERP → SCC or DPF required
- Logistics partners receive only necessary shipping data (data minimization)
- Vendor bank details stored encrypted in AP; access restricted to Finance

---

## 2. Production Line IoT Data Flow (OT-IT Convergence)

```mermaid
flowchart TB
    subgraph Factory["Factory Floor (OT)"]
        Sensor[IoT Sensors<br/>Temp/Vibration/Worker ID]
        Badge[Badge Readers<br/>Access Control]
        CCTV[CCTV Cameras]
    end

    subgraph OTNet["OT Network (Segmented)"]
        MES[MES Platform<br/>Production Mgmt]
        SCADA[SCADA<br/>Process Control]
        Historian[Data Historian<br/>Time-Series DB]
    end

    subgraph ITNet["IT Network"]
        direction TB
        DMZ[DMZ Gateway]
        Cloud[Cloud Analytics<br/>AWS/Azure]
        HRIS[HRIS<br/>Workday]
        ERP2[ERP]
    end

    Sensor --> MES
    Badge --> MES
    CCTV --> SCADA
    MES --> Historian
    Historian --> DMZ
    DMZ -->|"Aggregated/<br/>Pseudonymized"| Cloud
    Badge -.->|"Attendance<br/>(Worker ID + Time)"| HRIS
    MES -->|"Production<br/>Output"| ERP2
```

**Key Compliance Points**:
- OT network is air-gapped from IT; DMZ gateway enforces data filtering
- Worker ID data pseudonymized before reaching Cloud Analytics
- Raw biometric data stays on-prem; only hashed references cross to HRIS
- CCTV footage stays on OT network; accessed only via jump host with MFA

---

## 3. Employee HR & Biometric Data Flow

```mermaid
flowchart LR
    subgraph Onboarding["Onboarding"]
        App[Application<br/>Name, SSN, DOB]
        Bio[Biometric Enrollment<br/>Fingerprint/Face]
        Train[Safety Training<br/>Records]
    end

    subgraph HR["HR Systems"]
        HRIS2[HRIS<br/>Workday]
        Payroll[Payroll<br/>ADP]
        Access[Access Control<br/>System]

        HRIS2 --> Payroll
        HRIS2 --> Access
    end

    subgraph External["External"]
        ADP[ADP<br/>Payroll Processor]
        Insurance[Health Insurance<br/>Provider]
    end

    App --> HRIS2
    Bio --> Access
    Train --> HRIS2
    Payroll -->|"Encrypted<br/>DPA"| ADP
    HRIS2 -->|"Enrollment Data<br/>DPA"| Insurance
```

**Key Compliance Points**:
- Biometric data stored only in Access Control System (not in HRIS) — data minimization
- ADP and Insurance receive data under DPA with encryption
- Biometric consent obtained at enrollment; revocation triggers deletion within 30 days
- Safety training records retained per OSHA requirements (employment + 5 years)

---

## 4. B2B Customer Order Processing

```mermaid
flowchart LR
    subgraph Customer["B2B Customer"]
        PO[Purchase Order<br/>Contact Name, Email]
        Specs[Technical Specs<br/>May include<br/>personal notes]
    end

    subgraph Company2["Company Systems"]
        CRM[CRM<br/>Salesforce]
        ERP3[ERP<br/>Order Mgmt]
        Eng[Engineering<br/>Document System]
    end

    subgraph Fulfillment["Fulfillment"]
        Warehouse[Warehouse]
        Ship[Shipping Carrier]
        Invoice[Invoicing]
    end

    PO --> CRM
    PO --> ERP3
    Specs --> Eng
    CRM --> ERP3
    ERP3 --> Warehouse
    ERP3 --> Ship
    ERP3 --> Invoice
```

**Key Compliance Points**:
- B2B contacts: primarily "business card" data; GDPR still applies if EU individuals
- Technical specs reviewed for embedded personal data before archival
- No sale/sharing of B2B customer data (CCPA)
- Retention: contract duration + 5 years per tax requirements

---

## 5. Cross-Border Data Transfer Map

```mermaid
flowchart TB
    subgraph EU["EU / EEA"]
        EU_Emp[EU Employees]
        EU_Cust[EU B2B Customers]
        EU_Vend[EU Vendors]
    end

    subgraph US["United States"]
        US_DC[Primary Data Center<br/>On-Prem + AWS us-east-1]
        US_DR[DR Site<br/>AWS us-west-2]
    end

    subgraph APAC["APAC"]
        APAC_Office[APAC Sales Office]
    end

    EU_Emp -->|"SCC + DPF<br/>HR Data"| US_DC
    EU_Cust -->|"SCC + DPF<br/>Order Data"| US_DC
    EU_Vend -->|"SCC<br/>Vendor Data"| US_DC
    US_DC -->|Replication| US_DR
    US_DC -->|"Limited<br/>Sales Data"| APAC_Office
```

**Transfer Safeguards**:

| Transfer Path | Mechanism | TIA Completed |
|--------------|-----------|---------------|
| EU → US (Employee Data) | SCC (Module 2) + DPF | Yes |
| EU → US (Customer Data) | SCC (Module 2) + DPF | Yes |
| EU → US (Vendor Data) | SCC (Module 3) | Yes |
| US → APAC (Sales) | SCC (Module 1) | Yes |

---

## Data Flow Documentation Standards

All data flow diagrams should include:

- [ ] All systems that touch personal data
- [ ] Direction of data movement (arrows)
- [ ] Cross-border transfer points (marked with applicable safeguard)
- [ ] Encryption status (at rest / in transit)
- [ ] Access control boundaries (network segments)
- [ ] Version number and last review date

> **Diagrams below are rendered using Mermaid. GitHub natively supports Mermaid rendering in Markdown files. For presentations, export via [Mermaid Live Editor](https://mermaid.live) or draw.io.**
