# Standard DPA Template — TPRM (Software Developer Partners)

> **Note**: This DPA template supplements the [General DPA Template](../gdpr-ccpa/dpa-template.md) with software developer-specific provisions. Both documents should be incorporated into the Master Services Agreement.

---

## Software Developer-Specific Annex to DPA

### 1. Secure Development Obligations

Processor (Software Developer) shall:

1. **Maintain a Secure SDLC** aligned with OWASP SAMM or NIST SSDF, including at minimum:
   - Threat modeling during design phase
   - Static Application Security Testing (SAST) integrated into CI/CD pipeline
   - Software Composition Analysis (SCA) for all third-party dependencies
   - Dynamic Application Security Testing (DAST) prior to each major release
   - Manual security code review for all code paths handling Sensitive Personal Data
   - Remediation of Critical/High vulnerabilities before production deployment

2. **Provide** upon Controller's annual request:
   - Executive summary of most recent penetration test
   - SAST/DAST scan results for the prior 12 months
   - SCA dependency vulnerability report
   - Summary of security-related code review findings and remediation

3. **Prohibit** the introduction of:
   - Backdoors, undocumented access mechanisms, or telemetry without Controller's written consent
   - Hardcoded credentials, API keys, or secrets in source code
   - Debug mode, verbose logging of PII, or development tools in production environments

### 2. Developer Access & Personnel Security

1. **Access to Production Systems**: Developer access to production environments or production data is prohibited unless explicitly authorized in writing by Controller. Where authorized:
   - Access shall be time-limited (maximum 4-hour session)
   - All sessions shall be logged and recorded (keystroke-level or video recording)
   - Access shall require Controller's pre-approval via a formal change ticket
   - Break-glass access shall trigger immediate notification to Controller's CISO

2. **Access to Source Code & Repositories**:
   - Access shall be granted on a least-privilege, need-to-know basis
   - All repository actions shall be logged with immutable audit trails
   - Two-factor authentication shall be enforced for all repository access
   - Branch protection rules shall prevent direct pushes to main/master; all changes require peer review

3. **Personnel Vetting**:
   - All personnel with access to Controller's code, data, or systems shall undergo background checks (criminal, employment verification, education) prior to assignment
   - Personnel shall sign individual confidentiality agreements covering Controller's data
   - Upon personnel termination or reassignment, all access shall be revoked within 24 hours

### 3. Code Quality & Intellectual Property

1. **Code Ownership**: All custom-developed code, configurations, documentation, and derivative works created for Controller shall be Controller's sole and exclusive intellectual property. Processor hereby assigns all rights, title, and interest in such works to Controller.

2. **Third-Party Components**: Processor shall maintain an inventory (SBOM — Software Bill of Materials) of all third-party libraries, frameworks, and components used in Controller's software. This inventory shall be provided to Controller:
   - Upon initial delivery
   - Updated quarterly thereafter
   - Within 5 business days upon Controller's request

3. **Code Escrow**: For software deemed critical by Controller, Processor shall deposit source code with a mutually agreed neutral third-party escrow agent. Release conditions shall include:
   - Processor's bankruptcy, insolvency, or cessation of operations
   - Processor's material breach of support obligations uncured for 30 days
   - Processor's acquisition by a competitor of Controller

### 4. Change Management & Privacy Impact

1. **Change Notification**: Processor shall notify Controller at least 30 days in advance of any material change to:
   - Data processing locations or sub-processors
   - Security architecture or encryption methods
   - Software architecture that affects how PII is collected, processed, or stored

2. **Privacy Impact Assessment (PIA)**: For any change that introduces new PII processing or modifies existing PII processing, Processor shall:
   - Provide a PIA or security impact analysis to Controller 30 days before implementation
   - Not proceed with the change without Controller's written approval

3. **No Unauthorized Features**: Processor shall not introduce new features that process PII beyond the scope defined in this DPA without Controller's prior written consent and a corresponding DPA amendment.

### 5. Sub-Processor & Supply Chain

1. For software development services, Processor's Sub-Processors commonly include:
   - Cloud hosting platforms (IaaS/PaaS)
   - Code repository services
   - CI/CD pipeline services
   - Monitoring and APM tools
   - Communication and collaboration tools

2. Processor shall maintain an up-to-date list of all Sub-Processors in Schedule A and shall not engage new Sub-Processors without 30 days' prior notice and Controller's right to object.

3. For offshore development centers, Processor shall:
   - Provide details of physical security controls at the development facility
   - Confirm that no PII data leaves the authorized processing locations
   - Implement network controls preventing local storage/download of PII to developer workstations

### 6. Audit Rights — Software Development Specific

In addition to the general audit rights in the DPA, Controller may audit:

- Source code repositories (access controls, branch protection, commit history)
- CI/CD pipeline configuration (security gates, SAST/DAST integration)
- Developer workstation configurations (encryption, endpoint protection, screen lock)
- Code review records and approval workflows
- Dependency management and vulnerability remediation tracking

### 7. Breach Notification — Extended

For software-specific incidents, Processor shall additionally notify Controller within 4 hours if:

- Unauthorized code has been committed to Controller's repositories
- Secrets or credentials related to Controller's systems have been exposed
- A Sub-Processor's breach could affect Controller's code or data

---

**This Annex is incorporated by reference into the Data Processing Agreement between [Controller] and [Processor], effective [Date].**

| Controller | Processor |
|------------|-----------|
| Name: | Name: |
| Title: | Title: |
| Date: | Date: |
