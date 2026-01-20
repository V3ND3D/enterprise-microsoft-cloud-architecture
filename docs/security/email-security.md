# Email Security Architecture  
**Defender for Office 365 · Anti-Phishing · Safe Links · Safe Attachments · Authentication Controls**

Email is the highest-risk communication channel in any organization and represents the majority of phishing, credential theft, and malware delivery attempts.  
This document summarizes the email security architecture built using Microsoft Defender for Office 365 and supporting Microsoft 365 controls.

The goal of this architecture is to ensure that email threats are detected, blocked, or contained before reaching end users.

---

## 1. Email Threat Protection Overview

Microsoft Defender for Office 365 provides layered protection against:

- Phishing  
- Impersonation attacks  
- Malware attachments  
- Malicious URLs  
- Business email compromise (BEC)  
- Account takeover attempts  

This protection integrates into:

- Exchange Online  
- Teams  
- SharePoint  
- OneDrive  
- Identity Protection  
- Defender for Endpoint  

Email security feeds into the overall Zero Trust and device compliance model.

---

## 2. Authentication & Domain Protection

### 2.1 SPF  
Sender Policy Framework (SPF) prevents unauthorized mail servers from sending email on behalf of the organization.

### 2.2 DKIM  
DomainKeys Identified Mail cryptographically signs messages to prevent tampering and spoofing.

### 2.3 DMARC  
Domain-based Message Authentication Reporting and Conformance enforces alignment between SPF/DKIM and defines:

- Reject  
- Quarantine  
- None  

policies for unauthenticated mail.

### 2.4 SMTP AUTH Disabled  
Prevents legacy, insecure authentication methods used by botnets and malware.

Domain protections reduce impersonation, spoofing, and unauthorized relay attempts.

---

## 3. Anti-Phishing Architecture

### 3.1 User & Domain Impersonation Protection  
Rules detect:

- Similar-looking domains  
- Name-based impersonation  
- Internal spoofing attempts  

### 3.2 Machine Learning Models  
Microsoft’s ML-based filter evaluates:

- Writing style consistency  
- Anomalous sending patterns  
- Risky authentication behavior  

### 3.3 Enhanced Phishing Threshold  
Advanced settings provide higher sensitivity for high-value targets.

---

## 4. Safe Links Architecture

Safe Links provides URL rewriting and real-time detonation.

### Capabilities:
- Time-of-click scanning  
- URL rewriting in emails and Teams  
- Blocking malicious or suspicious destinations  
- Sandboxing for unknown links  

This reduces credential theft attempts and drive-by malware infections.

---

## 5. Safe Attachments Architecture

Safe Attachments isolates and detonates email attachments in a secure container.

### Features:
- Dynamic analysis  
- Malware detection using behavior models  
- Quarantine of suspicious files  
- Policy-based allow/block actions  

This prevents ransomware and zero-day malware from entering user inboxes.

---

## 6. Zero-Hour Auto Purge (ZAP)

ZAP automatically removes previously delivered malicious emails if threats are discovered after delivery.

### ZAP handles:
- Malware  
- Phishing  
- Spam  
- Time-of-click discovered threats  

This significantly reduces dwell time and exposure risk.

---

## 7. Policy Governance & Configuration

### 7.1 Baseline Email Security Policies  
Policies include:

- Anti-phishing  
- Anti-spam  
- Anti-malware  
- Safe Links  
- Safe Attachments  

### 7.2 Role-Based Access  
Email security is managed through:

- Security Administrator  
- Exchange Administrator  

Global admin is not required for ongoing governance.

### 7.3 Logging & Visibility  
Key telemetry includes:

- Threat Explorer  
- Quarantine insights  
- Mail flow reports  
- Alert policies  

These logs feed into audit, governance, and potential SIEM workflows.

---

## 8. Email Security Outcomes

- Strong protection against phishing and malware  
- Authentication enforcement against spoofing  
- Optimized Safe Links and Safe Attachments coverage  
- Reduction in malicious deliveries via ZAP  
- High alignment with HIPAA transmission security requirements  
- Improved Secure Score for mail-based controls  

---

## 9. Document Intent

This document supplements `security-overview.md` by providing a focused, operationally accurate description of the email security layer.  
It demonstrates capability in threat prevention, M365 configuration, and modern secure email design.
