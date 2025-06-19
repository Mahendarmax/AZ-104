
---

🧩 Microsoft Entra Domain Services

   ┌─────────────────────┐
   │ On-Prem User Device │
   │ (AD Joined, HR User)│
   └─────────┬───────────┘
             │
             ▼ VPN / ExpressRoute
   ┌────────────────────────────┐
   │ Azure Virtual Network      │
   │ (VNet)                     │
   │   ┌─────────────────────┐  │
   │   │ Legacy App VM       │  │
   │   │ (Domain-joined to   │  │
   │   │  Entra DS)          │  │
   │   └─────────────────────┘  │
   └────────────┬──────────────┘
                ▼ Auth using Kerberos/NTLM
   ┌──────────────────────────────────────┐
   │ Microsoft Entra Domain Services      │
   │ (Azure AD DS)                        │
   │ - Provides Kerberos, LDAP            │
   └────────────┬─────────────────────────┘
                ▼
   ┌──────────────────────────────────────┐
   │ Microsoft Entra ID                  │
   │ (Azure AD – Identity Source)        │
   │ Synced via Entra Connect            │
   └──────────────────────────────────────┘


---

## 🏛️ Hosting Legacy Applications in Azure

If you're hosting a **legacy application in Azure** that depends on traditional Active Directory features like:

- ✅ **Domain Join**
- ✅ **Kerberos / NTLM authentication**
- ✅ **Group Policy (GPO)**
- ✅ **LDAP access**

Then **Microsoft Entra Domain Services (Azure AD DS)** is the ideal solution — because it **provides these features without requiring on-prem domain controllers**.

---

## 🔄 Solution Architecture (Simple Path)

### 🔗 Step 1: Set Up Microsoft Entra Connect

- Sync on-premises users to **Microsoft Entra ID**
- These users automatically become visible in **Microsoft Entra Domain Services**

### 🌐 Step 2: Provide Network Access

- Set up **VPN** or **ExpressRoute** from on-premises to Azure  
- This allows on-prem users to securely access the Azure-hosted app

### 🔐 Step 3: Authentication Flow

- On-prem user logs in from their domain-joined device  
- The legacy app (hosted on an Azure VM) is **domain-joined to Entra Domain Services**
- The app authenticates the user via **Kerberos / NTLM**, using synced credentials

---

## ✅ Result

- No need for domain controllers in Azure  
- Legacy apps work with traditional protocols  
- Users can securely authenticate using existing credentials  
- Centralized identity management through **Microsoft Entra ID**

---



---

## 📦 Real-World Example

**Scenario**:  
Contoso Ltd. has an **old HR application** that only works if the machine is **domain-joined** and uses **Kerberos authentication** to log in.

### 🛠️ Instead of:

- Setting up a **domain controller VM** in Azure  
- Managing **replication**, **updates**, and **DNS** manually  

### ✅ They do this:

- Enable **Microsoft Entra Domain Services** via Azure Portal  
- Join the Azure VM to this **managed domain** (not on-prem AD)  
- Run the HR app securely — no extra servers or manual domain setup needed

> 🧠 **Note**: The VM is **not joined to on-premises Active Directory**.  
> It is joined to the **Microsoft Entra Domain Services domain**, which is fully managed and hosted in Azure.

---

## 🚀 Where to Enable It

You can enable **Microsoft Entra Domain Services** in the **Azure Portal**:

### 🔹 Steps:

1. Go to [https://portal.azure.com](https://portal.azure.com)
2. Search for **Microsoft Entra Domain Services**
3. Click **+ Create**
4. Provide:
   - **DNS domain name** (e.g., `corp.contoso.com`)
   - **Virtual Network** (same VNet as your VMs)
   - **Resource group**
5. Review and click **Create**

> ⏱️ Setup takes **30–90 minutes** to complete the initial deployment.

---


---

## 🧠 Easy Analogy

| Entra ID                                 | Entra Domain Services                                          |
|------------------------------------------|----------------------------------------------------------------|
| Like a **cloud phonebook** for apps      | Like a **classic domain controller**, but fully managed in Azure |
| **Identity-focused**                     | **Domain service–focused**                                     |
| Used for **SSO, MFA, access control**    | Used for **apps needing Kerberos, NTLM, LDAP, domain join**    |

---

---
## 🖥️ What is Domain Join (Short)

🧠 Domain Join is the process of registering a device (usually Windows) into a domain, so that it becomes part of a managed environment controlled by Active Directory (on-prem or Entra Domain Services in Azure).

- ✅ Be **centrally managed**
- ✅ Use **domain credentials** to log in
- ✅ Receive and apply **Group Policies**
- ✅ Access **shared network resources** (like drives, printers, internal apps)

---
