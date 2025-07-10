# 📘 Azure Private IP Address Allocation – Exam Quick Notes

## 🔗 Associating Private IP Addresses

- Private IPs can be **associated with**:
  - ✅ Virtual Machine (NIC)
  - ✅ Internal Load Balancer (Front-end config)
  - ✅ Application Gateway (Front-end config)

---

## 📌 Private IP Association Matrix

| Resource               | How it's associated        | Dynamic IP | Static IP |
|------------------------|-----------------------------|-------------|------------|
| Virtual Machine        | NIC                         | ✅ Yes      | ✅ Yes     |
| Internal Load Balancer | Front-end configuration     | ✅ Yes      | ✅ Yes     |
| Application Gateway    | Front-end configuration     | ✅ Yes      | ✅ Yes     |

---

## 🛠️ Private IP Address Assignment

- IPs are **allocated from subnet range** (e.g. `10.0.0.0/16`)

### 🔄 Dynamic (Default)
- Azure assigns the **next available unassigned** IP in the subnet.
- Example: If `10.0.0.4–10.0.0.9` are used → Azure assigns `10.0.0.10`

### 📍 Static
- You manually select any **unassigned/reserved** IP in the subnet.
- Example: Assign `10.0.0.20` if it's available in the subnet range.

---

## ⚠️ Important Limitation

> 🔁 **You cannot switch between Dynamic and Static IP directly.**
>
> To change the assignment type, you must:
> - ❌ Remove the existing IP configuration from the NIC.
> - ✅ Reassign a new IP with the desired type (static or dynamic).

---

## 💡 Key Points

- Use **Static IPs** for services that require fixed internal addressing.
- Private IPs are scoped **within the subnet of a VNet**.
- Plan address space carefully to avoid IP conflicts.
