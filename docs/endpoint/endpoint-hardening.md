# Endpoint Hardening & Protection Controls  
**ASR · Exploit Protection · Credential Guard · Local Admin Governance · Device Risk Reduction**

This document details the technical hardening controls applied to all corporate endpoints.  
These measures reduce attack surface, prevent exploitation, and integrate tightly with Defender for Endpoint.

---

## 1. Attack Surface Reduction (ASR)

ASR rules deployed in **block mode** include:
- Block Office macros and executable content  
- Block credential theft techniques  
- Block untrusted and unsigned scripts  
- Block executable files from email and web downloads  
- Block persistence mechanisms  

ASR provides strong ransomware and initial-access prevention.

---

## 2. Exploit Protection

Exploit mitigations applied via Intune include:
- Data Execution Prevention (DEP)  
- Address Space Layout Randomization (ASLR)  
- Control Flow Guard  
- Arbitrary code guard protections  
- Memory corruption mitigations  

These policies ensure modern exploit chains are significantly limited.

---

## 3. Credential Protection

### 3.1 LSA Protection  
Local Security Authority protection is enforced to prevent credential extraction.

### 3.2 Credential Guard  
Enabled via Intune to secure NTLM/Kerberos secrets and block credential replay attacks.

### 3.3 Remote Credential Guard  
Reduces risk during RDP usage by avoiding credential delegation.

---

## 4. Local Administrator Governance

### 4.1 No Local Admin for Users  
All end-users operate without local admin rights.

### 4.2 LAPS Enforcement  
Local administrator password rotation is:
- Automated  
- Unique per machine  
- Stored securely in Entra ID  

### 4.3 Admin Elevation Controls  
Administrative elevation is reserved for:
- IT personnel  
- Documented workflows  
- Temporary access only  

---

## 5. Device Configuration Hardening

Additional configuration controls include:
- Blocked removable media (policy-dependent)  
- Controlled Folder Access (where compatible)  
- SmartScreen + Defender reputation services enforced  
- Browser isolation and security policies  
- Restriction of unsigned and legacy executables  

These settings significantly reduce exposure to common malware vectors.

---

## 6. Threat & Vulnerability Management (TVM)

Defender for Endpoint provides:
- Device exposure score  
- Vulnerability catalogues  
- Weak configuration detection  
- Prioritized remediation recommendations  
- Software inventory visibility  

TVM is integrated into ongoing security operations.

---

## 7. Hardening Outcomes

- Strong mitigation of ransomware and phishing payloads  
- Reduction of credential theft and lateral movement  
- Standardized enforcement of enterprise controls  
- Clear administrative governance  
- High device security posture validated through compliance and TVM  

---

## 8. Document Intent

This document outlines the hardening approach that supports Zero Trust endpoint requirements.  
It complements the broader endpoint architecture and security documentation within this repository.
