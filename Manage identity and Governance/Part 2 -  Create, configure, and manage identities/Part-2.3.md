# 💻 Configure and Manage Device Registration – Microsoft Entra ID

## 🎯 Goal
Enable secure access for users on both personal (BYOD) and organization-owned devices using Microsoft Entra ID.

---

## 🧾 Device Types

### 1. 🔷 Microsoft Entra Registered Devices
  
![image](https://github.com/user-attachments/assets/49c44995-ed5c-43fd-b499-34f9358d0325)

- **Use case**: BYOD, mobile devices
- **Sign-in**: Local account + Microsoft Entra account
- **Ownership**: User or organization
- **OS support**: Windows 10/11, Android, iOS, macOS
- **Management**: Mobile Device Management (e.g., Intune)
- **Capabilities**: SSO, Conditional Access

> Registered when accessing a work app for the first time or manually through Settings.

---

### 2. 🟢 Microsoft Entra Joined Devices

![image](https://github.com/user-attachments/assets/aa95a8aa-71f2-4194-995b-5bbd1242963c)

devices that are registered directly with Microsoft Entra ID (formerly Azure AD) instead of being joined to a traditional on-premises Active Directory

- **Use case**: Cloud-first or cloud-only organizations
- **Sign-in**: Microsoft Entra account (no local account)
- **Ownership**: Organization
- **OS support**: All Windows 10/11 (except Home edition)
- **Management**: Intune or Configuration Manager (co-management)
- **Capabilities**: SSO (cloud/on-prem), Conditional Access, Self-service Password Reset, Windows Hello PIN reset

> Joined via OOBE, Autopilot, or bulk enrollment.

---

### 3. 🟠 Hybrid Microsoft Entra Joined Devices

![image](https://github.com/user-attachments/assets/c20dc03c-18a5-4600-abcb-a7f8c06fa17a)


- **Use case**: Organizations with on-prem Active Directory + cloud
- **Sign-in**: Active Directory + Microsoft Entra ID
- **Ownership**: Organization
- **OS support**: Windows 7, 8.1, 10, 11, Server 2008–2019
- **Management**: Group Policy, Configuration Manager, Intune (co-management)
- **Capabilities**: SSO (cloud + on-prem), Conditional Access, WHFB PIN reset

> Devices are joined to both on-prem AD and registered in Microsoft Entra ID.

---

## 🔄 Device Writeback (Required for Hybrid Scenarios)

- Syncs device objects from Microsoft Entra ID back to on-prem Active Directory.
- Enables on-prem Conditional Access via ADFS.
- Required for **Windows Hello for Business (WHFB)** in **Hybrid/Federated** environments.

> Device objects appear in the "Registered Devices" container in AD.

---

## 📌 Exam Tips

- **Registered** = BYOD / personal devices  
- **Joined** = Org-owned, cloud-first  
- **Hybrid** = Org-owned with both on-prem + cloud  
- **Device Writeback** is **mandatory** for hybrid Conditional Access & WHFB  

---
