# 🔐 Conditional Access in Microsoft Entra ID (Azure AD)

Microsoft Entra Conditional Access lets you enforce security policies based on specific conditions.  
It helps balance security and user productivity by applying the right access controls at the right time.

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

Conditional Access is a **Premium feature**:

- Requires **Microsoft Entra ID P1 or P2 license**
- Formerly known as Azure AD Premium P1/P2

---

## 🧪 Policy Components

### 🎯 Assignments

- **Users/Groups** – Who the policy applies to  
- **Cloud Apps/Actions** – What apps or operations are being accessed  
- **Conditions** – Criteria like location, device, platform, sign-in risk, etc.

---

## 🔍 Sign-in Risk

**Sign-in Risk** in Microsoft Entra ID represents the **probability that a given sign-in attempt might be malicious**,  
calculated using AI and machine learning to analyze user behavior, location, device, and login patterns.



### 📊 Risk Levels

| Risk Level           | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| **Low**              | Sign-in is unlikely to be malicious                                         |
| **Medium**           | Sign-in shows some suspicious behavior                                      |
| **High**             | Sign-in is very likely to be malicious (e.g., impossible travel, leaked creds) |
| **No risk detected** | Microsoft Entra ID detects no issues with the sign-in                       |

---

### 🧠 How Microsoft Detects Risk

- **Impossible travel** (e.g., same user signs in from India and US within 5 minutes)  
- **Atypical travel**  
- **Malware-linked IP addresses**  
- **Sign-ins from anonymous IPs or Tor**  
- **Leaked credentials**

---

### 🛡️ Use Cases in Conditional Access

- Block high-risk sign-ins  
- Require MFA for medium or high-risk logins  
- Allow only low/no-risk sign-ins  
- Redirect high-risk users to secure password reset

---

### 🧪 How to Use in a Policy

In a Conditional Access policy:

> Go to **Conditions → Sign-in Risk**, and choose which risk level(s) will trigger the policy.  
> ⚠️ Requires **Microsoft Entra ID Premium P2** license.

---

### 🏷️ License Requirement

| Feature               | Required License                      |
|-----------------------|---------------------------------------|
| **Sign-in Risk Policy** | Microsoft Entra ID Premium **P2**   |

---

---

## 🔐 Microsoft Entra ID – P1 vs P2 Feature Comparison

| 🔧 Feature / Capability                                         | ✅ P1 | 🔐 P2 |
|----------------------------------------------------------------|:----:|:----:|
| ✅ **Basic Conditional Access Policies**                        | ✔️   | ✔️   |
| ├─ User/Group targeting                                         | ✔️   | ✔️   |
| ├─ App-based targeting                                          | ✔️   | ✔️   |
| ├─ Location-based condition                                     | ✔️   | ✔️   |
| ├─ Device platform (iOS, Android, Windows, etc.)               | ✔️   | ✔️   |
| ├─ Require Multi-Factor Authentication (MFA)                   | ✔️   | ✔️   |
| ├─ Require compliant/hybrid Azure AD joined device             | ✔️   | ✔️   |
| ├─ Require approved client app                                 | ✔️   | ✔️   |
| ├─ Require app protection policy                               | ✔️   | ✔️   |
| ├─ Sign-in frequency / Session controls                        | ✔️   | ✔️   |
| ├─ Block or allow access based on conditions                   | ✔️   | ✔️   |
| 📊 Conditional Access insights and logging                     | ✔️   | ✔️   |
| ⚠️ **Sign-in Risk Condition** (based on real-time analysis)    | ❌   | ✔️   |
| ⚠️ **User Risk Condition** (based on identity protection)      | ❌   | ✔️   |
| 🔐 Risk-based Conditional Access (automated decisioning)       | ❌   | ✔️   |
| 🔐 Identity Protection (detect & respond to risky activity)    | ❌   | ✔️   |
| 👥 Access Reviews                                               | ❌   | ✔️   |
| 🔐 Privileged Identity Management (PIM)                         | ❌   | ✔️   |
| 🧭 Entitlement Management & Lifecycle Workflows                 | ❌   | ✔️   |

---

## 🌍 Location Condition

Use **Named Locations** (e.g., trusted IP ranges or countries) to limit access.

---

## 💻 Device Platform Condition

Specify the device platforms that policies apply to:

| Platform    | Description                                  |
|-------------|----------------------------------------------|
| **Windows** | Devices running Windows 10/11, Server, etc.  |
| **macOS**   | Apple desktop and laptop devices             |
| **iOS**     | iPhones and iPads                            |
| **Android** | Phones and tablets using the Android OS      |
| **Linux**   | Devices running Linux (Ubuntu, Debian, etc.) |
| **Unknown** | Devices where the OS can’t be determined     |

---

## 📱 Client App Type

Control access by application type:

| Client App Type                     | Description                                                           |
|------------------------------------|-----------------------------------------------------------------------|
| **Browser**                         | Web browsers (e.g., Edge, Chrome, Firefox)                            |
| **Mobile Apps and Desktop Clients** | Apps like Outlook, Teams, OneDrive (supporting modern auth)           |
| **Legacy Authentication Clients**   | Older apps using basic auth (POP, IMAP, SMTP, Office 2010)            |
| **Other Clients**                   | Includes apps using modern protocols like PowerShell, Azure CLI, etc. |

---

## ✅ Access Controls

Decide whether to:

- **Grant or Block Access**
- Require one or more of the following:
  - Multi-Factor Authentication (MFA)
  - Compliant device
  - Hybrid Azure AD joined device
  - Approved client app
  - Terms of use acceptance

---

## ⏱️ Session Controls (Optional)

Control user session behavior after sign-in:

- Restrict download or upload
- Enforce sign-out after a certain time
- Limit access on unmanaged devices

---

> 🔒 **Conditional Access ensures that only the right users, under the right conditions, can access your organization's data and apps.**

---
