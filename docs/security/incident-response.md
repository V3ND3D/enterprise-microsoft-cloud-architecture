# Incident Response Model  
**Lean Environment · Single Engineer · Defender-Centric Operations**

This document outlines the incident response (IR) model used in a lean IT environment where one engineer is responsible for all identity, endpoint, email, and security operations.

The purpose is to demonstrate clear, realistic, and technically sound IR processes that can function without a SOC or SIEM, while maintaining auditability and strong security posture.

---

## 1. Operating Context

The environment is maintained by a **single IT & Security operator**, functioning as:

- Head of IT  
- Network Administrator  
- Security Engineer  
- Incident Handler  

No SOC team exists, and Microsoft Sentinel is not yet deployed.  
All investigation, containment, and remediation is performed using Microsoft 365 Defender, Entra ID logs, and Intune governance.

Despite this constraint, the environment follows a structured, repeatable IR workflow.

---

## 2. Detection Model

Alerts originate from:

### 2.1 Microsoft Defender for Endpoint
- Malware detection  
- Behavioral anomalies  
- Credential theft attempts  
- Suspicious scripts or processes  
- Vulnerability exploitation signals  

### 2.2 Defender for Office 365
- Phishing attempts  
- Malicious attachments (Safe Attachments)  
- Malicious links (Safe Links)  
- Impersonation attempts  

### 2.3 Entra ID Identity Protection
- Risky user alerts  
- Risky sign-in attempts  
- Impossible travel  
- Authentication anomalies  

All alerts are triaged by a single engineer.

---

## 3. Lightweight Triage Workflow

A minimal but effective triage model ensures threats are handled consistently:

### Step 1 — Validate Alert
Check:
- Device timeline  
- Sign-in logs  
- Email trace (if relevant)  
- Defender threat details  

### Step 2 — Assess Severity
Classification:
- **High:** active compromise, confirmed malware, credential breach  
- **Medium:** phishing interaction, suspicious execution  
- **Low:** blocked activity, benign events  

### Step 3 — Determine Scope
Identify:
- Affected user(s)  
- Device(s)  
- Lateral movement potential  
- Related emails or sessions  

This scoping is done using Defender timelines, entity relationships, and Entra logs.

---

## 4. Containment Capabilities

Even without a SOC, the environment supports strong containment actions:

### 4.1 Device Containment  
- Isolate device from the network  
- Force security scans  
- Quarantine suspicious files  

### 4.2 Account Containment  
- Reset password  
- Revoke active sessions  
- Require MFA re-registration  

### 4.3 Email Containment  
- Quarantine malicious mail  
- ZAP removal of delivered threats  
- Block sender and associated URLs  

### 4.4 Policy Enforcement  
Conditional Access can immediately:

- Block risky sign-ins  
- Restrict access to compliant devices  
- Prevent access from unmanaged endpoints  

---

## 5. Remediation Model

### 5.1 Automated Remediation  
Defender resolves common incidents via:

- Malware removal  
- Registry repair  
- Artifact cleanup  

### 5.2 Manual Remediation  
Performed when needed:

- Device reimage  
- Baseline reapplication through Intune  
- Removal of malicious software paths  
- Account recovery and access review  

### 5.3 Policy Adjustments  
Incidents often drive:

- Stronger ASR settings  
- Updated Defender baselines  
- Adjusted email security or CA policies  

The single engineer maintains governance and documentation.

---

## 6. Logging & Evidence

All relevant evidence flows into:

- Unified Audit Log  
- Defender alerts  
- Intune device compliance logs  
- Sign-in and authentication telemetry  

These logs support:

- Audit preparation  
- Incident reconstruction  
- Future SIEM onboarding  

---

## 7. SIEM Readiness (Future Phase)

Although Microsoft Sentinel is not deployed, the environment is **architecturally prepared** for SIEM adoption:

- Log Analytics Workspace is active  
- All Defender logs are available for ingestion  
- Conditional Access and Identity logs are structured  
- Device telemetry is normalized  
- Governance and documentation are in place  

A SOC or MSSP could be integrated without major rework.

---

## 8. Incident Response Summary

This lean IR model provides:

- Rapid detection and containment  
- High-fidelity telemetry  
- Strong email and endpoint protection  
- Zero Trust-aligned controls  
- A practical, operational security workflow for a single engineer  

It demonstrates the ability to manage security end-to-end while preparing the organization for future SIEM and SOC maturity.

---

## 9. Document Intent

This document showcases a realistic incident response approach for small organizations and MSP environments, highlighting operational capability, technical depth, and clear governance even without a formal SOC.
