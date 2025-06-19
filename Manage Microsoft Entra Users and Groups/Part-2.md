---
# 🧩 Microsoft Entra Domain Services

![image](https://github.com/user-attachments/assets/e56ab0c1-10f2-4d70-976b-f9974f7f83c8)

Microsoft Entra Domain Services (formerly Azure AD DS) allows organizations to use domain services like **Kerberos**, **NTLM**, and **Group Policy** in Azure — **without deploying domain controllers**.
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
   - **DNS domain name** (e.g., corp.contoso.com)
   - **Virtual Network** (same VNet as your VMs)
   - **Resource group**
5. Review and click **Create**

> ⏱️ Setup takes **30–90 minutes** to complete the initial deployment.

---

---
### 🔹 Purpose and Use Case

- Enables **domain-join, LDAP, NTLM, and Kerberos authentication** in Azure  
- Ideal for **migrating LOB applications** that rely on domain authentication  
- Requires **no deployment of on-prem or cloud-based domain controllers**  
- Fully **compatible with traditional AD DS**

---

### 🔹 Alternatives Without Microsoft Entra Domain Services

1. **Site-to-site VPN** between on-premises and Azure IaaS  
   - Authentication traffic crosses the VPN  

2. **Replica domain controllers** deployed in Azure  
   - Replication crosses the VPN, but authentication stays in the cloud  

> ⚠️ Both methods add complexity, cost, and administrative overhead.

---

---

### 🔹 Licensing and Enablement

- Enabled via **Azure Portal**  
- Billed hourly (pay-as-you-go) based on **directory size**  
- Requires **Microsoft Entra ID P1 or P2 license**

---

### 🔹 Integration with On-Premises AD (Optional)

- Use **Microsoft Entra Connect** to sync user identities  
- Allows users to use **the same credentials** in both on-prem AD and Entra DS

---

> 📌 **Exam Tip**:  
> Microsoft Entra Domain Services is the best option for running legacy apps in Azure **without setting up and managing domain controllers or VPNs**.
---
