
---

## 🧩 Microsoft Entra Domain Services

![image](https://github.com/user-attachments/assets/e56ab0c1-10f2-4d70-976b-f9974f7f83c8)

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

## 🔹 Alternatives Without Microsoft Entra Domain Services

1. **Site-to-site VPN** between on-premises and Azure IaaS  
   - Authentication traffic crosses the VPN  

2. **Replica domain controllers** deployed in Azure  
   - Replication crosses the VPN, but authentication stays in the cloud  

> ⚠️ Both methods add complexity, cost, and administrative overhead.

---

## 🔹 Licensing and Enablement

- Enabled via **Azure Portal**  
- Billed hourly (pay-as-you-go) based on **directory size**  
- Requires **Microsoft Entra ID P1 or P2 license**

---

## 🔹 Integration with On-Premises AD (Optional)

- Use **Microsoft Entra Connect** to sync user identities  
- Allows users to use **the same credentials** in both on-prem AD and Entra DS

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

## When to use both

Use **Microsoft Entra ID** for **modern applications and secure identity** management.  
Use **Microsoft Entra Domain Services** when **legacy systems** require **domain join** or traditional **Kerberos/LDAP protocols**.

---
---
## 🖥️ What is Domain Join (Short)

🧠 **Domain Join** connects a **Windows device** (PC or VM) to a **central directory** (like **Active Directory** or **Microsoft Entra Domain Services**) so it can:

- ✅ Be **centrally managed**
- ✅ Use **domain credentials** to log in
- ✅ Receive and apply **Group Policies**
- ✅ Access **shared network resources** (like drives, printers, internal apps)

---
