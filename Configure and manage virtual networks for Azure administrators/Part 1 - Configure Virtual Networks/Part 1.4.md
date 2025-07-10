# 🌐 Azure Public IP Address – Exam Notes

## 📖 Overview
A **Public IP Address** in Azure allows resources like Virtual Machines and Load Balancers to communicate with the internet. Understanding its configuration and behavior is critical for exams like AZ-104, AZ-305, etc.


<img src="https://github.com/user-attachments/assets/1466624f-e5af-41ec-a396-5605f63e7b90" width="650" height="700">
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
