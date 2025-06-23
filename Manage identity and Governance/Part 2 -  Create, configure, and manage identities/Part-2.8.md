# 🔄 Automatic User Provisioning in Microsoft Entra ID

Automatic provisioning enables seamless user and group lifecycle management between Microsoft Entra ID and external systems like HR platforms, using the SCIM protocol.
![image](https://github.com/user-attachments/assets/11aae352-49af-4488-97c4-989dc04f128c)

---

## 🎯 Exact Use (In Short)

- 🔄 **Automate Account Management:** Automatically create, update, and delete users and groups in connected systems.
- 🔗 **Sync with HR Systems:** Link your HCM (HR software) with Microsoft Entra ID using SCIM 2.0.
- 🔐 **Improve Security:** Immediate deprovisioning reduces insider threat risks when employees leave.
- 🧩 **Standard-Based Integration:** Uses SCIM (an open standard) for consistent identity management across platforms.

---

## ⚙️ Key Components of SCIM-Based Provisioning

| Component                         | Description                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
| 🧑‍💼 **HCM System**                | Manages employee lifecycle (e.g., Workday, SAP SuccessFactors)             |
| 🔁 **Microsoft Entra Provisioning Service** | Uses SCIM 2.0 to sync identities with target applications                   |
| 🧾 **Microsoft Entra ID**         | Source identity directory (user repository)                                |
| 🎯 **Target System**              | Application with SCIM endpoint where users/groups are provisioned          |

---

## ❓ Why Use SCIM?

- SCIM (**System for Cross-Domain Identity Management**) is an **open standard** for automating the exchange of identity data.
- Ensures:
  - 🟢 New hires in the HCM system are provisioned automatically in Entra ID.
  - 📝 Attributes like role, email, and department are synced.
  - 🔴 Terminated users are deprovisioned quickly to reduce security risk.

---

## 🔄 How It Works (High-Level Flow)

1. Employee joins the company and is added in the HCM system.
2. Microsoft Entra Provisioning Service picks up the change using SCIM.
3. A new user is created in Microsoft Entra ID and assigned appropriate roles/groups.
4. Any updates (like department change) sync automatically.
5. When the employee leaves, the record is removed from HCM → Entra ID deprovisions access.

---

## 📘 Exam Tip

> SCIM-based provisioning in Microsoft Entra ID is ideal for **HR-driven identity lifecycle management**.  
> Always associate it with **automated user creation, update, and deprovisioning** across systems using **SCIM 2.0**.

---
