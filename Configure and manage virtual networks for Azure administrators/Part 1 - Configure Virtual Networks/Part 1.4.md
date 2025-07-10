# 🌐 Azure Public IP Address – Exam Notes

## 📖 Overview
A **Public IP Address** in Azure allows resources like Virtual Machines and Load Balancers to communicate with the internet. Understanding its configuration and behavior is critical for exams like AZ-104, AZ-305, etc.


<img src="https://github.com/user-attachments/assets/ffd9fd78-5094-4e62-8a61-de34a6cb024d" width="650" height="550">
---

## ⚙️ Configuration Settings

| Setting               | Description |
|-----------------------|-------------|
| **IP Version**        | Choose `IPv4`, `IPv6`, or `Both` |
| **SKU**               | `Basic` or `Standard` |
| **Name**              | Must be unique within the Resource Group |
| **Assignment Method** | `Dynamic` or `Static` |
| **Tier (Standard SKU)** | `Regional` or `Global` |

---

## 🆚 Key Differences Summary

| Feature                     | DHCP Private IP (Azure) | Public IP - Dynamic       | Public IP - Static        |
|-----------------------------|--------------------------|----------------------------|----------------------------|
| Scope                       | Internal (VNet only)     | Internet-facing            | Internet-facing            |
| Protocol Used               | DHCP                     | Azure-managed assignment   | Azure-managed reservation  |
| Assigned By                 | Azure DHCP               | Azure IP Pool              | Azure IP Pool              |
| IP Changes?                 | Yes (unless reserved)    | Yes (on stop/deallocate)   | No                         |
| Created Manually?           | No (auto by subnet config) | Yes                        | Yes                        |
| DNS/FW Compatibility        | Not applicable           | ❌ Not reliable             | ✅ Required for stable DNS |

---

## 📌 Exam Tips

- Azure **does not use DHCP for public IP assignment**.
- **Static Public IPs** are used when IP address **must remain constant**.
- **Dynamic Public IPs** are suitable for **non-critical, cost-optimized scenarios**.
- **DHCP** is only responsible for **private IPs** within a **VNet**.

---

## 🎯 Real-World Example

| Scenario                          | Type of IP Used       |
|----------------------------------|------------------------|
| Internal VM communication        | DHCP Private IP (VNet) |
| Test VM with temporary access    | Dynamic Public IP      |
| Production web server            | Static Public IP       |
| Azure Bastion or VPN Gateway     | Static Public IP       |
## 🔁 Assignment Methods

### 🌀 Dynamic
- Assigned when resource starts.
- Can **change** on stop/deallocate.
- Stays the same on reboot or OS shutdown.
- Released when disassociated.

### 📍 Static
- Assigned at **creation time**.
- **Fixed IP** until manually deleted.
- Useful for **DNS**, **firewall rules**, and **static routes**.

---

## ⚠️ Important Notes

- **IPv6 + Basic SKU** → Only supports **Dynamic** assignment.
- **Standard SKU** supports **Static** assignment for both IPv4 and IPv6.
- SKU of Public IP must match the SKU of any associated Load Balancer.
- Cannot change Dynamic ↔ Static **if associated** with a resource.

---

## 📌 Best Practices

- Use **Static IPs** for production workloads.
- Prefer **Standard SKU** for:
  - Zone redundancy
  - Enhanced availability
  - Secure by default
- Name IPs with clarity: `web-prod-pip`, `vm1-public-ip`, etc.

---

## 🧠 Exam Points to Remember

- ✅ Public IP enables external communication.
- ✅ Two types of assignment: **Dynamic** and **Static**.
- ✅ **Basic SKU** is cheaper, limited features.
- ✅ **Standard SKU** supports high availability, zone-redundancy.
- ✅ IP address can’t be reassigned across regions.

---

## 🧪 Use Case Matrix

| Scenario                      | Recommended Configuration         |
|-------------------------------|-----------------------------------|
| Production Web Server         | Static, Standard SKU              |
| Test VM                       | Dynamic, Basic SKU                |
| Load Balancer Frontend IP     | SKU must match Load Balancer SKU  |
| Global Web App Gateway        | Static, Standard, Global Tier     |

---

## 🖼️ Diagram

```plaintext
[Virtual Machine]
     |
     |--> 🌐 Public IP Address (Static or Dynamic)
             |
             --> Internet

You cannot change assignment type (Dynamic ↔ Static) if IP is already associated with a resource.
```
