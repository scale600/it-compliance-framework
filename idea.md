# IT Compliance Framework — 미국 제조업 GDPR/CCPA, IT Audit, TPRM 정책 수립 및 GitHub 공시 전략

> **Wonhee Richard Lee** | Senior Cloud Systems Administrator
>
> Sena Technologies에서의 IPO 지원, Annual IT/OT Audit 설계, Bose Project TPRM 경험을 바탕으로 한 실무 방법론 문서입니다. 본 문서는 `scale600/it-compliance-framework` GitHub Repository의 설계 기반이며, 이력서에 언급된 GDPR/CCPA, IT Audit, TPRM 경험을 공개적으로 검증 가능한 형태로 제공하는 것이 최종 목표입니다.
>
> 법률 전문가(변호사/DPO) 검토 필수. 본 문서는 일반 가이드이며 회사 상황에 맞게 커스터마이징 필요.

---

## 목차

1. [GDPR & CCPA 정책 수립](#1-gdpr--ccpa-정책-수립)
2. [Annual IT Audit 정책 수립](#2-annual-it-audit-정책-수립)
3. [TPRM 정책 수립](#3-tprm-정책-수립)
4. [통합 운영 및 유지보수](#4-통합-운영-및-유지보수)
5. [GitHub Repository 전략](#5-github-repository-전략)

---

## 제조업 특성 및 주요 PII 흐름

미국 제조업(automotive, machinery, electronics, consumer goods 등)은 IT(ERP, CRM, HRIS) + OT(생산 라인, IoT 센서, PLC/SCADA) 시스템이 복잡하게 연결됩니다. 주요 PII 흐름:

| 영역 | 데이터 유형 | 주요 시스템 |
|------|------------|------------|
| 직원/작업자 | 이름, SSN, biometric(지문/얼굴인식), 건강/안전 기록, 작업 로그, CCTV | HRIS(Workday), Payroll, 출입 시스템 |
| 고객 (B2B) | 구매/엔지니어링 담당자 연락처, 주문 사양, 결제 정보 | CRM(Salesforce), ERP(SAP/Oracle) |
| 공급망/벤더 | 연락처, 계약 서류, 금융 정보, 배송 주소 | ERP, WMS, 벤더 포털 |
| 생산/IoT | 작업자 ID + 센서 데이터(위치/시간), 품질 검사 기록 | MES, PLC/SCADA, IoT 센서 |
| 기타 | IP/device ID, inferred data(생산 효율 분석) | 웹/포털, Analytics |

글로벌 공급망으로 인해 EU 데이터(수출/고객) 및 CA 주민 데이터가 혼재될 수 있어 GDPR + CCPA/CPRA를 동시 고려해야 합니다.

---

## 1. GDPR & CCPA 정책 수립

### 1.1 시스템 구조 파악 (1-2주)

**크로스-펑셔널 팀 구성:** IT/OT, HR, 공급망, 법무, 생산팀 참여.

**자산 인벤토리 항목:**

| 카테고리 | 시스템 예시 |
|---------|------------|
| IT 시스템 | ERP(SAP/Oracle), CRM(Salesforce), HRIS(Workday), WMS(물류) |
| OT/생산 | MES, PLC/SCADA, IoT 센서(온도/진동/작업자 트래킹), CCTV |
| 타사 서비스 | 클라우드(AWS/Azure), 물류 파트너(FedEx/UPS API), 벤더 포털, Analytics(Google Analytics) |
| 오프라인 | 종이 문서, USB, 이메일 첨부 |

**도구:** Excel/Google Sheets + Visio/draw.io로 시스템 다이어그램 작성.
**참고 표준:** NIST, IEC 62443.

### 1.2 PII 정의 및 분류 (1주)

| 규제 | 정의 |
|------|------|
| **GDPR** | "identified or identifiable natural person"에 관한 모든 정보. Special Category(건강, 인종, 노동조합 등) 별도 보호. |
| **CCPA/CPRA** | "Personal Information" — 소비자/가구와 직·간접 연관된 정보(11개 카테고리). Sensitive PI(SSN, geolocation, health, biometrics 등) 별도 보호. Household data 포함. |

**분류 매트릭스:**

| Tier | 유형 | 예시 | 보호 수준 |
|------|------|------|----------|
| Tier 1 | Direct Identifiers | 이름, SSN, 이메일 | 최고 |
| Tier 2 | Quasi-identifiers | IP, Employee ID | 높음 |
| Sensitive | 특수 범주 | Biometric, Health, Precise Geolocation | 최고 + 별도 동의 |

**Data Minimization 원칙:** 불필요한 데이터는 즉시 삭제 또는 익명화.

### 1.3 데이터 흐름 매핑 / RoPA (2-4주)

GDPR Article 30 Record of Processing Activities(RoPA)와 CCPA 데이터 인벤토리의 핵심.

**RoPA 템플릿 컬럼:**

| 항목 | 설명 |
|------|------|
| Processing Activity | 처리 활동명 (예: "Employee Time Tracking via IoT") |
| Data Subjects | 데이터 주체 (Employees, Contractors) |
| Categories of Personal Data | 데이터 유형 (Name, Employee ID, Timestamp, Location) |
| Purposes | 처리 목적 (Payroll, Safety Compliance) |
| Lawful Basis | GDPR: Contract / Legitimate Interest / Consent; CCPA: Business Purpose |
| Sources | 수집 경로 (HR System, Badge Reader, Sensors) |
| Storage | 저장 위치 (On-prem Server / AWS us-east-1) |
| Retention | 보유 기간 (Payroll 7년, Sensor logs 90일) |
| Recipients | 수신자 (Internal HR, Payroll Processor, Insurance) |
| Transfers | 국제 전송 (EU-US: SCC + DPF) |
| Security Measures | 암호화(at-rest/transit), RBAC, MFA, Audit Logs |
| Risks & Mitigation | DPIA 필요 여부 |

**제조업 구체적 데이터 흐름 예시:**

```
공급망: Vendor → ERP → Logistics Partner (국제 전송)
생산: IoT Sensor → MES → Cloud Analytics (OT-IT Convergence)
HR: Onboarding → HRIS → Payroll (Sensitive Data)
B2B: Customer Order → CRM/ERP → Fulfillment
```

**방법론:** 부서별 인터뷰 → 시각적 다이어그램(draw.io) → 자동화 툴 도입 검토(OneTrust, DataGrail). 매년 또는 시스템 변경 시 검토.

### 1.4 정책 문서화 (2-4주)

**필수 문서 목록:**

| 문서 | 설명 |
|------|------|
| Privacy Policy / Notice | 웹사이트 게시용 통합 정책 (GDPR + CCPA) |
| Notice at Collection | 데이터 수집 시점 고지 (웹폼, 온보딩) |
| Data Processing Agreement (DPA) | 모든 Processor/Vendor와 체결 |
| Records of Processing Activities (RoPA) | 모든 처리 활동 기록 |
| Data Subject Rights Procedure (DSAR) | Access, Deletion, Opt-out, Portability 처리 절차 |
| Breach Response Plan | GDPR 72시간, CCPA 신속 통지 |
| DPIA/PIA Template | 고위험 처리 시 영향 평가 |
| Vendor/Supply Chain Assessment | 공급망 벤더 평가 |
| Employee Training Policy | 연간 개인정보보호 교육 |

**Privacy Policy 구조 (15-25페이지):**

1. Introduction & Controller Info: 회사명, 주소, DPO/Privacy Contact
2. Personal Information Collected: CCPA 카테고리 테이블 + GDPR 설명
3. Sources & Purposes: 수집 경로 및 처리 목적
4. Sharing/Selling: "We do not sell" 명시, Service Providers only
5. International Transfers: SCC/DPF 설명
6. Retention Periods: Category별 보유 기간
7. Your Rights: Access, Delete, Opt-out, Correct 등 및 신청 방법(email, web form)
8. Security Measures: Encryption, audits
9. Updates & Contact

**CCPA 카테고리 테이블 예시:**

| Category | Collected | Purpose | Disclosed | Sold |
|----------|-----------|---------|-----------|------|
| Identifiers | Yes | Order fulfillment, Security | Service Providers (Logistics) | No |
| Sensitive PI | Yes (Biometric) | Factory access control | No | No |
| Commercial Info | Yes | Order processing | Service Providers | No |

### 1.5 법적 근거 및 특화 영역

- **GDPR Lawful Basis:** Contract(주문/고용 시 가장 일반적), Legitimate Interest(analytics), Consent(biometric), Legal Obligation.
- **IoT/OT:** Sensor data pseudonymization 우선, 불필요 시 anonymization.
- **HR:** Biometric/건강 기록 별도 보호, 명시적 동의.
- **공급망:** Vendor 데이터 공유 제한, DPA 필수.
- **Cross-border:** EU-US Data Privacy Framework(DPF) 또는 SCC + TIA.

### 1.6 구현 타임라인

| 기간 | 활동 |
|------|------|
| Week 1-4 | Applicability Assessment + Gap Analysis + Data Inventory |
| Week 5-8 | Full Data Mapping & RoPA 구축 |
| Week 9-12 | Policy Draft + Stakeholder Review |
| Month 4 | Training + Notice Deployment (웹사이트, 온보딩) |
| Ongoing | Annual Review (Q4 IT Audit 연계) |

---

## 2. Annual IT Audit 정책 수립

### 2.1 개요

**정책 문서:** "Annual IT & OT Security and Privacy Audit Policy" (10-15페이지)

**목적:** GDPR/CCPA 준수 증명, 위험 식별, 통제 효과성 검증, 지속 개선.

**Scope:** 모든 IT/OT 시스템, 데이터 흐름, PII 처리, Vendor/TPRM.

### 2.2 Audit Program (연간 체크리스트)

| 영역 | 점검 항목 |
|------|----------|
| **Governance** | Policies 최신 상태? Roles & Responsibilities 명확? |
| **Data Inventory & RoPA** | RoPA가 실제 데이터 흐름과 일치? 모든 PII 자산 식별? |
| **Access Management** | RBAC/MFA 100% 적용? Privileged access quarterly review? |
| **Data Protection** | Encryption(at-rest/transit) 적용? DLP 솔루션 운영? Retention 자동 삭제? |
| **Vulnerability Management** | 월간 스캔 수행? Critical patch SLA(48시간) 준수? |
| **Incident & Breach** | Table-top exercise 연 1회? GDPR 72시간 / CCPA 신속 통지 테스트? |
| **Privacy Controls** | DSAR 처리 정확성/적시성(샘플 10건)? Consent 기록 유지? |
| **OT/IoT Specific** | 네트워크 segmentation? Device inventory 최신? Firmware 업데이트? |
| **Vendor/TPRM** | High-risk vendor sample audit? DPA 준수 확인? |
| **Logging & Monitoring** | Audit trail immutable? SIEM alerting 정상? |

### 2.3 실행 방법론

| 단계 | 내용 |
|------|------|
| **Planning** | 1개월 전 Scope 확정, 팀 구성 (CISO + Privacy Officer 주도) |
| **Fieldwork** | 2-4주 (remote + on-site factory), Document Review + Interviews + Technical Testing |
| **Reporting** | Executive Summary + Detailed Findings (Risk Rating: Critical/High/Medium/Low) + CAP Template |
| **Follow-up** | 90일 내 Remediation Review, High risk 30일 이내 해결 |

### 2.4 조직 및 산출물

**책임자:** CISO 주도, Audit Committee/Board 보고.

**참여 부서:** IT, OT, HR, Legal, Business Units. 독립 검토자: Internal Audit 또는 External Auditor.

**산출물 템플릿:**
- Audit Checklist (Excel, Evidence 컬럼 포함)
- Findings Report Template (Issue | Evidence | Risk | Recommendation | Owner | Due Date)
- CAP Tracker (Corrective Action Plan)

### 2.5 연계

Audit 결과 → Privacy Policy / RoPA / TPRM 업데이트 (30일 이내). 연간 사이클: Q4 Full Audit → Q1 정책 업데이트.

---

## 3. TPRM 정책 수립

### 3.1 개요

**정책 문서:** "Third-Party Risk Management (TPRM) Policy" (15-20페이지) + Vendor Playbook

**목적:** Trusted Software Developer Partners 선정·관리, 데이터 보호 의무 이행(DPA 체결, Audit Right), 공급망 리스크 최소화.

**Scope:** 모든 Vendor. 특히 Software Developers(onshore/offshore, SaaS, custom development). High-risk: PII 접근, OT/IT integration, cloud hosting.

### 3.2 Vendor Lifecycle

#### A. Selection & Due Diligence

**Trusted Partner 기준:**
- ISO 27001, SOC 2 Type II, GDPR/CCPA 인증 또는 equivalent
- Privacy & Security Program 증빙 (DPO 임명, Breach Notification SLA ≤ 48시간)
- 제조업 경험 (OT/IoT 보안, IEC 62443)
- Financial stability + Cyber Liability Insurance

**Due Diligence Checklist:**
- Questionnaire: Data 처리 범위, Sub-processor 목록, Breach 이력
- Technical Review: Code security practices(SAST/DAST), Encryption, Access controls
- Legal Review: DPA readiness, Governing Law (US + EU)
- Risk Scoring (0-100): PII exposure(40%), Security maturity(30%), Financial(10%), Reputation(20%)

#### B. Contracting

**DPA 필수 조항:**
- Processing only on documented instructions (GDPR Art. 28)
- CCPA: "Service Provider"로서 Sell/Share 금지, Limited Use
- Audit Rights: Annual + For-Cause (회사 또는 대리인)
- Sub-processor: 사전 서면 승인 + 동일 수준 보호
- Breach Notification: 24-48시간 이내
- Data Return/Deletion: 계약 종료 시 30일 내 삭제 증적
- Liability & Indemnification: Breach로 인한 벌금 보상
- International Transfers: SCC/DPF 적용
- Insurance: Cyber Liability 최소 $5M

**Software Developer 특화:**
- Secure SDLC 요구 (OWASP, Privacy by Design)
- Code ownership, IP 보호, Backdoor 금지
- Access Logging (developer access to PII)

#### C. Ongoing Monitoring

| Tier | 대상 | 모니터링 주기 |
|------|------|-------------|
| Tier 1 (High-risk) | PII/OT 접근 Software Partners | Quarterly Security Reports + Annual On-site/Remote Audit + Continuous Monitoring |
| Tier 2 (Medium) | 일반 Vendor | Biannual + Continuous Monitoring (security scorecard) |

**KPI:** Uptime ≥99.9%, Incident resolution <4시간, Zero unauthorized PII access.

**Software Developer 전용:**
- Code Review / Penetration Testing 결과 공유
- Access Logging (developer access to PII)
- Change Management 시 Privacy Impact Assessment(PIA)
- Code escrow (critical systems)

#### D. Offboarding

- Access Revocation (all accounts, API keys, shared repos)
- Data Deletion Certificate 수취
- Post-termination Audit (6개월 이내)

### 3.3 조직 및 거버넌스

- **책임자:** CISO/Privacy Officer + Procurement + Legal
- **TPRM Committee:** Quarterly Meeting — High-risk Vendor Review
- **도구:** GRC Platform (OneTrust, BitSight, ServiceNow GRC)
- **교육:** Vendor-facing 팀(Procurement, IT) 대상 연 1회

### 3.4 구현 타임라인

| 기간 | 활동 |
|------|------|
| Month 1 | 기존 Vendor Inventory + Risk Tiering (Software Partners 우선) |
| Month 2 | Standardize Questionnaire & DPA Template |
| Month 3-4 | High-risk Contracts Renegotiation |
| Month 5+ | Monitoring Process Rollout + IT Audit 연계 |
| Annual | Full TPRM Effectiveness Review |

---

## 4. 통합 운영 및 유지보수

### 4.1 거버넌스 체계

- **Privacy Committee:** DPO/CISO/Legal 주도, Quarterly Meeting
- **연계 매트릭스:** Privacy Policy ↔ Audit Findings ↔ TPRM Contracts
- **문서 관리:** Central Repository(SharePoint/GRC), Retention 7년
- **Escalation:** Material findings → Executive Leadership 7일 이내 보고

### 4.2 연간 사이클

| 분기 | 활동 |
|------|------|
| Q1 | Privacy Training + 정책 검토 |
| Q2-Q3 | Monitoring & Evidence Collection |
| Q4 | Integrated Audit (IT/OT + Privacy + TPRM) |
| Post-Audit | Remediation tracking → 정책 업데이트 |

### 4.3 전체 구현 타임라인 (6-9개월)

| 기간 | 활동 |
|------|------|
| Month 1-2 | Assessment & Drafts (Gap Analysis, 정책 초안) |
| Month 3-5 | Data Mapping, Contracts Renegotiation, First Audit |
| Month 6+ | Rollout, Training, Monitoring, Annual Cycle 진입 |

### 4.4 핵심 지표 (KPI)

- RoPA coverage: 목표 100%
- Audit findings closure rate: 목표 90일 내 95%+
- Vendor compliance score: Tier 1 평균 80+/100
- DSAR 응답 시간: GDPR 30일 / CCPA 45일 준수율 100%

---

## 5. GitHub Repository 전략

### 5.1 목적

이력서에 언급된 GDPR/CCPA, IT Audit, TPRM 경험을 **공개적으로 검증 가능한 형태**로 제공. Recruiters/Hiring managers가 실제 정책·템플릿·방법론을 확인할 수 있도록 합니다.

**Repo:** `scale600/it-compliance-framework`

### 5.2 Repository 구조

```
it-compliance-framework/
├── README.md                       # 메인 랜딩 페이지
├── LICENSE                         # MIT or CC-BY
├── gdpr-ccpa/
│   ├── policy-template.md          # Full Policy Template
│   ├── ropa-template.md            # RoPA 컬럼 설명 및 예시
│   ├── data-mapping-example.md     # 제조업 데이터 흐름 다이어그램 (Mermaid)
│   ├── privacy-notice.md           # 웹사이트 게시용 Privacy Notice
│   ├── dpa-template.md             # 표준 Data Processing Agreement
│   └── dsar-procedure.md           # Data Subject Access Request 절차
├── it-audit/
│   ├── annual-audit-program.md     # Audit Program 상세
│   ├── audit-checklist.md          # 영역별 체크리스트
│   ├── audit-report-template.md    # Findings Report 양식
│   ├── cap-tracker.md              # Corrective Action Plan Tracker
│   └── ot-iec62443-notes.md        # OT/IoT 환경 감사 노트
├── tprm/
│   ├── tprm-framework.md           # Vendor Lifecycle 4단계 상세
│   ├── vendor-tiering-matrix.md    # Risk Tier 기준 및 평가표
│   ├── due-diligence-questionnaire.md  # Vendor 평가 질문지 (20+ 항목)
│   ├── standard-dpa-template.md    # TPRM 특화 DPA
│   └── software-developer-checklist.md # Secure SDLC, Code Review 체크리스트
├── evidence/                       # Anonymized artifacts (필수)
│   ├── bose-tprm-summary.md        # Bose TPRM 사례 (익명화)
│   ├── compliance-dashboard.md     # 컴플라이언스 대시보드 예시
│   └── audit-findings-example.md   # Audit Findings 샘플
├── resources/
│   ├── glossary.md                 # 용어 정의
│   └── references.md               # 참고 표준 및 자료
└── docs/
    ├── overview.md                 # 전체 프레임워크 개요
    └── manufacturing-use-cases.md  # 제조업 특화 사례
```

### 5.3 README.md 핵심 구성

```markdown
# IT Compliance Framework — Manufacturing

**Wonhee Richard Lee** | Senior Cloud Systems Administrator

Sena Technologies에서 구축한 GDPR/CCPA Compliance, Annual IT & OT Audit,
TPRM(Third-Party Risk Management) 프레임워크를 공개적으로 문서화한 Repository입니다.

### Key Achievements
- **GDPR/CCPA Framework**: IPO 준비 과정에서 전체 컴플라이언스 아키텍처 설계 및 구현
- **Annual IT Audit**: IT/OT 통합 감사 프로그램 설계 및 운영
- **TPRM**: Bose Project에서 Vendor Security Assessment 주도 → "Trusted Developer" 획득

### Repository Sections
- [GDPR & CCPA](./gdpr-ccpa/) — 정책, RoPA, Data Mapping, DPA
- [Annual IT Audit](./it-audit/) — Checklist, Report Template, OT Security
- [TPRM](./tprm/) — Vendor Lifecycle, Software Developer Partners 특화

### Manufacturing Focus Areas
- IoT / OT Environment Privacy & Security
- Global Supply Chain Data Flow
- Zero-Trust + Intune + Okta Integration
- Cloud Cost Optimization while maintaining Compliance

**Live Portfolio**: [project.techcloudup.com](https://project.techcloudup.com)
**Contact**: wonhee.eng@gmail.com
```

### 5.4 구현 시 주의사항

- **Anonymization 필수:** 회사명 → "Global Manufacturing Company", 수치/데이터는 fictionalize.
- **형식:** Markdown 테이블 및 Mermaid 다이어그램 적극 활용. Excel 대신 Markdown 테이블 사용.
- **GitHub Pages 활성화:** `https://scale600.github.io/it-compliance-framework` 로 웹사이트화.
- **Resume 연계:** "Detailed IT Compliance frameworks publicly documented at: github.com/scale600/it-compliance-framework" 문구 추가.
- **LinkedIn/GitHub Profile에 해당 Repo Pin.**

### 5.5 Evidence 폴더 중요성

`evidence/` 폴더는 이 Repository의 신뢰도를 결정하는 가장 중요한 섹션입니다. 템플릿만으로는 누구나 다운로드 가능한 ICO/IAPP 자료와 차별화되지 않습니다. 최소한 아래 중 하나 이상 포함:

- 실제 Audit Findings 예시 (익명화된)
- Compliance Dashboard 구성 예시
- Bose TPRM 프로젝트 요약 (성과 중심, 기밀 정보 제외)
- 구현 전/후 비교 데이터

---

## 부록: 주요 참고 표준 및 도구

| 분야 | 표준/도구 |
|------|----------|
| 개인정보보호 | GDPR, CCPA/CPRA |
| 정보보안 | ISO 27001, NIST SP 800-53, SOC 2 Type II |
| OT/IoT 보안 | IEC 62443 |
| Data Mapping | Excel, OneTrust, DataGrail |
| GRC | OneTrust, ServiceNow GRC, RSA Archer |
| Vendor Risk | BitSight, Security Scorecard |
