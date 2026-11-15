# Enterprise Cybersecurity Risk & Compliance Readiness Simulation

An end-to-end Governance, Risk, and Compliance (GRC) readiness package simulating **ISO/IEC 27001:2022** and **NIST CSF 2.0** alignment for a mid-sized cloud SaaS organization.

## Simulated Organization Scope
* **Company Profile:** NovaCloud Technologies (fictional B2B SaaS provider, ~60 employees) handling enterprise customer PII and payment workflows.
* **Infrastructure Scope:** AWS production/staging environments, corporate Identity Provider (IdP), perimeter edge firewalls/routers, and third-party SaaS sub-processors.
* **Objective:** Identify technical and supply-chain risks, quantify inherent vs. residual risk exposure, establish enforceable security policies, and define audit-ready verification evidence.

## Repository Structure
- **[01-Risk-Management](./01-Risk-Management):** 5×5 Cybersecurity Risk Register tracking 10 technical and supply-chain risks with automated inherent/residual scoring formulas, severity classifications, and NIST CSF 2.0 / ISO 27001 mappings.
- **[02-Governance-Policies](./02-Governance-Policies):** Enterprise Access Control & MFA Policy (`POL-SEC-001`) written to remediate high-priority perimeter and identity risks.
- **[03-Audit-and-Compliance](./03-Audit-and-Compliance):** Control-to-Evidence verification matrix mapping all 10 risks to required internal and external audit artifacts.
