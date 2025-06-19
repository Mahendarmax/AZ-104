# 🔁 Microsoft Entra Application Proxy

Microsoft Entra Application Proxy is a **cloud-based reverse proxy** that allows secure remote access to **internal web applications**—without the need for VPN or firewall changes.

---

## 🌐 What Are Internal Web Apps?

**Internal web apps** are web applications that:
- Are hosted **on-premises** or in a **private network/cloud** (e.g., within Azure VNet)
- Are **not directly accessible over the public internet**
- Typically require LAN, VPN, or proxy access

### 🏠 Examples:
- On-prem SharePoint
- HR portals hosted on internal IIS servers
- ERP or intranet apps inside a datacenter

> ⚠️ These apps are different from SaaS or public cloud apps like Microsoft 365.

---

## ✅ Key Benefits of Application Proxy

- 🌍 **Remote Access** to internal apps from anywhere
- 🔐 **No VPN Required** – Secure without complex networking
- 👤 **Single Sign-On (SSO)** for seamless experience
- 🛡️ **Conditional Access Integration** – Enforce MFA, device compliance, etc.
- ⚙️ **High Availability** using multiple on-prem connectors

---

## ⚙️ Components

| Component                   | Description                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| **Application Proxy Connector** | Installed on-premises; makes outbound connection to Microsoft Entra       |
| **Microsoft Entra ID**          | Authenticates users and enforces access policies                           |
| **User Device**                 | Connects to the app via public Microsoft Entra URL                          |

---

## 🌐 Supported Application Types

- Internal web apps using **HTTP/HTTPS**
- Apps with **Integrated Windows Authentication (IWA)**
- Apps requiring **Kerberos Constrained Delegation (KCD)**

---

## 🔄 How It Works (Access Flow)

1. User requests access via browser
2. Microsoft Entra ID authenticates the user (MFA/SSO/CA policies apply)
3. Application Proxy routes request securely to on-premises connector
4. Connector serves the internal app back to the user

---

## 🏷️ Licensing Requirements

- Requires **Microsoft Entra ID Premium P1 or P2**

---

## 🧪 Exam-Focused Tips

- Use App Proxy to expose internal apps **securely** over the internet
- **No need** to open inbound firewall ports or deploy VPNs
- Integrates with **SSO**, **Conditional Access**, and **Identity Protection**
- Ideal for hybrid organizations needing **cloud-based identity access** to **on-premises apps**

---

> 🔐 Application Proxy bridges the gap between cloud identity and on-premises applications without compromising security.

---