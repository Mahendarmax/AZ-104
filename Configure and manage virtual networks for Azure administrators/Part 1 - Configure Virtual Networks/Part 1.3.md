# 📘 Plan IP Addressing – Azure Virtual Networks

## 🧾 Module Summary
Learn how to plan IP addressing in Azure by understanding the types of IP addresses, their assignment methods, and usage scenarios. Proper IP planning ensures seamless connectivity between Azure resources, on-premises networks, and the internet.

---

## 🔗 Key Concepts

### 1. IP Address Types
Azure supports two types of IP addresses:

| Type        | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| **Private** | Used for internal communication within a VNet or on-premises (via VPN/ER). |
| **Public**  | Used for communication with the internet.                                   |

---

### 2. Private IP Addresses
- Enable communication **within** Azure virtual networks and **on-premises** networks.
- **Not accessible from the internet.**
- Used by backend services, databases, internal VMs.
- Assigned to network interfaces (NICs), load balancers, and private endpoints.

---

### 3. Public IP Addresses
- Allow **internet communication**.
- Can be assigned to:
  - Azure Virtual Machines
  - Application Gateways
  - Azure Load Balancers
  - VPN Gateways

- **SKUs:**
  - **Basic** – Not zone resilient, no SLA.
  - **Standard** – Zone resilient, secure by default.

---

### 4. IP Assignment Types

| Assignment Type | Description                                   | Use Cases                                                                 |
|------------------|-----------------------------------------------|---------------------------------------------------------------------------|
| **Dynamic**      | Assigned automatically by Azure DHCP          | General-purpose workloads, where IP change is acceptable                 |
| **Static**       | Manually assigned and remains constant        | DNS records, Firewall rules, Role-based VMs like DCs and DNS servers     |

- Static IPs must be reserved within the subnet's address range.
- Static IPs ensure consistency for:
  - TLS/SSL certificates
  - IP-based security models
  - DNS mappings

---

## 🧠 Best Practices & Use Cases

### 🔐 Use Static IPs When:
- DNS resolution depends on a fixed IP.
- IP-based firewall or NSG rules are in place.
- Certificate bindings are IP-specific.
- Role-based workloads require fixed identities.

### 🗂 Separate Subnets for:
- Static IP resources
- Dynamic IP resources

This promotes clarity and management efficiency.

---

## 📌 Planning Considerations

- Ensure IP address spaces are non-overlapping across VNets and on-prem.
- Choose between **IPv4** and **IPv6** support as per workload.
- Reserve ranges for future subnetting.
- Plan for hybrid scenarios: VPN and ExpressRoute need private IPs.

---

## 📚 Related Learning
- [Design an IP addressing schema for your Azure deployment](https://learn.microsoft.com/en-us/training/modules/design-ip-addressing-schema/)

Includes hands-on sandbox to practice IP planning in real Azure environments.

---

## 📝 Exam Tips

- Know **when to use Public vs. Private IPs**.
- Static IPs are **required** for:
  - DNS consistency
  - TLS/SSL binding
  - Role-based services
- Understand **Standard vs. Basic Public IP** differences.
- Plan address space to **avoid overlap** with on-prem networks.

---

## 🛠 Example Use Case Diagram

[Virtual Machine]
|
|--> 🔒 Private IP --> 🗄️ Internal Database (within VNet)
|
└--> 🌐 Public IP --> 🌍 Internet (external access)

yaml
Copy
Edit
