# AZ-104: Plan Virtual Networks

## Overview
This module focuses on designing and planning Azure Virtual Networks (VNets), which are foundational to Azure infrastructure deployment. It covers VNet characteristics, common scenarios, and best practices for configuration.


![image](https://github.com/user-attachments/assets/26b5c050-960a-4ac0-ac87-f28f339f511b)


---

## 🔹 Key Concepts

- **Azure Virtual Network (VNet)** is a logical isolation of Azure resources within your subscription.
- Enables secure communication between:
  - Azure resources
  - On-premises infrastructure
  - Internet (when needed)
- VNets use **CIDR (Classless Inter-Domain Routing)** for IP address allocation.
- Custom **DNS server** settings can be applied.
- VNets can be segmented into **subnets** for traffic control and isolation.

---

## 🔄 Connectivity Options

- **VNet Peering**: Connects VNets within the same or different regions. CIDR blocks must not overlap.
- **Site-to-Site VPN**: Connects Azure to on-premises networks using **IPSec** encryption.
- **ExpressRoute**: Private dedicated connection between Azure and on-prem datacenter.

---

## 🔧 Common Scenarios

### 1. Cloud-Only VNet
- No on-premises dependency.
- Internal communication between services.
- External access via endpoints if needed.

### 2. Extend On-Premises Network
- Use **Site-to-Site VPN** to securely expand datacenter to Azure.
- Scalable and secure cloud integration.

### 3. Hybrid Cloud
- Integrate cloud applications with legacy systems like UNIX/mainframes.
- Supports complex enterprise-grade environments.

---

## 📝 Planning Considerations

- Ensure **non-overlapping IP ranges** to avoid routing conflicts.
- Define **subnets** based on resource types or roles.
- Use **Network Security Groups (NSGs)** to control inbound/outbound traffic.
- Choose between **Azure DNS** or **custom DNS**.
- Apply **user-defined routes (UDRs)** where custom routing is needed.

---

## 📌 Quick Exam Tips

- Understand VNet peering and hybrid networking (VPN vs ExpressRoute).
- Know how to configure and segment subnets.
- Familiar with NSG rules and their application at subnet and NIC level.
- Plan address spaces to support scaling and connectivity.

---

