# 📌 Determine Network Security Group (NSG) Effective Rules

## 🧠 Overview

When multiple **Network Security Groups (NSGs)** are associated with both a **subnet** and **network interface (NIC)**, their rules are evaluated **independently**. The combination of both determines the **effective** rules applied to a virtual machine (VM).

Understanding the **evaluation order**, **priority handling**, and **intra-subnet behavior** is key to configuring secure and functional networking.

---

## 🔄 NSG Rule Evaluation Order

| Traffic Type | Evaluation Sequence                            |
|--------------|--------------------------------------------------|
| **Inbound**  | Subnet NSG → NIC NSG                             |
| **Outbound** | NIC NSG → Subnet NSG                             |
| **Intra-subnet** | Evaluated based on rules applied to the subnet NSG |

> 🔍 Each NSG processes its rules **independently**, and both must allow traffic for it to pass.

---

## 🧮 Effective Rules Logic

- If **either NSG denies** traffic, **the traffic is blocked**.
- Rules are matched based on **priority** (lower number = higher priority).
- Default rules exist unless overridden by custom rules with a higher priority.

---

## 🛠️ Key Considerations for Effective Rules



<img width="927" height="454" alt="image" src="https://github.com/user-attachments/assets/d410d314-e706-48cc-9a2f-061e713cdffd" />




### ✅ 1. No NSG = All Traffic Allowed
- If no NSG is associated at subnet/NIC level, **default Azure rules apply**, allowing all traffic.

### ✅ 2. Define Allow Rules at Every Level
- For traffic to flow:
  - Subnet NSG must allow it.
  - NIC NSG must allow it.
- Missing allow rule at **any level** = **traffic denied**.

### ✅ 3. Intra-subnet Traffic Control
- Subnet-level NSGs **can block communication** between VMs within the **same subnet**.
- Define explicit **deny rules** to prohibit internal traffic.

### ✅ 4. Rule Priority Best Practices
- Rules processed in **ascending order of priority**.
- Use **priority gaps** (e.g., 100, 200, 300) to easily insert new rules later.

---

## 🔍 Viewing Effective Rules in Azure

- Use the **"Effective security rules"** link on the **Networking blade** of a VM in the Azure Portal.
- This view shows **combined NSG rules** from subnet and NIC.
- For deep analysis, use **Azure Network Watcher** for centralized diagnostics.

---

## 🧠 Exam Tips

- 📌 **Subnet-level NSG evaluated first for inbound**, NIC-level **for outbound**.
- 🧱 **Both levels must allow traffic**; one deny = total deny.
- 🧰 Use **Network Watcher** and **Effective security rules** tool for troubleshooting.
- 🔗 **Intra-subnet rules are enforced** through subnet-level NSG.
- 🛑 Never forget to define **Allow rules at both levels**, or traffic is dropped by default.

---

## 📊 Example: Inbound Evaluation

```text
            [Internet]
                 |
         (Subnet NSG - Rule: Allow TCP:80)
                 |
         (NIC NSG - Rule: Deny All)
                 |
                [VM]

=> Result: ❌ DENIED (because NIC NSG denies)

```
