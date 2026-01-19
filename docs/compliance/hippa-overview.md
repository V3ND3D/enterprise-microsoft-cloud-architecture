# HIPAA Compliance Overview  
**Administrative · Physical · Technical Safeguards**

This document summarizes how a modern Microsoft cloud environment aligns with HIPAA’s required safeguards. It provides a practical, implementation-focused overview designed for IT auditors, security teams, and technical stakeholders.

HIPAA sets the legal framework for protecting Protected Health Information (PHI). In a cloud-managed environment, compliance is achieved by combining identity controls, encryption, device governance, audit logging, and operational processes.

---

## 1. HIPAA Safeguard Categories

HIPAA defines three core safeguard groups:

### Administrative Safeguards  
Policies, procedures, and role-based controls that govern how PHI is accessed and managed.

### Physical Safeguards  
Protection of physical devices, office spaces, and infrastructure where PHI is created, stored, or transmitted.

### Technical Safeguards  
Controls implemented directly through technology—identity, authentication, encryption, access control, audit logging, and data protection.

This repository focuses on the *technical* and *administrative* safeguards implemented through Microsoft 365, Entra ID, Intune, Defender, and Azure governance.

---

## 2. Key Compliance Objectives in Cloud Environments

A HIPAA-aligned Microsoft environment must ensure:

- Only authorized, authenticated users access PHI  
- Devices with PHI are encrypted and compliant  
- Access is logged, monitored, and traceable  
- PHI is not exposed through email, cloud apps, or unmanaged endpoints  
- Administrative privilege is minimized  
- Policies are enforced consistently across the tenant  
- Violations are detectable and containable  

These objectives are met through a combination of Conditional Access, device compliance enforcement, Defender threat protection, Purview DLP, and audit logging.

---

## 3. Core Microsoft Capabilities Supporting HIPAA

### Identity & Access: Entra ID  
- MFA  
- Conditional Access  
- Role-based access control  
- Identity Protection risk policies  
- Access reviews  

### Endpoint Protection: Intune + Defender  
- BitLocker with TPM  
- Secure Boot  
- OS compliance  
- ASR rules  
- Vulnerability monitoring  
- Device isolation  

### Data Protection: Purview  
- Data Loss Prevention (DLP) policies  
- Content scanning for PHI identifiers  
- Activity monitoring (email, SharePoint, OneDrive, Teams)  

### Logging & Audit: Azure + M365  
- Log Analytics Workspace  
- Unified audit log  
- Sign-in telemetry  
- Defender incident visibility  

---

## 4. Operational Compliance Practices

To maintain audit readiness:

- Policies and configurations are version-controlled  
- Administrative actions are logged  
- Conditional Access policies enforce organizational rules  
- Non-compliant devices are automatically blocked from PHI  
- Email protections (DKIM, SPF, DMARC, Safe Links, Safe Attachments) reduce exposure  
- Access reviews validate least-privilege over time  

---

## 5. Document Intent

This overview establishes the foundation for how HIPAA intersects with cloud architecture.  
Detailed mappings and technical safeguards appear in the accompanying documents:

- **technical-safeguards.md**  
- **control-mapping.md**
