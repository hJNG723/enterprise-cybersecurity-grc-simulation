# INFORMATION SECURITY POLICY: ACCESS CONTROL & MULTI-FACTOR AUTHENTICATION (MFA)

**Document ID:** `POL-SEC-001`  
**Version:** 1.0  
**Effective Date:** November 2026  
**Owner:** Information Security & GRC Team  
**Review Cycle:** Annual  
**Framework Alignment:** ISO/IEC 27001:2022 (`A.5.15`, `A.5.16`, `A.5.18`, `A.8.5`, `A.8.20`) | NIST CSF 2.0 (`PR.AA-01`, `PR.AA-03`, `PR.AA-05`)  
**Linked Risk Register Entries:** `RSK-2026-001`, `RSK-2026-002`  

---

## 1. Purpose
This policy establishes mandatory requirements for managing user identities, enforcing Multi-Factor Authentication (MFA), governing privileged access, and restricting network-level access across all organizational systems. Its primary objective is to prevent unauthorized access, privilege creep, and lateral movement resulting from compromised credentials or overly permissive network rules.

## 2. Scope
This policy applies to:
* All employees, contractors, interns, and third-party vendors accessing company-managed systems, cloud environments, corporate Identity Providers (IdP), databases, and network infrastructure.
* All production, staging, and corporate IT assets, including edge firewalls, routers, servers, and SaaS applications.

---

## 3. Policy Statements

### 3.1 Identity Lifecycle & Provisioning (`RSK-2026-002`)
* **Unique Identification:** Every user must be assigned a unique user ID. Shared, generic, or group accounts are strictly prohibited across all operating systems, databases, and cloud consoles.
* **Automated Provisioning & Deprovisioning:** User account creation, role modifications, and terminations must be synchronized via automated System for Cross-domain Identity Management (SCIM) integration between the Human Resources Information System (HRIS) and the corporate Identity Provider (IdP).
* **Termination SLA:** Upon employee or contractor offboarding, all corporate IdP, VPN, and system access must be revoked automatically within **1 hour** of HRIS status change (and immediately for involuntary terminations). Manual monthly cross-checks alone are insufficient.

### 3.2 Principle of Least Privilege & Access Reviews (`RSK-2026-002`)
* **Role-Based Access Control (RBAC):** Access rights shall be granted strictly based on documented job roles and the Principle of Least Privilege. Default access to all sensitive systems is *Deny All*.
* **Privileged Access Separation:** Administrative personnel must maintain separate standard user accounts (for daily email/web tasks) and dedicated privileged accounts (for system or infrastructure administration).
* **Periodic Access Reviews:**
  * **Privileged / Administrative Accounts:** Reviewed **quarterly** by system owners and the GRC team.
  * **Standard User Accounts:** Reviewed **semi-annually** by department managers.

### 3.3 Multi-Factor Authentication (MFA) Requirements (`RSK-2026-002`)
* **Universal MFA Enforcement:** MFA is mandatory for all user logins to the corporate IdP, VPN, email, and cloud/SaaS applications.
* **Phishing-Resistant MFA for Privileged Access:** All administrative accounts accessing production servers, databases, cloud management consoles, or network security appliances must use hardware-backed, phishing-resistant MFA (**FIDO2 / WebAuthn** security keys). SMS-based or voice-call MFA is prohibited for privileged roles.
* **Session Timeouts:** Administrative console sessions must automatically lock or terminate after **15 minutes** of inactivity.

### 3.4 Network & Perimeter Access Control (`RSK-2026-001`)
* **Strict Port & Service Filtering:** All edge firewalls and internal network Access Control Lists (ACLs) must follow an explicit *Default-Deny* posture. Broad port ranges and legacy unencrypted management protocols (e.g., Telnet, HTTP, plain FTP) are prohibited.
* **Administrative Interface Isolation:** Management interfaces for firewalls, routers, and staging/production databases must never be exposed to the public internet. Access is permitted only via encrypted jump hosts or authenticated corporate VPNs.
* **Quarterly Firewall Rule Audits:** The Network Security team must review all firewall and ACL rule sets **quarterly** to identify and remove unused, shadow, or overly permissive rules.

---

## 4. Control & Risk Mapping Matrix

| Policy Section | Addressed Risk ID | ISO/IEC 27001:2022 Control | NIST CSF 2.0 Subcategory | Required Audit Evidence |
|---|---|---|---|---|
| **3.1 Identity Lifecycle** | `RSK-2026-002` | `A.5.16` (Identity management)<br>`A.5.18` (Access rights) | `PR.AA-01` (Identities & credentials managed) | HRIS-to-IdP SCIM sync logs; sample terminated user timestamps vs. IdP deactivation logs. |
| **3.2 Least Privilege** | `RSK-2026-002` | `A.5.15` (Access control)<br>`A.8.2` (Privileged access rights) | `PR.AA-05` (Access permissions & authorizations managed) | Signed quarterly privileged access review sign-off sheets; IAM role permission exports. |
| **3.3 MFA Enforcement** | `RSK-2026-002` | `A.8.5` (Secure authentication) | `PR.AA-03` (Users, services & hardware authenticated) | IdP Conditional Access policy configuration export requiring FIDO2/WebAuthn for admin groups. |
| **3.4 Network Access** | `RSK-2026-001` | `A.8.20` (Networks security)<br>`A.8.22` (Segregation of networks) | `PR.AA-05` (Network access restrictions enforced) | Quarterly firewall rule-base review report; exported edge ACL configurations showing Default-Deny. |

---

## 5. Exceptions & Compliance
* **Policy Exceptions:** Any temporary deviation from this policy requires a formal Risk Exception Request documenting compensating controls, business justification, and written approval from the CISO/GRC Lead. Exceptions expire after a maximum of **90 days**.
* **Enforcement:** Violations of this policy may result in revocation of system access and disciplinary action in accordance with HR policies.
