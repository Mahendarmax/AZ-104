# 📘 Manage Licenses in Microsoft Entra ID

Microsoft cloud services like Microsoft 365, EMS, and Dynamics 365 require licenses for user access. Microsoft Entra ID helps manage and assign these licenses efficiently using portals or PowerShell.

---

## ✅ Key Concepts

### 🔑 Traditional Licensing (Single-User Assignment)
- Licenses were assigned **individually to each user**.
- Admins needed to manually update or write PowerShell scripts for changes.
- ❌ Not scalable for large organizations.
- Prone to inconsistency and delays in provisioning or deprovisioning.

### 👥 Group-Based Licensing (Modern & Recommended)
- Assign licenses to **security groups** in Microsoft Entra ID.
- **Automatic license assignment** when users join or leave the group.
- Reduces manual tasks and administrative overhead.
- Ensures license compliance and consistency across departments or roles.

---

## 🔄 Single-User vs Group-Based Licensing

| Feature                      | Single-User Licensing                 | Group-Based Licensing                        |
|-----------------------------|---------------------------------------|----------------------------------------------|
| Assignment Method           | Manual or scripted per user           | Assigned to Microsoft Entra security groups  |
| Scalability                 | Poor (tedious for large orgs)         | High (automatic propagation)                 |
| Automation                  | Requires PowerShell scripts           | Built-in automation                          |
| License Consistency         | Hard to maintain                      | Consistent across group members              |
| Dynamic Group Support       | ❌ Not applicable                      | ✅ Supported (via Microsoft Entra dynamic groups) |
| Best Use Case               | Small orgs or exceptions              | Large orgs and role-based provisioning       |

---

## 🪪 License Requirements

### Required Subscriptions for Group Licensing
To use **group-based licensing**, you must have one of the following:
- Microsoft Entra ID Premium P1 or P2 (trial or paid)
- Office 365 Enterprise E3 or equivalent:
  - Office 365 A3, GCC G3, GCC High E3, DoD E3

### Number of Licenses
- You **must have a license for each unique user** in a licensed group.
- Users **don’t need to be assigned individually**, but the license count must match group size.
- Example: If a group has 1,000 members → you need at least 1,000 licenses.

---

## 🧾 Types of Licenses

### 🔹 Microsoft Entra ID Plans
- **Free** – Basic directory and identity features
- **Premium P1** – Conditional Access, group-based licensing, SSO, etc.
- **Premium P2** – Includes all P1 features + Identity Protection, PIM

### 🔹 Microsoft 365 Plans
- Microsoft 365 Business (Basic, Standard, Premium)
- Microsoft 365 Enterprise (E1, E3, E5)
- Microsoft 365 Education (A1, A3, A5)

### 🔹 Office 365 Plans
- Office 365 Enterprise (E1, E3, E5)
- Office 365 Government (G1, G3, G5, GCC High, DoD)

### 🔹 Enterprise Mobility + Security (EMS)
- EMS E3 and EMS E5

### 🔹 Dynamics 365 Licenses
- Apps for Sales, Customer Service, Field Service, and more

---

## 🌟 Features of Group-Based Licensing

- ✔ Assign licenses to **any security group** (cloud-only or synced from on-prem via Entra Connect).
- ✔ Disable specific **service plans** in product (e.g., disable Yammer temporarily).
- ✔ Supported for:
  - Microsoft 365
  - EMS
  - Dynamics 365
- ✔ Managed through **Azure portal** (coming to Microsoft Entra Admin Center).
- ✔ Automatic and **fast license provisioning** (typically within minutes).
- ✔ Supports **multiple license sources** (group + direct assignment):
  - License is counted only **once**, even if applied from multiple groups.
- ⚠️ Alerts provided when:
  - Not enough licenses
  - Conflicting services assigned
- 📋 Admins can review errors and **resolve license conflicts**.

---

## 🌍 Usage Location

- Some Microsoft services are **not available in all countries**.
- Admins should set **Usage Location** in the user profile.
  - If not set, user inherits **directory default location**.
- ✅ **Best Practice**:
  - Always define usage location during user creation or via Microsoft Entra Connect.
  - Ensures users do **not receive services in unsupported regions**.

---

## 📌 Notes for Exams

- Understand the difference between **Single-User** and **Group-Based** license assignment.
- Know **license requirements** and **count logic**.
- Recognize **group licensing benefits**: automation, scalability, efficiency.
- Be familiar with **types of licenses** (Entra ID, Microsoft 365, EMS, Dynamics).
- Understand the importance of setting the **Usage Location**.
- Group licensing is currently supported in the **Azure Portal**, and **coming soon** to Microsoft Entra Admin Center.

---
