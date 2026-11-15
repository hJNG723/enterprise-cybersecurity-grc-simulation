# AUDIT READINESS & CONTROL EVIDENCE MATRIX (ISO/IEC 27001:2022 & NIST CSF 2.0)

**Document ID:** `AUD-MAT-001`  
**Version:** 1.0  
**Scope:** NovaCloud Technologies — Production SaaS & Corporate Infrastructure  
**Purpose:** Maps enterprise risks and governance controls to verifiable audit artifacts required for internal readiness reviews and external certification audits.

---

## Control Verification & Evidence Matrix

| Control Domain | Risk ID | ISO/IEC 27001:2022 | NIST CSF 2.0 | Control Objective & Requirement | Primary Audit Evidence (Artifacts) | Verification Frequency | Control Owner |
|---|---|---|---|---|---|---|---|
| **Network Security & Perimeter Filtering** | `RSK-2026-001` | `A.8.20` (Networks security)<br>`A.8.22` (Segregation of networks) | `PR.AA-05` | Edge firewalls and internal ACLs enforce a Default-Deny posture; insecure legacy ports are blocked and rules are reviewed periodically. | 1. Exported edge firewall & ACL configuration files.<br>2. Signed quarterly firewall rule-base audit checklist and change tickets. | Quarterly | Lead Network Security Engineer |
| **Identity Lifecycle & Access Governance** | `RSK-2026-002` | `A.5.15` (Access control)<br>`A.5.16` (Identity management)<br>`A.5.18` (Access rights) | `PR.AA-01`<br>`PR.AA-05` | User accounts are provisioned/deprovisioned automatically via HRIS-SCIM integration within 1 hour of termination; privileged access is reviewed quarterly. | 1. SCIM provisioning/deprovisioning system logs.<br>2. HR termination list cross-referenced against IdP account disable timestamps.<br>3. Quarterly privileged access review sign-off records. | Quarterly / Continuous | Head of IT Infrastructure |
| **Strong Authentication (MFA)** | `RSK-2026-002` | `A.8.5` (Secure authentication) | `PR.AA-03` | Phishing-resistant MFA (FIDO2/WebAuthn) is enforced for all administrative and privileged access across IdP, cloud consoles, and databases. | 1. JSON/screenshot export of IdP Conditional Access policies.<br>2. Sample authentication logs proving MFA challenge enforcement for admin roles. | Semi-Annual | Head of IT Infrastructure |
| **Third-Party & Supply Chain Risk (TPRM)** | `RSK-2026-003` | `A.5.19` (Information security in supplier relationships)<br>`A.5.21` (Managing ICT supply chain) | `GV.SC-06` | Critical SaaS sub-processors undergo security due diligence prior to onboarding and submit annual independent audit reports. | 1. Completed Vendor Security Assessment Questionnaires.<br>2. Current SOC 2 Type II or ISO 27001 certificates on file.<br>3. Executed Data Processing Agreements (DPAs) with 48h breach notification SLAs. | Annual / Onboarding | Vendor Management / GRC Lead |
| **Technical Vulnerability & Patch Management** | `RSK-2026-004` | `A.8.8` (Management of technical vulnerabilities) | `PR.PS-02` | Production Linux/Windows workloads are scanned weekly; Critical/High CVEs are remediated within defined SLAs (7 days Critical / 30 days High). | 1. Authenticated vulnerability scan reports (e.g., Nessus/Inspector).<br>2. Patch deployment logs and Jira remediation tickets showing SLA compliance. | Monthly | Cloud & Systems Engineering Lead |
| **Backup Integrity & Disaster Recovery** | `RSK-2026-005` | `A.8.13` (Information backup)<br>`A.5.30` (ICT readiness for business continuity) | `PR.IR-03` | Production backups are encrypted, immutable (Object Lock), stored cross-region, and tested via scheduled restoration drills. | 1. Cloud storage immutability/Object Lock configuration screenshots.<br>2. Automated daily backup job completion logs.<br>3. Semi-annual Disaster Recovery (DR) restoration test report. | Semi-Annual | Site Reliability Engineering (SRE) Lead |

---

## Audit Sampling Methodology (Readiness Guidelines)
* **Population vs. Sample Testing:** For continuous controls (e.g., offboarding revocations, patch tickets), auditors will request a full population list for the review period and select a random sample of **10–25 items** to trace end-to-end evidence.
* **Configuration Snapshots:** For preventative technical controls (e.g., MFA policies, firewall Default-Deny rules, S3 Object Lock), system-generated configuration exports with visible timestamps are required rather than manual assertions.
