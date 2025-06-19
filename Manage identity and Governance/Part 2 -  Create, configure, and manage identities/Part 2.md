# 📘 Create, Configure, and Manage Users in Microsoft Entra ID


---

## 📌 Overview

Every user who needs access to Azure resources requires an **Azure user account**.

- A **user account** stores details for:
  - ✅ **Authentication** (sign-in process)
  - ✅ **Authorization** (access control via access tokens)
- Once a user is authenticated, **Microsoft Entra ID** issues an **access token**.
- The token defines:
  - What resources the user can access
  - What actions they can perform

---

## 🛠️ Managing Users in Azure Portal

Use the **Microsoft Entra ID dashboard** in the **Azure Portal** to manage users.

### Important Points:
- You can only manage **one directory at a time**.

# 📂 What is a Directory in Microsoft Entra ID (Azure AD)?

In **Microsoft Entra ID** (formerly Azure AD), a **directory** is a container for all identity-related objects like:

- 👤 **Users**  
- 👥 **Groups**  
- 💻 **Devices**  
- 📦 **Applications**  
- 🔐 **Service Principals**


- Use the following to switch directories:

  - **Directory + Subscription** panel
  - **Switch directory** button (top toolbar)

---
🎯 Purpose of the Directory

The directory serves as your organization's **identity and access management database** in the Microsoft Cloud. It is used to:

- ✅ Store and manage identity information securely  
- ✅ Authenticate users and devices  
- ✅ Authorize access to Azure and Microsoft 365 resources  
- ✅ Apply security and compliance policies  
- ✅ Centralize user and access management across apps and services

> 📌 In short, the directory is the **foundation for managing who has access to what** in your Microsoft environment.
---

 📂  You May need to  Create Separate Directories

You may want to create a **separate directory per project** when:

- 🔐 Each project needs **isolated identity and access control**
- 🧾 Each has **separate billing, security, or compliance needs**
- 🚪 Different users, apps, or partners work on different projects
- 🌐 You want complete **multi-tenant isolation** (like for clients or environments)

⚠️ Things to Keep in Mind

| Consideration                 | Explanation                                                                 |
|------------------------------|-----------------------------------------------------------------------------|
| 🎟️ Sign-in accounts          | Users must be invited to each directory separately                          |
| 🔄 Switching directories      | You need to manually switch directories in the Azure Portal                 |
| 🔗 Subscriptions              | Each Azure subscription is linked to **one** directory at a time            |
| 🧭 Navigation                 | Azure Portal → "Switch directory" to work in the other project environment  |
| 🔐 Access Management          | Role assignments and policies do **not** carry over between directories     |


- When you create an Azure subscription, it's **automatically linked** to a specific Microsoft Entra ID (Azure AD) **directory (tenant)**.
- All user access, roles, and policies for that subscription are managed **within that directory only**.

| Term       | Meaning                                                                 |
|------------|-------------------------------------------------------------------------|
| **Tenant** | A dedicated, trusted instance of Microsoft Entra ID for your organization |
| **Directory** | The actual container that holds users, groups, apps, etc. (inside the tenant) |

> 📘 A subscription belongs to only **one directory** at a time. Plan your tenant and access strategy accordingly.

---

---
## 🔎 How to View Users

To view user accounts:

```text
Azure Portal → Microsoft Entra ID → Users → All Users
