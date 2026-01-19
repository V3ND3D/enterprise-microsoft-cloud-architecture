# Security Architecture Overview  
**Microsoft Defender · Threat Protection · Email Security · Exposure Reduction · Monitoring & Telemetry**

This document outlines the security architecture governing threat protection, endpoint hardening, email security, monitoring, and exposure reduction across the Microsoft cloud environment.  
Security controls are deeply integrated into identity, endpoint, and governance layers to support a Zero Trust operating model and regulatory requirements.

The foundation of this architecture is Microsoft Defender, which unifies threat detection, prevention, investigation, and response across all workloads.

---

## 1. Security Architecture Principles

### Zero Trust Enforcement  
Access is granted only when identity, device posture, and risk signals meet policy requirements.

### Defense-in-Depth  
Controls implemented at identity, endpoint, email, and cloud layers reduce attack surface and block lateral movement.

### Telemetry-Driven Security  
High-quality signals from Defender, Entra ID, Intune, and Azure provide full visibility and enable rapid response.

### Compliance Through Configuration  
Security controls are standardized via policy and enforced consistently across all devices and services.

---

## 2. Threat Protection Stack

### 2.1 Defender for Endpoint (EDR)
Core endpoint protection platform responsible for:
- Behavioral threat detection  
- Real-time monitoring  
- Automated investigation  
- Exposure score reduction  
- Endpoint vulnerability reporting  

Endpoints onboard automatically during Intune enrollment.

### 2.2 Attack Surface Reduction (ASR)
ASR rules enforced in block mode where compatible:
- Block executable content from email/Office  
- Block credential theft techniques  
- Block untrusted scripts  
- Block process injection  
- Prevent persistence methods  

ASR significantly reduces ransomware and malware risk.

### 2.3 Exploit Protection
Enterprise-wide exploit mitigations configured via Intune:
- DEP  
- ASLR  
- Control flow integrity  
- Memory corruption mitigations  

### 2.4 Antivirus & EDR Policies
- Cloud-delivered protection always enabled  
- Tamper protection locked on  
- Automatic sample submission enabled  
- Real-time scanning enforced  

### 2.5 Defender for Office 365 (Email Security)
Email threat protection includes:
- Safe Links  
- Safe Attachments  
- Anti-phishing policies with impersonation protection  
- SMTP auth disabled  
- Quarantine and ZAP (Zero-hour Auto Purge)  

Email represents 90+% of initial attack vectors; hardening the channel is critical.

### 2.6 Defender for Cloud (Baseline)
While cloud workload protection is not fully deployed, baseline controls include:
- Secure Score for Azure  
- Policy compliance evaluation  
- Resource posture metrics  
- CIS-aligned recommendations  

---

## 3. Endpoint Security Architecture

Endpoint security is tightly integrated with identity and compliance.

### 3.1 Posture Requirements  
Devices must meet:
- BitLocker encryption with TPM protector  
- Secure Boot enabled  
- Up-to-date OS version  
- Defender healthy & active  
- No unresolved high-severity threats  

### 3.2 Compliance Enforcement  
Noncompliant devices trigger:
- Restricted access via Conditional Access  
- User notifications  
- Required remediation before access restored  

### 3.3 Device Hardening  
Includes:
- Browser hardening  
- Restricting unsigned apps  
- USB & removable media restrictions where applicable  
- Credential protection (LSA, Credential Guard)  

### 3.4 Local Admin Governance  
- End-users are not local admins  
- LAPS enforced for local admin accounts  
- Admin elevation strictly controlled  

---

## 4. Email & Collaboration Security

### 4.1 Anti-Phishing Controls  
- User impersonation protection  
- Domain impersonation detection  
- Real-time scanning of inbound messages  

### 4.2 Safe Links  
URL rewriting and reputation analysis provide:
- Time-of-click evaluation  
- URL detonation  
- Blocking of malicious destinations  

### 4.3 Safe Attachments  
- Sandboxing of files  
- Malware detonation  
- Quarantine of suspicious payloads  

### 4.4 Authentication & Domain Protections  
- SPF configured  
- DKIM deployed  
- DMARC alignment evaluated  
- Tenant configuration aligns with Microsoft 365 security best practices  

Email security is critical for credential protection and ransomware prevention.

---

## 5. Identity-Integrated Security (Conditional Access)

Conditional Access reinforces security decisions based on identity + device health + risk.

### 5.1 Authentication Controls  
- MFA required for all accounts  
- Legacy auth blocked  
- Passwordless auth adoption planned  

### 5.2 Device-Based Access Enforcement  
- Only compliant devices may access corporate data  
- High-risk devices blocked until resolved  

### 5.3 Risk-Based Policies  
Powered by Entra ID Identity Protection:
- Risky sign-ins → MFA challenge or block  
- Risky users → password reset or block  
- Suspicious sessions → session control enforcement  

---

## 6. Threat Analytics & Exposure Reduction

### 6.1 Secure Score Governance  
Security posture improved from:
**46.15% → 93.88%**

Changes driving this improvement:
- Removal of McAfee conflicts  
- Standardized Defender policies  
- ASR rollout  
- Email threat protection enhancements  
- Compliance enforcement  
- Administrative privilege reductions  

### 6.2 Exposure Score  
Defender for Endpoint provides:
- Vulnerability visibility  
- Software inventory  
- Misconfiguration detection  
- Attack path insights  

### 6.3 Threat Analytics  
Reports used to identify:
- Active global threats  
- Exploited vulnerabilities  
- Recommended remediation steps  

---

## 7. Logging, Monitoring & Incident Response

### 7.1 Log Ingestion  
Log Analytics Workspace collects:
- Defender alerts  
- Identity risk events  
- Audit logs  
- Device compliance data  
- Sign-in telemetry  

### 7.2 Security Monitoring  
Monitoring performed through:
- Microsoft 365 Defender portal  
- Entra ID Identity Protection  
- Email threat dashboards  
- Compliance and Secure Score dashboards  

### 7.3 Incident Handling Workflow  
While a full SOC workflow is not yet deployed, current incident processes include:
- Alert triage via Defender portal  
- Investigation of device timelines  
- Evidence gathering via EDR  
- Remediation via Intune or user isolation  

### 7.4 SIEM-Ready Architecture  
Even without Sentinel deployed, the environment is prepared for:
- Centralized alert correlation  
- Automated playbooks  
- Analytics rule deployment  
- SOC integration  

---

## 8. Security Outcomes

- Secure Score increased from **46.15% → 93.88%**  
- Significantly reduced attack surface through ASR & exploit mitigations  
- Email threat protection fully hardened  
- Device compliance tightly enforced via conditional access  
- High-fidelity telemetry across identity, device, and cloud layers  
- Privilege minimization through RBAC and local admin governance  
- Consistent hardening of all endpoints and identity pathways  

---

## 9. Document Intent

This document establishes the current security architecture implemented across the Microsoft cloud environment.  
It acts as a reference for future enhancements, including SIEM integration, identity-driven session control, and advanced automation.

Security is treated as an integrated discipline — not a separate system — ensuring cohesive behavior across identity, endpoint, and cloud workloads.
