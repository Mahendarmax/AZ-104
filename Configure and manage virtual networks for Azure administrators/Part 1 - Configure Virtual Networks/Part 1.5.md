# 📘 Azure Public IP Address Association – Exam Quick Notes

## 🔗 Associating Public IP Addresses

- Public IPs can be **associated with**:
  - ✅ Virtual Machine (NIC)
  - ✅ Internet-facing Load Balancer (Front-end config)
  - ✅ VPN Gateway (IP config)
  - ✅ Application Gateway (Front-end config)

- **Supported IP types**:
  - ✔️ **Dynamic Public IP**
  - ✔️ **Static Public IP** (note: static IPs depend on SKU type)

---

## 📌 Public IP Association Matrix

| Resource            | How it's associated        | Dynamic IP | Static IP     |
|---------------------|-----------------------------|-------------|----------------|
| Virtual Machine     | NIC                         | ✅ Yes      | ✅ Yes         |
| Load Balancer       | Front-end configuration     | ✅ Yes      | ✅ Yes         |
| VPN Gateway         | VPN gateway IP configuration| ✅ Yes      | ✅ Yes *       |
| Application Gateway | Front-end configuration     | ✅ Yes      | ✅ Yes *       |

> 🔸 *Static IP only on specific SKUs

---

## 🆚 Public IP SKU Comparison

| Feature          | Basic SKU           | Standard SKU                             |
|------------------|---------------------|-------------------------------------------|
| **IP Assignment**| Static or Dynamic   | Static only                               |
| **Security**     | Open by default     | Secure by default (closed to inbound)     |
| **Resources**    | NICs, VPN, App GW, LB | NICs or Public Standard Load Balancers  |
| **Redundancy**   | Not zone redundant  | Zone redundant by default                 |

> ⚠️ **Important:**  
> Basic SKU Public IPs will be **retired on Sept 30, 2025**.  
> 👉 Use **Standard SKU** going forward.

---

## 💡 Key Points

- Choose **Standard SKU** for production workloads.
- **Static IPs** offer predictability – useful for DNS and firewall rules.
- VM’s **Public IP** is attached to its **NIC**, not directly to the VM.
- **Deallocating a VM with Dynamic IP** → causes IP change.

