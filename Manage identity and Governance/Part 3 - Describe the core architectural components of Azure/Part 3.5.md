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

Management Group
│
├── Subscription A
│   └── Resource Group A1
│       └── Resources
└── Subscription B
    └── Resource Group B1
        └── Resources

---
