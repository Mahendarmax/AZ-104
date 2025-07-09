# 🌐 Create Subnets in Azure - Exam Notes

## 🎯 Goal:
Segment a virtual network (VNet) into logical subnets for improved **security**, **performance**, and **management**.

---

## 📘 Key Facts About Azure Subnets

- Each **subnet** is a **subset of the VNet address space**
- Subnet address ranges must be:
  - ✅ Unique within the VNet
  - ❌ Must not **overlap** with other subnets
  - ✅ Specified using **CIDR notation** (e.g., `192.168.1.0/24`)

---

## 🔒 Reserved IP Addresses in Each Subnet (`/24` example)

| IP Address        | Purpose                                 |
|-------------------|------------------------------------------|
| `192.168.1.0`     | Network identifier                       |
| `192.168.1.1`     | Default **gateway**                      |
| `192.168.1.2-1.3` | **Azure DNS** IPs mapped to the VNet     |
| `192.168.1.255`   | **Broadcast address**                    |

> 📌 Total 5 addresses are reserved in each subnet.

---

## 📐 Design Considerations

### 1. **Service Requirements**
- Some Azure services (like **VPN Gateway**) require a **dedicated subnet**
- Ensure **enough address space** is unallocated for such services

### 2. **Network Virtual Appliances (NVA)**
- Azure allows traffic flow between subnets by default
- You can override routing to send traffic through an **NVA**
- Deploy services in **separate subnets** to apply custom routing

### 3. **Network Security Groups (NSGs)**
- Associate **0 or 1 NSG per subnet**
- Each NSG can be:
  - Shared across subnets
  - Custom per subnet
- NSG rules control **inbound/outbound** traffic

### 4. **Azure Private Link**
- Secure, **private connectivity** to Azure PaaS or partner services
- Eliminates **exposure to public internet**
- Simplifies architecture with **private endpoints** in a subnet

---

## 🧠 Exam Tips

- Subnets must not **overlap**
- **5 IPs** reserved per subnet
- Subnet routing is **customizable**
- Services like **VPN Gateway** require a **dedicated subnet**
- Use **NSGs** to apply security rules at subnet level
- **Private Link** ensures private, secure connections to services

