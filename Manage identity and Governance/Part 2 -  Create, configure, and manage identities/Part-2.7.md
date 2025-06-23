# 🛡️ Custom Security Attributes in Microsoft Entra ID

Custom security attributes are **business-specific key-value pairs** assigned to Microsoft Entra objects (like users, apps, or resources).  
They are primarily used for **Attribute-Based Access Control (ABAC)** and storing organization-specific metadata.

---

## 🎯 Exact Use (In Short)

- 🔐 **ABAC (Attribute-Based Access Control):** Grant or restrict access to Azure resources based on attribute values.
- 🧾 **Enhance Profiles:** Store custom data like hire date, salary, or department.
- 🔍 **Filter & Manage:** Easily filter users/apps/resources for automation, audits, and reporting.
- 🔒 **Visibility Control:** Restrict who can view or set sensitive attributes.
- 🔄 **Hybrid Sync:** Sync custom attributes from on-prem AD to Microsoft Entra ID.

---

## ✅ What Are Custom Security Attributes?

- Custom attributes defined by your organization.
- Used to store metadata on Entra ID objects (e.g., `EmployeeHireDate`, `HourlySalary`).
- Provide additional context for identity-based access and filtering.

---

## 🎯 Why Use Custom Security Attributes?

- 📌 Extend user profiles with organization-specific metadata.
- 🔒 Restrict sensitive attribute visibility (e.g., only admins can view salary).
- 📂 Categorize thousands of applications for auditing and filtering.
- 🔐 Grant access to Azure resources based on attributes (e.g., project access to storage blobs).

---

## 🧰 What Can You Do with Them?

- Define custom business attributes across your tenant.
- Assign them to:
  - Users
  - Applications
  - Microsoft Entra resources
  - Azure resources
- Use them in filters and queries to manage Entra objects.
- Enable **Attribute-Based Access Control (ABAC)** scenarios.
- Govern access based on attribute values.

---

## 🧾 Key Features

| Feature              | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| 🌐 Tenant-Wide        | Usable across the entire Microsoft Entra tenant                            |
| 📄 Descriptions       | Each attribute can have a meaningful description                           |
| 🔢 Data Types         | Supports `String`, `Integer`, and `Boolean`                                |
| 🔁 Value Options      | Can be configured as single-value or multi-value                           |
| 📝 Value Input        | Accepts user-defined (free-form) or predefined values                      |
| 🔄 Sync Support       | Can be assigned to directory-synced users from on-premises Active Directory |

---

## 🧪 Example Use Cases (Exam Tip)

- Extend HR data like hire date or salary into Entra profiles.
- Implement access control policies for cloud resources using attribute filters.
- Organize apps into logical groups for audit or automation purposes.

---

## 📘 Exam Tip

> **Custom security attributes** are a foundation for **Attribute-Based Access Control (ABAC)** in Microsoft Entra ID.  
> Use them to drive **contextual, policy-based decisions** for secure access control beyond traditional roles.

---
