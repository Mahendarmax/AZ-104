# 🔒 What is Azure RBAC? — Exam-Focused Notes

![image](https://github.com/user-attachments/assets/8b91a011-658f-4158-808d-8d514be23136 width="500" )


## 📌 Core Cloud Identity & Access Concerns
- ✅ Ensure **access is revoked** when people leave the organization.
- ✅ Balance between **team autonomy** and **central governance**.
- ✅ Use **Microsoft Entra ID + Azure RBAC** to implement secure access strategies.

---

## 📁 Azure Subscriptions and Identity
- An **Azure subscription** is linked to **one Microsoft Entra tenant**.
- Users, groups, and apps from this tenant can manage resources.
- **Azure uses Entra ID** for:
  - Single Sign-On (SSO)
  - Centralized access management
- **Microsoft Entra Connect** syncs on-prem AD with Azure.
  - Disabling an AD account revokes cloud access automatically.

---

## 🎯 What is Azure RBAC?

- **Azure RBAC = Authorization system** on Azure Resource Manager.
- Provides **fine-grained, role-based access** to Azure resources.
- Examples:
  - One user manages VMs.
  - Another manages SQL DBs—within same subscription.
- Role assignments apply at various **scopes**:
  - Management Group → Subscription → Resource Group → Resource
- **Parent → Child scope inheritance** applies (e.g., Subscription → RG → Resource).

---

## 🔧 Azure RBAC – Use Cases

Use Azure RBAC to:
- Allow one user to manage VMs, another to manage networks.
- Let DB admins manage SQL databases only.
- Allow full control over a **single Resource Group**.
- Let an **application** access specific resources only.

---

## 🧭 Access Control (IAM) in Portal
- IAM = **Access Control pane** in the Azure Portal.
- See:
  - Who has access
  - What roles are assigned
- You can also assign or remove roles here.

---

## ⚙️ How Azure RBAC Works

### 1️⃣ Security Principal (Who?)
- The **identity** you're granting access to:
  - 👤 User
  - 👥 Group
  - 🤖 Service Principal (application)

---

### 2️⃣ Role Definition (What?)
- Set of **permissions** granted (aka **role**).
- Roles specify **read**, **write**, **delete**, etc.

#### 🏗️ Common Built-In Roles:
| Role | Capabilities |
|------|--------------|
| Owner | Full control incl. access delegation |
| Contributor | Manage resources, no access delegation |
| Reader | View resources only |
| User Access Administrator | Manage user access only |

- You can also create **custom roles** if needed.

---

### 3️⃣ Scope (Where?)
- The **level** at which access is applied:
  - Management Group
  - Subscription
  - Resource Group
  - Resource
- **Scopes are hierarchical**:
  - Permissions assigned at higher levels are inherited by lower levels.

---

## 🔗 Role Assignment (Who + What + Where)
- Binding of **security principal** + **role** + **scope** = Access.
- To **grant access** → Create a role assignment.
- To **revoke access** → Remove the assignment.

📝 Example:
- Group: `Marketing`
- Role: `Contributor`
- Scope: `Sales Resource Group`

---

## 🚫 Azure RBAC = Allow Model
- Role grants allow specific actions: read/write/delete.
- If multiple roles apply → **Permissions are additive**.
- 🔍 NotActions can **exclude** certain permissions from a role:
  - Example: `Contributor` allows all `Actions` *except*:
    - Deleting roles/assignments
    - Managing blueprint artifacts
    - Granting access at tenant scope

---

📌 **EXAM TIPS**
- ✅ RBAC ≠ Authentication → Only handles authorization.
- ✅ Roles are cumulative (more than one role = union of permissions).
- ✅ Inheritance is automatic down the scope tree.
- ✅ Use **least privilege principle** while assigning roles.

