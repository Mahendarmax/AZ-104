# 🔐 Conditional Access in Microsoft Entra ID (Azure AD)

Microsoft Entra Conditional Access lets you enforce security policies based on specific conditions. It helps balance security and user productivity by applying the right access controls at the right time.

---

## ⚙️ Examples of Conditional Access Scenarios

- **Require MFA for External Users**  
  Users outside the corporate network must perform Multi-Factor Authentication.

- **Block Access from Risky Sign-ins**  
  Automatically block logins detected as high risk.

- **Require Compliant Device**  
  Only allow access from Intune-compliant devices.

- **Limit Access to Specific Countries**  
  Block logins from outside trusted regions.

- **Allow Access to SharePoint Online but Block Download on Unmanaged Devices**  
  Useful for BYOD (Bring Your Own Device) scenarios.

---

## 🏷️ Licensing Requirement

- Conditional Access is a **Premium feature**
  - Requires **Microsoft Entra ID P1 or P2 license**
  - Formerly known as Azure AD Premium P1/P2

---

## 🧪 Policy Components

### 🎯 Assignments
- **Users/Groups** – Who the policy applies to
- **Cloud Apps/Actions** – What apps or operations are being accessed
- **Conditions** – Criteria like:
  - Sign-in risk
  - Location
  - Device platform
  - Client app type

### ✅ Access Controls
- **Grant or Block Access**
- **Require One or More of the Following**:
  - Multi-Factor Authentication (MFA)
  - Compliant device
  - Hybrid Azure AD joined device
  - Approved client app
  - Terms of use acceptance

### ⏱️ Session Controls (Optional)
- Control user session behavior after sign-in, such as:
  - Restricting download or upload
  - Enforcing sign-out after a certain time
  - Limited access on unmanaged devices

---

> 🔒 Conditional Access ensures that only the right users, under the right conditions, can access your organization's data and apps.

