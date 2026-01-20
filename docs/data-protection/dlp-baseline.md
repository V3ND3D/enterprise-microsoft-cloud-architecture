# Data Loss Prevention (DLP) Baseline  
**PHI Protection · Audit Mode → Enforcement Mode · Cross-Workload Controls**

This document outlines the baseline Data Loss Prevention (DLP) policy implemented in Microsoft Purview to protect sensitive information, including PHI, across Microsoft 365 workloads.

The baseline ensures HIPAA-aligned data handling and restricts unauthorized disclosure of sensitive data through email, file sharing, or collaboration tools.

---

## 1. Purpose of the Baseline

The DLP baseline enables:

- Detection of PHI across M365  
- Prevention of unauthorized data sharing  
- Audit-ready reporting  
- Consistency of data governance across workloads  
- Alignment with HIPAA technical safeguards  

This baseline is the foundation for future granular policies.

---

## 2. Workload Coverage

The baseline policy applies to:

- **Exchange Online**  
  - Outbound email controls  
  - Policy tips for users  
  - Blocking or auditing based on sensitivity  

- **SharePoint Online & OneDrive**  
  - Prevent external sharing of PHI  
  - Restrict access based on sensitivity levels  

- **Microsoft Teams**  
  - Scans content and files shared in chats  
  - Monitors sensitive data movement  

This ensures full protection across all collaboration and storage channels.

---

## 3. Sensitivity Detection

Purview uses Sensitive Info Types (SITs) to detect:

- Medical information  
- Personal identifiers (Name + DOB + Address combinations)  
- Insurance-related terms  
- Other regulated content categories  

These SITs support HIPAA’s “minimum necessary” requirement.

---

## 4. Enforcement Flow

### Enforcement occurs in two stages:

### **Stage 1 — Audit Mode**
- Alerts logged in Purview  
- User notifications (policy tips)  
- No blocking action  
- Used during initial rollout and tuning  

### **Stage 2 — Enforce Mode**
- Blocks email containing PHI sent to unauthorized recipients  
- Prevents external file sharing of sensitive content  
- Restricts copying and printing where applicable  
- Generates alerts for Security & Compliance review  

The environment transitions from Audit → Enforce only after validation.

---

## 5. User Experience Controls

- **Policy Tips:** Inform users when PHI is detected  
- **Justification Prompts:** Optional prompts for override (if enabled)  
- **Alert Emails:** Notify security admins of violations  

This reduces accidental disclosures and supports user education.

---

## 6. Governance & Monitoring

Purview provides centralized visibility via:

- Activity Explorer  
- Alert Explorer  
- DLP incident logs  
- Compliance Manager scoring  
- Exportable audit evidence  

All events are retained in accordance with HIPAA audit requirements.

---

## 7. Future Enhancements

Planned improvements include:

- Granular PHI-specific DLP policies  
- Automatic labeling via sensitivity classification  
- SIEM integration via Sentinel connectors  
- Conditional Access adjustments based on DLP events  

These enhancements will further strengthen data protection.

---

## 8. Document Intent

This document establishes the baseline DLP configuration used to protect PHI across cloud workloads.  
It complements:

- `purview-overview.md`  
- HIPAA safeguard documentation  
- Security architecture documentation
