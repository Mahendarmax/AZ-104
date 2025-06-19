
---

🧩 Microsoft Entra Domain Services

 ![image](https://github.com/user-attachments/assets/2cfe118e-1a66-4152-b5d1-5ad4ac90e1e0)

how an **on-premises user** accesses a **legacy application hosted in Azure**, using **Microsoft Entra Domain Services (Azure AD DS)**.

## 🔁 Step-by-Step Flow

### 1. 🧑‍💼 On-Prem User Device
- The user logs in from a **domain-joined PC or laptop**
- Example: An HR user trying to access a legacy HR application

### 2. 🌐 VPN / ExpressRoute
- The user's device is connected to Azure through a **secure channel**:
  - 🔒 VPN connection, or  
  - ⚡ Azure ExpressRoute (private, high-speed connection)
- This allows communication between on-prem devices and Azure resources

### 3. 🖧 Azure Virtual Network (VNet)
- A **private network in Azure** where your app and VM live
- Works like an on-premises network, but in the cloud

### 4. 🖥️ Legacy App VM
- The legacy application is hosted on a **Windows VM in Azure**
- This VM is **domain-joined to Microsoft Entra Domain Services**

### 5. 🔐 Authentication via Microsoft Entra Domain Services
- The VM authenticates the user using **Kerberos or NTLM**
- **Microsoft Entra Domain Services (Azure AD DS)** handles authentication  
  - No need to deploy domain controllers yourself
  - Supports **LDAP**, **Group Policy**, and **classic Windows auth**

### 6. 🧠 Microsoft Entra ID (Azure AD)
- Acts as the **identity source** for the organization
- On-premises users are **synced** to Entra ID using **Microsoft Entra Connect**
- Entra ID passes identities to **Entra Domain Services**

## ✅ Summary Table

| Component                        | Role/Purpose                                               |
|----------------------------------|-------------------------------------------------------------|
| On-Prem User Device              | Source device (e.g., user PC)                              |
| VPN / ExpressRoute               | Secure connection to Azure                                 |
| Azure Virtual Network (VNet)     | Hosts the VM and app in a private Azure network            |
| Legacy App VM                    | App requiring domain join and Kerberos auth                |
| Microsoft Entra Domain Services  | Authenticates using Kerberos/NTLM; provides LDAP/GPO       |
| Microsoft Entra ID (Azure AD)    | Central identity source, synced from on-prem via Entra Connect |

---

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
