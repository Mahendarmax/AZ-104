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
Assign different Microsoft Entra ID licenses to specific users using group-based licensing.

**NOTE: you can’t assign different licenses to different users within the same group — all members of a group inherit the same set of licenses.**

## 👥 Scenario

- **Total users**: 5
- **License distribution**:
  - 2 users → **Microsoft Entra ID Basic**
  - 3 users → **Microsoft Entra ID P1**

## ✅ Solution: Use Separate Groups

Create **two separate groups** and assign licenses accordingly:

### 🔹 Group 1: `Basic-License-Group`
- Add 2 users
- Assign **Microsoft Entra ID Basic license**

### 🔹 Group 2: `P1-License-Group`
- Add 3 users
- Assign **Microsoft Entra ID P1 license**

Each user inherits the license based on their group membership.

## ⚙️ Steps to Assign License to a Group

1. Go to **Microsoft Entra admin center**
2. Navigate to **Groups** → Select the target group
3. Click **Licenses** → **Assignments**
4. Select the appropriate license
5. Click **Save**

## ℹ️ Notes

- Users can belong to **multiple groups**.
- Final license is a **union of all services** from group memberships.
- Conflicts and assignment issues can be monitored in the **Microsoft 365 Admin Center → Billing → Licen

## ✅ What Will Happen if the User Belongs to Two Different Groups?

### Scenario

A user is a member of two groups:

- `Basic-License-Group` → Assigns **Microsoft Entra ID Basic**
- `P1-License-Group` → Assigns **Microsoft Entra ID P1**

### ✅ Expected Behavior

- ✅ Only the **higher-level license (P1)** will be **applied** to the user
- ✅ Only **one license unit (P1)** will be **consumed**
- ✅ **Microsoft Entra automatically prioritizes** higher-tier licenses to avoid duplication

### 📝 Note

- The **Basic license** will be **ignored** for that user
- No duplicate or unnecessary license consumption occurs
- User will have access to **all features** provided by the **P1 license**

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

## 📦 What Is a Subscription?

- A **subscription** is a product/plan you purchase from Microsoft.
- It includes **a set number of licenses** that can be assigned to users.
- Examples:
  - Microsoft 365 E3 (10-user subscription)
  - Microsoft Entra ID P1 (5-user subscription)

---

## 🧾 What Is a License?

- A **license** is what gives an individual user access to Microsoft services (e.g., Teams, Outlook, Entra ID features).
- You **assign licenses** from your subscription to users.
- A license includes access to one or more service plans (e.g., Exchange, OneDrive).

---

## 🔄 Key Difference: Subscription vs License

| Concept        | Subscription                          | License                                    |
|----------------|----------------------------------------|--------------------------------------------|
| What it is     | A product/plan you buy                 | The entitlement you assign to a user       |
| Scope          | Applies to your entire organization    | Applies to specific users or devices       |
| Contains       | Multiple licenses                      | Access to services like Teams, Outlook     |
| Billing        | Monthly or yearly                      | Included in the subscription               |

---

## ✅ Do I Need to Buy Both?

- **No** – When you buy a **subscription**, it already **includes licenses**.
- You do **not** buy licenses separately.
- You simply assign the licenses from your active subscription.

---

## 🔁 Can I Increase Licenses in a Subscription?

- ✅ Yes, you can increase or decrease license count anytime.
- Go to [Microsoft 365 Admin Center](https://admin.microsoft.com) → **Billing → Your products** → Update license quantity.
- Billing updates automatically.

---


## 🪪 License Requirements

### Required Subscriptions for Group Licensing
To use **group-based licensing**, you must have one of the following:
- Microsoft Entra ID Premium P1 or P2 (trial or paid)
- Office 365 Enterprise E3 or equivalent:
  - Office 365 A3, GCC G3, GCC High E3, DoD E3

![image](https://github.com/user-attachments/assets/70509a39-25ca-456a-9bd8-ee4711536888)

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
