# Microsoft Entra ID – AZ-104 Exam Summary
---

## 🔹 1. Microsoft Entra ID vs. Active Directory Domain Services (AD DS)

- **AD DS** is an on-premises directory service.
- **Microsoft Entra ID** is a cloud-based Platform as a Service (PaaS).
- No need for infrastructure deployment or maintenance.
- Entra ID offers native cloud features:
  - Multi-factor authentication (MFA)
  - Self-service password reset (SSPR)
  - Identity protection
  - Conditional Access
  - Application Proxy

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

📘 **Note**: Microsoft Entra ID is not a replacement for AD DS in traditional environments but complements it for modern cloud-first identity and access management.

