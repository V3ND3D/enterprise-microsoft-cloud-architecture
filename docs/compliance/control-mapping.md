# HIPAA Technical Control Mapping  
**HIPAA §164.312 → Microsoft Cloud Capabilities**

This mapping connects HIPAA’s required safeguards to the specific Microsoft technologies and configurations implemented in the environment.

The purpose is to provide auditors, security teams, and compliance stakeholders with a clear, defensible mapping of “what control satisfies what requirement.”

---

## 1. Access Control (164.312a)

| HIPAA Requirement | Microsoft Implementation |
|-------------------|--------------------------|
| Unique User Identification | Entra ID accounts with MFA |
| Emergency Access | Break-glass accounts with isolation |
| Automatic Logoff | Conditional Access session controls |
| Encryption & Decryption | BitLocker + TLS 1.2+ |

---

## 2. Audit Controls (164.312b)

| HIPAA Requirement | Microsoft Implementation |
|-------------------|--------------------------|
| Activity Logging | Unified Audit Log, Entra logs |
| System Monitoring | Defender for Endpoint telemetry |
| Log Retention | Log Analytics Workspace |
| Audit Review | Secure Score & threat analytics dashboards |

---

## 3. Integrity (164.312c)

| HIPAA Requirement | Microsoft Implementation |
|-------------------|--------------------------|
| Data Integrity | SharePoint/OneDrive versioning |
| Integrity Verification | Safe Attachments malware detonation |
| Device Integrity | Secure Boot, TPM, ASR, Defender |

---

## 4. Authentication (164.312d)

| HIPAA Requirement | Microsoft Implementation |
|-------------------|--------------------------|
| Person Authentication | MFA for all users |
| Entity Authentication | Conditional Access + Identity Protection |

---

## 5. Transmission Security (164.312e)

| HIPAA Requirement | Microsoft Implementation |
|-------------------|--------------------------|
| Encryption in Transit | TLS enforcement across M365 |
| Integrity Controls | Safe Links + Safe Attachments |
| Network Transport Security | Meraki AutoVPN, encrypted tunnels |

---

## 6. Device & Endpoint Controls

| Safeguard Area | Implementation |
|----------------|----------------|
| Encryption at Rest | BitLocker (TPM protector) |
| Malware Protection | Defender (EDR/AV) |
| Configuration Baselines | Intune policies |
| Privilege Minimization | LAPS + no local admin |

---

## 7. Data Protection & DLP

| Safeguard Area | Implementation |
|----------------|----------------|
| PHI Detection | Purview Sensitive Info Types |
| Restricting Unauthorized Disclosure | Purview DLP policies |
| Email Exposure Prevention | Safe Links, ZAP, anti-phishing |

---

## 8. Logging & Monitoring

| Safeguard Area | Implementation |
|----------------|----------------|
| Sign-In Tracking | Entra ID logs |
| Device Posture Tracking | Intune + Defender |
| Alerting | Microsoft 365 Defender |
| SIEM Readiness | Azure Log Analytics |

---

## 9. Document Intent

This mapping provides a defensible reference connecting HIPAA requirements to cloud security controls. It supports audits, compliance reviews, and future governance enhancements.
