# HIPAA Technical Safeguards  
**Identity · Device Security · Logging · Data Protection**

HIPAA’s technical safeguards define the measurable, enforceable controls a system must implement to protect PHI. This document outlines how these requirements are satisfied using Microsoft cloud technologies.

---

## 1. Access Control (45 CFR §164.312(a))

### Identity Authentication & MFA  
- Entra ID authenticates all users with MFA  
- Conditional Access controls enforce compliant devices  
- Legacy authentication blocked  

### Role-Based Access  
- RBAC restricts PHI access to authorized job functions  
- Break-glass accounts isolated and monitored  

### Automatic Session Controls  
- Sign-in frequency  
- Token lifetimes  
- Conditional Access session restrictions  

---

## 2. Audit Control (45 CFR §164.312(b))

### Logging  
All identity, device, and email activity is logged via:

- Unified Audit Log  
- Defender telemetry  
- Sign-in logs  
- Intune device compliance reports  

### Centralization  
Logs are consolidated into a **Log Analytics Workspace**, enabling:

- Review  
- Alerting  
- Retention  
- Export for audits  

---

## 3. Integrity (45 CFR §164.312(c))

### Device Integrity Protection  
- Secure Boot  
- TPM-backed BitLocker  
- ASR rules preventing tampering  
- Real-time Defender protection  
- Automatic remediation  

### Data Integrity  
- Safe Attachments scans files for malicious manipulation  
- SharePoint/OneDrive versioning supports recovery  

---

## 4. Person or Entity Authentication (45 CFR §164.312(d))

Entra ID enforces:

- MFA for all users  
- Conditional Access based on risk and compliance  
- Passwordless methods (planned)  
- Identity Protection for risky behaviors  

---

## 5. Transmission Security (45 CFR §164.312(e))

### Encryption in Transit  
- TLS 1.2+ required across all M365 workloads  
- SMTP AUTH disabled  
- Safe Links rewrites malicious URLs  

### VPN Connectivity  
- Site-to-site VPN tunnels secured between locations  
- Meraki MX as the encrypted routing boundary  

---

## 6. Device Security

### Windows 11 Compliance  
- Encryption (BitLocker + TPM)  
- Secure Boot  
- OS version enforcement  
- No local admin for users  
- Managed through Intune baselines  

### Endpoint Hardening  
- ASR rules  
- Exploit Protection  
- Credential Guard and LSA protection  

---

## 7. Data Loss Prevention (Purview)

Purview DLP enforces:

- PHI-sensitive content scanning  
- Restriction or auditing of file transfers  
- Email monitoring for PHI keywords  
- Alerts for policy violations  

Supports HIPAA’s “minimum necessary” principle.

---

## 8. Incident Response Support

- Alerts received through Defender  
- Device isolation option  
- Automated investigation  
- Timeline + forensics capabilities  

While not a full SOC, the environment is SIEM-ready.

---

## 9. Document Intent

This document outlines the **specific technical controls** that enforce HIPAA compliance across identity, device, network, and data layers.

The next document provides a formal control mapping.
