# 🛡️ Implement Network Security Groups (NSGs) in Azure

> **Module:** Implement network security groups  
> **XP Earned:** 100 XP  
> **Completion Time:** 4 minutes

---

## 📘 Overview

A **Network Security Group (NSG)** is a core component in Azure used to filter **network traffic to and from Azure resources**. NSGs contain security rules that allow or deny traffic based on various conditions such as source/destination IP, port, and protocol.

---

## 🔐 Key Concepts

### ✅ What is a Network Security Group?
- A **Network Security Group** is a set of security rules that control **inbound and outbound traffic**.
- NSGs can be associated with:
  - **Subnets**
  - **Network Interfaces (NICs)**
- NSGs help create **layered security** for resources inside a virtual network.

---

## 📍 NSG Rule Characteristics

| Feature                  | Description                                                 |
|--------------------------|-------------------------------------------------------------|
| Inbound/Outbound Rules   | Allow or deny traffic based on defined criteria             |
| Multiple Associations    | An NSG can be **associated multiple times**                 |
| Management               | Created and managed via the **Azure portal**                |
| Visibility               | VM Overview page shows NSG associations and rule details    |

---

## 🌐 NSGs with Subnets

- NSGs **can be assigned to a subnet** to secure all resources within that subnet.
- Used to implement **screened subnets (DMZ)** for controlling external access.
- **Only one NSG can be associated** per subnet.
- Traffic restrictions apply to **all machines** within the subnet.

---

## 🔌 NSGs with Network Interfaces (NICs)

- NSGs can be assigned **individually to a NIC**.
- Each NIC in a subnet can have **zero or one NSG associated**.
- Rules applied at the NIC level allow fine-grained control of traffic to individual VMs.

---

## 🧠 Exam Tips

- 📝 **NSG scope**: Subnet-level NSGs affect all resources in the subnet. NIC-level NSGs apply specifically to the VM.
- 📌 **Only one NSG per subnet/NIC**, but an NSG can be reused across different subnets or NICs.
- 🔍 Use the **VM overview page** to inspect which NSGs are applied and review their rules.
- 🚫 Use NSGs in a **DMZ architecture** to limit inbound traffic from the internet while allowing internal traffic.
- 🛑 **Default rules** exist in every NSG — custom rules take priority over default ones if there's a match.

---

## 📊 Diagram

```text
[Internet]
   |
   v
[NSG - DMZ Subnet]
   |
   v
[Web Server VM] <-- NSG applied at NIC level (optional)
   |
   v
[Backend Subnet] <-- NSG restricts internal access
   |
   v
[Database VM]

```

### Additional importent information

# Azure Subnet Design: Frontend vs Backend

## 🔹 What is a Subnet?
A **Subnet** is a range of IP addresses within a Virtual Network (VNet). It helps organize and secure resources logically.

---

## 🧩 Subnet Types in Architecture

### ✅ Frontend Subnet
- **Purpose**: Hosts resources that interact with users or the public.
- **Examples**:
  - Web servers (e.g., IIS, NGINX)
  - Load balancers
  - Application Gateways
- **Access**:
  - Requires **inbound access** (usually via public IP or Application Gateway)
- **Network Security**:
  - NSGs allow HTTP/HTTPS from the internet

---

### ✅ Backend Subnet
- **Purpose**: Hosts internal components not exposed to the internet.
- **Examples**:
  - Databases (SQL, CosmosDB)
  - Internal APIs
  - App services
- **Access**:
  - Only from frontend subnet or trusted networks (via private IP)
- **Network Security**:
  - NSGs deny public access, allow traffic only from frontend or specific IP ranges

---

## 📐 Typical Network Diagram

