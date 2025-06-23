# 🛠️ Azure Management Infrastructure Overview

Azure management infrastructure helps you organize and control access to resources using a **hierarchical structure** of:

> Management Groups → Subscriptions → Resource Groups → Resources

---

## 📦 Azure Resources & Resource Groups

- **Resource**: Basic unit in Azure (e.g., VM, Storage, Database, etc.)
- **Resource Group**:
  - Logical container for multiple resources
  - One resource can only belong to **one resource group**
  - Deleting a resource group deletes all its resources
  - Cannot be nested inside another resource group
  - Used for organizing, managing access, and clean-up

---

## 📃 Azure Subscriptions

- **Subscription**: Unit for **billing**, **authentication**, and **access control**
- Required to **provision resources**
- Linked to an Azure account (identity in Microsoft Entra ID)

### 🧱 Subscription Boundaries
- **Billing boundary**: Separate costs and invoices
- **Access control boundary**: Assign roles and policies per subscription

### 📊 Use Cases for Multiple Subscriptions
- **Environment separation**: e.g., Dev, Test, Prod
- **Organizational separation**: Different teams/departments
- **Billing separation**: Track costs per project/team

---

## 🏢 Azure Management Groups

- Provide a **level above subscriptions**
- Group **multiple subscriptions** for unified governance
- Support **policy enforcement** and **access control**
- Policies and access settings are **inherited** by child subscriptions and resources
---
---
### 🌲 Hierarchy Example
![image](https://github.com/user-attachments/assets/cb16715c-0183-469c-8950-1cb48fe8a408)


---

## ✅ Key Facts

- Maximum **10,000** management groups per directory  
- Maximum **6 levels deep** (excluding root and subscriptions)  
- Each **management group or subscription** can have **only one parent**

---

## 🎯 Use Case Examples

- **Enforce governance**:  
  Apply policies at the management group level (e.g., restrict VM deployments to specific regions)

- **Simplify access**:  
  Assign a single Azure RBAC role to a management group to grant access across all child subscriptions and resources

---
---
## 📌 Summary

| **Component**       | **Purpose**                                      |
|---------------------|--------------------------------------------------|
| `Resource`          | Actual Azure service you create/use              |
| `Resource Group`    | Logical grouping of resources                    |
| `Subscription`      | Unit for billing, access, and deployment         |
| `Management Group`  | Governance across multiple subscriptions         |

---
