# 👥 Create, Configure, and Manage Groups – Microsoft Entra ID

## Requirements
- Access to the **Microsoft Entra admin center**
- **User Administrator** or higher role

---

## 📌 Purpose of Groups
![image](https://github.com/user-attachments/assets/b49d4a03-f816-4dcf-9367-5f41d8332e96)

Groups in Microsoft Entra ID simplify access management by allowing you to:

- Assign permissions to multiple users at once.
- Define security boundaries.
- Automate membership using user attributes.

---

## 🧱 Group Types in Microsoft Entra ID

### 🔐 Security Groups

- **Purpose**: Control access to **Azure resources**, **applications**, and other secured assets.
- **Use case**: Assign permissions to a VM, storage account, or role assignment.
- **Creation**: Typically created and managed by administrators.
- **Supports**: Assigned or dynamic membership.
- **Does not include**: Shared mailbox, Teams, or SharePoint.

> Best used for **access control and security permissions**.

---

### 📧 Microsoft 365 Groups

- **Purpose**: Designed for **collaboration**.
- **Includes**:
  - Shared mailbox (Exchange)
  - Shared calendar
  - SharePoint document library
  - Planner, OneNote, Teams
- **Use case**: Project teams, departments, or any group needing collaborative tools.
- **Creation**: Can be created by users (if allowed) or admins.
- **Supports**: Assigned or dynamic membership.
- **Can include external users**: Guest access supported.

> Best used when **collaboration tools and shared resources** are needed.

---

## 👤 Membership Types

| Type      | Description                                                                |
|-----------|----------------------------------------------------------------------------|
| Assigned  | Users are **manually added or removed** from the group.                    |
| Dynamic   | Users are added **automatically** based on rules (e.g., department = IT).  |

---

## ⚙️ Dynamic Groups

- Membership is controlled by **rules based on user attributes** (e.g., job title, location).
- Updated **automatically** when user attributes change.
- Available for both **Security** and **Microsoft 365 Groups**.
- Reduces admin overhead for large or changing teams.
![image](https://github.com/user-attachments/assets/924bf422-19e4-4635-bce9-205a0994911e)

> Example rule:  
`(user.department -eq "HR")` → Adds all HR users to the group automatically.

---

## 🔍 View Existing Groups

1. Go to the **Microsoft Entra admin center**.
2. Under **Identity**, select **Groups**.
3. View or filter by **group type** and **membership type**.

---
