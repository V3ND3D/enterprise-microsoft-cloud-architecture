# Microsoft Purview Data Protection Overview  
**Data Governance · Sensitivity Identification · DLP Enforcement · Audit Visibility**

Microsoft Purview provides the data governance and protection foundation for safeguarding sensitive information across Microsoft 365.  
This document summarizes how Purview is implemented to enforce HIPAA-aligned controls, prevent data leakage, and classify PHI across cloud workloads.

Purview complements the broader security architecture by adding governance, data visibility, and policy enforcement across email, cloud storage, and collaboration platforms.

---

## 1. Role of Purview in the Security Architecture

Purview directly supports:

- HIPAA data protection requirements  
- PHI identification using Sensitive Info Types (SITs)  
- Data Loss Prevention (DLP) monitoring  
- Visibility into sensitive content movement  
- Enforcement of “minimum necessary” access  
- Centralized compliance dashboards  

Purview is part of the Zero Trust model and integrates with:

- Exchange Online  
- SharePoint Online  
- OneDrive  
- Teams  
- Defender for Office 365  
- Compliance Manager  
- Entra ID (identity-driven policies)  

---

## 2. Sensitive Info Types (SITs)

Purview uses machine learning and pattern matching to detect PHI and other sensitive categories.

Common SITs include:

- Medical terms and diagnosis codes  
- Insurance identifiers  
- Patient-related terms  
- Email/phone/address combinations  
- Financial indicators (if applicable)  

These SITs allow Purview to identify and classify sensitive data automatically.

---

## 3. Workloads Covered

Purview protection applies across:

### 3.1 Exchange Online  
- Outbound email scanning  
- PHI detection  
- Policy-triggered alerts  
- Blocking or auditing actions  

### 3.2 SharePoint & OneDrive  
- File-level PHI scanning  
- Oversharing detection  
- External sharing restriction  

### 3.3 Microsoft Teams  
- Document and message-level scanning  
- Prevention of PHI leaving authorized users  
- Chat and file analysis  

This ensures full lifecycle protection across all collaboration surfaces.

---

## 4. Compliance & Audit Visibility

Purview provides:

- Activity Explorer for PHI-related activity  
- Alerts when sensitive data moves inappropriately  
- Audit evidence for compliance reviews  
- Dashboards for monitoring policy impact  
- Integration with Secure Score and Compliance Score  

This allows compliance and security teams to validate control effectiveness.

---

## 5. Enforcement Modes

Purview DLP policies typically operate in two modes:

### **Audit Mode (soft enforcement)**  
- Detect and log sensitive actions  
- Provide user tips  
- No blocking action taken  

Used during early rollouts.

### **Enforce Mode (hard enforcement)**  
- Block email containing PHI  
- Prevent file sharing outside the organization  
- Restrict copying or printing sensitive data  
- Trigger alerts and automated remediation  

The environment begins in Audit Mode and transitions into Enforce Mode once validation is complete.

---

## 6. Integration with Conditional Access & Intune

Purview signals combine with identity and device state:

- Conditional Access restricts PHI access to compliant devices  
- Intune prevents PHI on unmanaged endpoints  
- Defender alerts escalate high-severity PHI risks  
- Access is governed not only by identity, but by device security posture  

This forms a complete data protection pipeline.

---

## 7. Document Intent

This document provides a high-level overview of Purview’s role in the environment.  
The next file (`dlp-baseline.md`) defines the specific baseline DLP configuration.
