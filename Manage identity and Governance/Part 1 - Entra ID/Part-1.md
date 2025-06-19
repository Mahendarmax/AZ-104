# Microsoft Entra ID 
---
![image](https://github.com/user-attachments/assets/212b449a-763e-4fa4-8695-df9c6f479664)

## 🔹 1. Microsoft Entra ID vs. Active Directory Domain Services (AD DS)

- **AD DS** is an on-premises directory service.
- **Microsoft Entra ID** is a cloud-based Platform as a Service (PaaS).
- No need for infrastructure deployment or maintenance.
- Entra ID offers native cloud features:
  - Multi-factor authentication (MFA)
  - Self-service password reset (SSPR)
  - Identity protection
  - [Conditional Access](./Aditional_info/Conditional_Access.md)
  - [Application Proxy](./Aditional_info/Application_Proxy.md)

---

## 🔹 2. Key Identity Management Capabilities

- Manage users and groups (create, provision, maintain)
- Configure Single Sign-On (SSO) for SaaS apps
- Enable federation between organizations
- Detect irregular sign-in activity
- Implement multi-factor authentication
- Configure Application Proxy
- Extend on-premises AD DS using Entra Connect

---

## 🔹 3. Entra Tenant Architecture

- Multi-tenant by default (isolation between instances)
- Each Azure subscription links to **only one** Microsoft Entra tenant
- A single Microsoft Entra tenant can support **multiple Azure subscriptions**
- Tenants serve as **security boundaries** and contain identity objects

---

## 🔹 4. Microsoft Entra Tiers

- **Free Tier**:
  - Included with Azure or Microsoft 365 subscriptions
  - Basic identity management features
- **Paid Tiers** (Basic, Premium P1/P2):
  - Conditional Access
  - Identity Protection
  - Group-based access management
  - Self-service capabilities

---

## 🔹 5. Domain Configuration

- Default domain: `yourtenant.onmicrosoft.com`
- Custom domains supported via DNS verification
- Domain names define user sign-in identities

---

## 🔹 6. Schema Differences with AD DS

- Fewer object types than AD DS
- No **Organizational Units (OUs)** – use **groups** instead
- No support for **traditional computer objects**
  - Uses **device class** for modern device management
- Group Policy Objects (GPOs) not supported – use **modern management**

---

## 🔹 7. Application Representation

- Two object types:
  - **Application**: Defines the app
  - **ServicePrincipal**: Represents the app instance in a tenant
- Enables use of an application across multiple tenants

---

## 🔹 8. Modern Identity Focus

- Designed for **web and cloud-based applications**
- Powers identity for services like:
  - Microsoft 365
  - Microsoft Intune
  - Azure services
- Supports millions of authentications per week globally

---

# 🔁 Active Directory vs Microsoft Entra ID (Azure AD)

the key differences between **Active Directory (AD)** and **Microsoft Entra ID (formerly Azure AD)** for identity and access management.

---

## 📊 Feature Comparison Table

| **Feature / Category**                | **Active Directory (AD)**                                | **Microsoft Entra ID (Azure AD)**                                |
|--------------------------------------|-----------------------------------------------------------|------------------------------------------------------------------|
| **Type of Service**                  | On-premises directory service                             | Cloud-based identity and access management (IDaaS)               |
| **Hosting Environment**              | Runs on Windows Server (local data centers)               | Runs in Microsoft Azure (cloud)                                  |
| **Protocol Support**                 | LDAP, Kerberos, NTLM                                      | SAML, OAuth 2.0, OpenID Connect                                  |
| **Primary Use Case**                 | Authentication for on-prem servers, desktops, and apps    | Authentication for cloud apps (M365, Azure, SaaS)                |
| **Device Join Type**                 | Domain-joined (Windows PCs, servers)                      | Azure AD-joined / Hybrid Azure AD-joined                         |
| **Group Policy Support**            | Yes (via GPOs, OUs, etc.)                                 | No GPOs; uses Intune for modern management                       |
| **Organizational Units (OUs)**       | Yes, for delegation and GPO scoping                       | Not supported; use groups and roles instead                      |
| **Internet Access**                  | Not designed for direct internet access                   | Designed for internet-native applications                        |
| **Single Sign-On (SSO)**             | Limited to on-prem AD-integrated apps                     | SSO for thousands of SaaS/cloud applications                     |
| **Multi-Factor Authentication (MFA)**| Requires additional setup (e.g., NPS Extension)           | Built-in support (with Premium P1 or P2 license)                 |
| **Self-Service Password Reset (SSPR)**| No native support                                         | Supported (Free tier for cloud users, more in Premium)           |
| **Conditional Access**              | No                                                        | Yes (Premium feature)                                            |
| **User Federation**                 | Limited / complex to configure                            | Native support for B2B and B2C scenarios                         |
| **License / Cost**                   | Windows Server CALs                                       | Free, Basic, Premium P1/P2 tiers                                 |
| **Application Access**              | Mostly internal/on-prem                                   | Secure access to cloud and hybrid apps                           |
| **Join to Microsoft 365 / Azure**    | Not possible directly                                     | Core identity provider for Microsoft 365 and Azure               |

---

📘 **Note**: While both services manage identities, **Active Directory** is suited for on-premises environments, whereas **Microsoft Entra ID** is optimized for cloud-native solutions.


📘 **Note**: Microsoft Entra ID is not a replacement for AD DS in traditional environments but complements it for modern cloud-first identity and access management.

---

# 📘 Microsoft Entra ID as a Directory Service for Cloud Apps

## ☁️ Role in Cloud-Based Services

- Microsoft Entra ID is essential for enabling **authentication and authorization** in Microsoft cloud services like:
  - Microsoft 365
  - Microsoft Intune
  - Microsoft Azure
  - Microsoft Dynamics 365

- Each cloud service creates its own **Microsoft Entra tenant**, but it's recommended to use a **single tenant** for unified identity management across services.

## 🌐 Unified Identity Provider

- Microsoft Entra ID acts as a **single identity service** across all Microsoft cloud services.
- It supports **Single Sign-On (SSO)** for both Microsoft and third-party services such as:
  - Facebook
  - Google
  - Yahoo
  - On-premises AD DS

## 👩‍💻 Developer and App Integration

- Microsoft Entra ID can be integrated with **custom applications** for authentication.
- Developers can simplify this integration using:
  - **Azure Portal**
  - **Microsoft Visual Studio 2013 or later**

- In **Azure App Service**, authentication using Microsoft Entra can be enabled via:
  - The **Authentication/Authorization blade**
  - Specify the Entra tenant to restrict access only to users within that directory.

- **Deployment slot-level authentication settings** can be configured independently for staging or production use cases.

---

---
