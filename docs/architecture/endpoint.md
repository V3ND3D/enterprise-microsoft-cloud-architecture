# Endpoint Architecture  
**Intune · Device Compliance · Configuration Baselines · Autopilot · Lifecycle · Hardening**

This document outlines the endpoint architecture that governs device onboarding, configuration, compliance, and operational management within the Microsoft cloud ecosystem.  
Endpoint management establishes device trust, enforces security baselines, and provides continuous visibility into the health and security of the workstation fleet.

The architecture follows a Zero Trust model, where **device compliance is a prerequisite for access** to corporate resources.

---

## 1. Device Trust Model

Endpoint trust is established through a combination of identity, compliance posture, and security signals.  
A device is considered *trusted* when it meets the following criteria:

- Entra-joined or hybrid-joined  
- Managed through Intune  
- Meets compliance baselines (BitLocker, Secure Boot, TPM, OS integrity)  
- Has Defender for Endpoint active and reporting  
- Is assigned to the correct user and group scopes  

Devices failing any requirement enter **restricted access states** through Conditional Access and Intune compliance actions.

---

## 2. Provisioning Architecture (Autopilot & Enrollment)

Device provisioning is standardized using Autopilot and Entra-based enrollment flows.

### 2.1 Autopilot Registration
- Devices registered with hardware hashes imported into Intune  
- Assigned to Autopilot deployment profiles  
- Group-tagged for automated policy and app assignment  

### 2.2 Deployment Workflow
1. Device powered on or reset  
2. Autopilot applies:
   - Tenant information  
   - Enrollment status page  
   - Device naming conventions  
3. Device auto-enrolls into Intune  
4. Compliance and configuration profiles apply during provisioning  
5. Required apps and security baselines deploy automatically  

### 2.3 Provisioning Principles
- No manual imaging  
- No local account provisioning  
- All devices provisioned consistently via cloud-driven automation  

This ensures predictable onboarding, reduced provisioning time, and consistent security posture.

---

## 3. Configuration & Baseline Enforcement

Each device receives enforced configurations through Intune profiles and baselines.

### 3.1 Security Baselines
- Windows Security Baseline  
- Microsoft 365 Security Baseline  
- Custom security configurations for hardened posture  

Includes:
- Firewall settings  
- Credential Guard  
- Exploit Protection validation  
- ASR compatibility baselines  

### 3.2 Configuration Profiles
Profiles enforce:
- BitLocker settings (TPM-only protector)  
- Browser restrictions and hardening  
- Remote help availability  
- Endpoint security policies (AV/EDR alignment)  
- Local admin restriction  
- Password and lockout policies  

### 3.3 Update Rings (Windows Update for Business)
- Structured update channels to reduce disruption  
- Quality updates enforced regularly  
- Feature updates staged for testing → production  

This structure provides an enforceable, auditable configuration footprint.

---

## 4. Compliance Policies & Enforcement

Compliance policies determine whether a device is permitted to access corporate services.

### 4.1 Compliance Criteria
- **BitLocker encryption required**  
- **Secure Boot enabled**  
- **TPM available and activated**  
- **Up-to-date OS build**  
- **Defender for Endpoint healthy**  
- **No high-risk threats detected**  

### 4.2 Compliance States & Actions
- Noncompliant devices → restricted access via Conditional Access  
- Notification rules inform users of remediation steps  
- Automated remediation for select misconfigurations  

### 4.3 Reporting & Monitoring
- Compliance dashboards in Intune  
- Device risk levels from Defender integrated  
- Dead/stale devices flagged for removal  

Compliance is a core element of the Zero Trust posture.

---

## 5. Local Admin Governance

Minimizing endpoint privilege is critical for reducing lateral movement and malware execution risk.

### 5.1 Local Admin Restrictions
- End users are not local administrators  
- Admin group membership enforced via Intune  
- Unauthorized privilege elevation blocked  

### 5.2 Microsoft LAPS Implementation
- Local passwords rotated automatically  
- Stored securely in Entra ID  
- Access controlled through RBAC  

### 5.3 Just-In-Time Elevation (Future State)
- Privilege elevation via PIM or elevation tools considered for mature deployments  

This governance model prevents privilege creep and enforces clean administrative boundaries.

---

## 6. Endpoint Hardening (Defender + OS Configuration)

### 6.1 Defender for Endpoint Integration
- Devices onboarded automatically during enrollment  
- EDR is active with real-time monitoring  
- Attack Surface Reduction rules enforced  
- Exploit Protection enabled and standardized  

### 6.2 OS-Level Hardening
Includes:
- Restricting potentially vulnerable features  
- Hardening removable storage  
- Reducing unsigned/unknown app execution  
- Enforcing credential protection features  

### 6.3 Application Controls (Future Phase)
- AppLocker or Intune App Control for Business for production deployment  
- Controlled folder access based on business requirements  

---

## 7. Lifecycle Management

Consistent lifecycle operations ensure workstations remain secure and manageable across their lifespan.

### 7.1 Active Device State
Devices must:
- Check in regularly  
- Report compliance  
- Maintain Defender health  
- Stay current on updates  

### 7.2 Lost/Stolen Device Response
- Remote wipe  
- Lock  
- Selective wipe for BYOD scenarios  

### 7.3 Decommissioning
- Autopilot reset or wipe  
- Removal from dynamic groups  
- Retirement from Intune  
- License reallocation back to directory pools  

Lifecycle management ensures data protection and posture consistency.

---

## 8. Telemetry, Reporting & Monitoring

Telemetry strengthens detection, visibility, and compliance reporting.

### 8.1 Defender Telemetry
- EDR data sent to Defender portal  
- Alerts integrated with incident queue  
- Device risk signals feed Conditional Access decisions  

### 8.2 Log Analytics Integration
- Central workspace collects security, identity, and endpoint logs  
- Enables long-term retention for auditability  
- Supports future Sentinel deployment  

### 8.3 Intune Reporting
- Device compliance  
- Update status  
- Hardware/software inventory  
- Policy deployment monitoring  

This telemetry model provides complete endpoint visibility.

---

## 9. Architectural Outcomes

- Standardized provisioning across the entire device fleet  
- Predictable and enforceable security baselines  
- Compliance-driven access across all endpoints  
- Local admin governance aligned with least-privilege principles  
- Defender integration providing security telemetry and automated response  
- Consistent lifecycle operations for onboarding, maintenance, and retirement  
- High endpoint posture maturity supporting Zero Trust adoption  

---

## 10. Document Intent

This document serves as:
- A reference for designing endpoint management strategies  
- A guide for implementing Intune compliance and configuration enforcement  
- A foundation for integrating endpoints with identity and security architecture  
- A baseline for modern, cloud-managed workstation environments  

Endpoint trust forms the second pillar of the overall cloud architecture.  
Subsequent documents build on this enforcement layer.
