# Conditional Access Baseline (Concise)

This baseline enforces identity, device, and risk requirements across the tenant.

## Core Policies
1. **MFA Required**
   - Applied to all users
   - Excludes break-glass accounts (monitored)

2. **Block Legacy Authentication**
   - Prevents insecure authentication protocols

3. **Require Compliant or Hybrid Joined Device**
   - Ensures device posture validation (BitLocker, Secure Boot, Defender health)

4. **Require Approved Apps for Mobile**
   - Enforces app-level controls for iOS/Android

5. **Risk-Based Access**
   - Medium/high sign-in risk → block
   - High user risk → password reset + block

6. **Session Controls**
   - Sign-in frequency enforced for sensitive apps
   - Conditional Access App Control supported where applicable

## Intent
Provide a minimal, enforceable Zero Trust access baseline aligned to identity and device posture.
