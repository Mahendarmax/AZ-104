# ✍️ Create Network Security Group (NSG) Rules



## 🔐 Overview

Azure lets you easily **create security rules** in a **Network Security Group (NSG)** to control **inbound and outbound traffic**. You can configure these rules in the **Azure portal** using predefined service templates or custom values.

---

## 🔧 Rule Configuration Properties

To create a rule, you must configure the following settings:

<img width="368" height="334" alt="image" src="https://github.com/user-attachments/assets/70f5917c-4799-4ff3-92ef-dcd35f9a59f2" />




| Property     | Description                                                                 |
|--------------|-----------------------------------------------------------------------------|
| **Source**   | Defines the **origin** of the traffic (e.g., IP range, Service Tag, ASG)    |
| **Destination**| Defines the **target** of the traffic (e.g., IP range, Service Tag, ASG)  |
| **Service**  | Specifies **protocol + port range** (e.g., TCP:443 for HTTPS, TCP:3389 for RDP) |
| **Priority** | Rule execution order (value from **100–4096**; lower = higher precedence)   |
| **Action**   | Choose to **Allow** or **Deny** traffic                                     |

> ℹ️ You can also choose predefined services like **HTTPS**, **RDP**, **FTP**, **SSH**, or enter **custom ports**.

---

## 🧠 Key Concepts

- ✅ **Source/Destination** can be:
  - An IP range (e.g., `192.168.1.0/24`)
  - A **Service Tag** (e.g., `Internet`, `VirtualNetwork`)
  - An **Application Security Group (ASG)**
  - `Any`

- 📡 **Service (Port + Protocol)**:

<img width="244" height="203" alt="image" src="https://github.com/user-attachments/assets/4d444b13-38ef-4b21-bbbf-cad4136917a9" />


  - Can be **predefined** (RDP, SSH, HTTPS, etc.)
  - Or defined manually (e.g., TCP:8080, UDP:53)

- 🔢 **Priority**:

<img width="369" height="136" alt="image" src="https://github.com/user-attachments/assets/d5f3904a-e6ef-4fcb-9cdd-716270c0e541" />



  - **Lower number = higher priority**
  - Use priority gaps like `100`, `200`, `300` for future expansion

- 🚦 **Action**:
  - `Allow` – Permit traffic
  - `Deny` – Block traffic

---

## 📊 Example Rule Configuration

```text
Allow HTTPS Traffic from Internet to Web VM
-------------------------------------------
Source      : Internet (Service Tag)
Destination : 10.0.1.4 (Web VM IP)
Service     : HTTPS (TCP:443)
Priority    : 200
Action      : Allow
Direction   : Inbound

```

🧠 Exam Tips
🛠️ Custom vs. Predefined Services: You can use either, depending on your use case.

🔀 Rules are processed in priority order. First match wins — further rules are ignored.

🔒 Deny by default: If no rule matches, traffic is denied.

📍 Configure rules at the correct scope (subnet or NIC) for precision.

📊 Always review effective security rules post-creation for validation.
