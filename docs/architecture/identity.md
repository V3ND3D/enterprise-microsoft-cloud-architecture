# Identity Architecture  
**Entra ID · Access Control · Conditional Access · Identity Lifecycle · Governance**

This document outlines the identity architecture that defines authentication, authorization, and administrative control across the Microsoft cloud environment.  
Identity serves as the foundational trust plane, determining how users, devices, and services interact with protected resources.

The goal is to establish a consistent and enforceable identity model aligned with Zero Trust principles and regulatory requirements.

---

## 1. Identity as the Control Plane

Identity is the authoritative source for:
- Authentication and MFA
- Authorization and least-privilege access
- Device trust evaluation
- Administrative role boundaries
- Access governance and lifecycle management

All architecture decisions across endpoint management, security, and governance originate from identity posture.

---

## 2. Directory Structure & Organizational Model

### 2.1 Tenant Organization
- Users, devices, and administrators are organized using a standardized grouping model.  
- Security groups follow consistent naming conventions for automation and auditability.  
- Dynamic groups are used where feasible to reduce administrative overhead.

### 2.2 Administrative Boundary Model
Roles are scoped to align with least-privilege principles:
- **Global Admin:** Restricted to break-glass accounts and exceptional procedures  
- **Cloud Device Administrator:** Endpoint-specific responsibilities  
- **Security Administrator:** Threat insights, alerts, and policies  
- **Compliance Administrator:** Data handling & DLP responsibilities  
- **User/Group Administrator:** Provisioning & lifecycle tasks  

This separation ensures clear operational boundaries and reduces risk of privilege misuse.

---

## 3. Identity Lifecycle Management

A consistent identity lifecycle ensures users and systems maintain correct entitlements across their tenure.

### 3.1 Provisioning
- Accounts created in Entra ID  
- Assigned to standardized security groups  
- MFA enrollment enforced at first sign-in  
- Device provisioning tied to Autopilot workflow  

---

### 3.1.1 License Assignment & Entitlement Provisioning

Licensing determines which services and security controls are available to each identity.  
Licenses are assigned through **group-based licensing** to enforce consistency and reduce administrative overhead.

#### License Types
- **Microsoft 365 Business Premium** (core productivity + security suite)  
- **Defender for Endpoint Plan 2**  
- **Intune (MDM/MAM)**  
- **Azure AD Premium features** (MFA, Conditional Access, Identity Protection)  
- Role-specific or workload-specific add-ons as required  

#### Assignment Workflow
1. Account is created in Entra ID  
2. User placed into appropriate licensing/security groups  
3. Group-based licensing auto-assigns:  
   - Productivity suite (Office, Teams, OneDrive)  
   - Intune enrollment rights  
   - Defender for Endpoint onboarding  
   - Conditional Access policy scope  
4. Licensing validated prior to device provisioning  

#### Operational Impact
- Ensures users receive correct security and productivity entitlements  
- Reduces license drift and misalignment  
- Supports audit and compliance requirements  
- Enables automated endpoint onboarding and Defender activation  

Licensing is treated as a foundational identity function because downstream services (Intune, Defender, Purview) depend on it.

---

### 3.2 Access Maintenance
- Access reviews used for sensitive roles  
- Group memberships audited regularly  
- Conditional Access policies enforce continuous validation  

### 3.3 Deprovisioning
- Immediate revocation of sessions  
- Removal of group memberships  
- Device retirement actions triggered  
- Mailbox and data governance steps executed  

Lifecycle consistency ensures identity quality and reduces long-term access risk.

---

## 4. Conditional Access Architecture

Conditional Access defines the real-time access decision engine.  
Policies follow a layered model:

### 4.1 Baseline Policies
- MFA required for all accounts  
- Block legacy authentication  
- Require modern authentication protocols  

### 4.2 Device Trust Policies
- Require device to be compliant for resource access  
- Require approved or managed apps for mobile scenarios  
- Restrict access from unknown or unmanaged endpoints  

### 4.3 Location & Risk Controls
- Block sign-ins from risky countries or TOR networks  
- Entra ID Identity Protection integrated for risk evaluation  
- Sign-in and user risk policies enable automated remediation  

### 4.4 Session Controls
- Conditional Access App Control for SaaS enforcement  
- Limited access (web-only, read-only) for high-risk sessions  

The objective is to ensure that **authentication + device posture + risk signals = access decision**.

---

## 5. Role-Based Access Control (RBAC)

RBAC enforces least-privilege across all administrative workflows.

### 5.1 Role Assignment
- No standing global admin access  
- Admin roles assigned through privileged access groups (PAGs)  
- Roles defined by functional responsibility (Identity, Endpoint, Security, Compliance)

### 5.2 Privileged Access Workflow
- Break-glass accounts isolated and monitored  
- Admin roles reviewed quarterly  
- Elevation workflows documented and restricted  
- Logging for all administrative actions  

### 5.3 Service Principal Governance
- App consent restricted  
- OAuth applications require security review  
- High-permission SPNs monitored via Defender & Entra logs  

This ensures administrative actions are auditable and controllable.

---

## 6. Identity Governance Controls

Identity Governance supports compliance, auditability, and operational consistency.

### 6.1 Access Reviews
- Scheduled reviews for security groups and privileged roles  
- Removes dormant or unnecessary access rights  

### 6.2 Entitlement Management
- Access packages used for structured onboarding flows  
- Automated approvals ensure consistency  
- Access expiration reduces long-term access drift  

### 6.3 Consent & App Governance
- User consent disabled for unverified apps  
- Admin consent workflows reviewed  
- Defender for Cloud Apps monitors OAuth usage  

### 6.4 Audit & Monitoring
- Sign-in logs ingested into Log Analytics  
- Identity Protection alerts escalated per severity  
- Reporting dashboards used for compliance evaluations  

---

## 7. Identity Security Controls

### 7.1 Authentication Controls
- MFA enforced universally  
- Passwordless authentication planned (FIDO2 / Authenticator)  
- Blocking legacy authentication to remove insecure protocols  

### 7.2 Risk-Based Controls
- Risky user and risky sign-in policies enabled  
- Automated remediation: MFA reset, password reset, or access block  

### 7.3 Session Hardening
- Token lifetime and sign-in frequency governed by CA  
- High-risk operations require reauthentication  

---

## 8. Architectural Outcomes

- Centralized identity authority governing all access decisions  
- Reduced administrative risk through RBAC and separation of duties  
- Conditional Access enforcing device compliance and MFA  
- Identity lifecycle processes aligned with security and operational requirements  
- Consistent governance for privileged accounts, OAuth apps, and entitlement workflows  
- Strengthened identity security posture through risk-based adaptive access  

---

## 9. Document Intent

This document serves as:
- A reference for designing identity-centric architectures  
- A guide for implementing Conditional Access and RBAC  
- A baseline for integrating identity with endpoint and security workflows  
- A foundation for Zero Trust-aligned operational models  

Identity functions as the anchor for the entire cloud environment.  
Subsequent documents build on this control plane.
