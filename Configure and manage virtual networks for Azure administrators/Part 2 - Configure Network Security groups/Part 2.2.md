# 📋 Determine Network Security Group (NSG) Rules

## 🔐 Overview

**NSG rules** are used to filter **inbound and outbound network traffic** in Azure. These rules define the **flow of traffic** to and from resources in a **subnet** or **network interface (NIC)**.

Each **NSG** comes with **default rules** created by Azure, but **custom rules** can be added to fine-tune security.

---

## 📌 Default Security Rules (Auto-created by Azure)

<img width="883" height="257" alt="image" src="https://github.com/user-attachments/assets/5cf6ec34-9934-4777-86e7-f9054735d86c" />

<img width="891" height="246" alt="image" src="https://github.com/user-attachments/assets/2aabb353-1dae-4a1d-8fab-74f41cbf3479" />

```text

| Direction | Rule Name                | Action | Purpose                                                                 |
|-----------|--------------------------|--------|-------------------------------------------------------------------------|
| Inbound   | AllowVNetInBound         | Allow  | Allows traffic from within the same VNet                                |
| Inbound   | AllowAzureLoadBalancerIn| Allow  | Allows traffic from Azure load balancer                                 |
| Inbound   | DenyAllInbound           | Deny   | Denies all other inbound traffic                                        |
| Outbound  | AllowVNetOutBound        | Allow  | Allows traffic to the same VNet                                         |
| Outbound  | AllowInternetOutBound    | Allow  | Allows outbound traffic to the internet                                 |
| Outbound  | DenyAllOutBound          | Deny   | Denies all other outbound traffic                                       |

> ⚠️ **Note:** Default rules **cannot be deleted** but **can be overridden** by a custom rule with a **higher priority** (lower priority number).

```
---

## ⚙️ Custom Rule Parameters


| Setting              | Values/Details                                                                 |
|----------------------|---------------------------------------------------------------------------------|
| **Source**           | `Any`, `IP address`, `My IP`, `Service Tag`, `Application Security Group`     |
| **Source Port Range**| Specific port number or range                                                  |
| **Destination**      | `Any`, `IP address`, `Service Tag`, `Application Security Group`              |
| **Destination Port** | Specific port number or range                                                  |
| **Protocol**         | `Any`, `TCP`, `UDP`, `ICMP`                                                   |
| **Action**           | `Allow` or `Deny`                                                              |
| **Priority**         | Integer between **100–4096** (lower value = higher priority)                  |
| **Direction**        | `Inbound` or `Outbound`                                                       |

> ✅ **Processing Order**: NSG rules are processed **in order of ascending priority**. Once a match is found, further rules are ignored.

---

## 🧠 Exam Tips

- 🔁 **Default NSG rules are always present** — DenyAllInbound and AllowInternetOutbound are critical ones to remember.
- 🛑 **You cannot delete default rules**, but **you can override them** with a rule that has a **lower priority value** (higher precedence).
- 🧩 **Security rules apply independently** for inbound and outbound directions.
- 📊 **Priorities must be unique** within the same NSG.
- 🎯 Custom rules are useful to allow traffic like SSH (port 22), RDP (port 3389), or block specific IPs.

---

## 🖼️ Conceptual Diagram

```text
             [Internet]
                 |
     ----------------------------
     |         NSG Rules         |
     ----------------------------
     | Priority | Action | Port |
     |   100    | Deny   | 3389 | <- Custom Rule (High Priority)
     |  65000   | Allow  | VNet | <- Default Rule
     |  65500   | Deny   | All  | <- Default Rule
     ----------------------------
                 |
             [VM/NIC]

```
