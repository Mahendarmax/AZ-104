# 🛡️ Azure Policy Design Principles - Exam Essentials

## 📘 Overview
- Azure Policy supports governance by enforcing rules and compliance across Azure resources.
- Helps **secure, manage, and track** cloud resource usage and costs.
- Policies are strategically planned and applied at different scopes within a hierarchy.

---

## 🏗️ Governance Hierarchy in Azure

| Scope | Description |
|-------|-------------|
| **Management Groups** | Organize subscriptions for enterprise-level governance; can be nested |
| **Subscriptions** | Logical containers for billing, scaling, and management |
| **Resource Groups** | Logical groupings of Azure resources (1 resource → 1 group) |
| **Resources** | The actual services (VMs, databases, etc.) deployed in Azure |

🧠 **Inheritance**: Policies applied at higher levels (e.g., subscription) cascade down to lower levels (e.g., resource).

---

## ⚙️ Azure Resource Manager (ARM)

- ARM is the **control layer** for deploying and managing Azure resources.
- Supports **template deployments**, **RBAC**, **tagging**, and **auditing**.
- Azure Policy is integrated directly with ARM to evaluate policies at deployment time.

---

## 🔄 Control Plane vs Data Plane

| Plane | Purpose |
|-------|---------|
| **Control Plane** | Manages Azure resources via APIs/tools (e.g., create, update, delete) |
| **Data Plane** | Interacts with resource data (e.g., uploading files, reading secrets) |

Azure Policy operates mainly on the **control plane**, but also supports **data plane** integration for specific services.

---

## 🔌 Data Plane Policy Support (Resource Provider Modes)

| Provider | Use Case |
|----------|----------|
| `Microsoft.Kubernetes.Data` | Manage Kubernetes objects like pods and containers |
| `Microsoft.KeyVault.Data` | Govern vault secrets and certificates |
| `Microsoft.Network.Data` | Enforce custom network policy memberships |
| `Microsoft.ManagedHSM.Data` | Manage HSM keys with policy |
| `Microsoft.DataFactory.Data` | Block outbound domains in Data Factory |
| `Microsoft.MachineLearningServices.v2.Data` | Evaluate ML model deployment compliance |

---

## 🚦 Operation Flows: Greenfield vs Brownfield

### ✅ Greenfield (Policy-first)
- Policy exists **before** resource is created or updated.
- ARM evaluates:
  1. **RBAC first**, then  
  2. **Azure Policy**
- Delta changes are merged with existing state before evaluation.

### 🏗️ Brownfield (Resource-first)
- Resources already exist; policy is applied **afterward**.
- Azure Policy runs:
  - **Compliance scans every 24h**
  - Or manually triggered scans
- Existing noncompliant resources are **flagged**, not deleted.

---

## 📌 Design Tips

- Always design for **inheritance and consistency** using the governance hierarchy.
- Leverage **Azure Policy + Azure Resource Manager** for centralized management.
- Apply **policy exemptions** thoughtfully to avoid over-restriction.
- Consider **compliance scanning + auto-remediation** in Brownfield environments.
- Design policies with a balance of **control, stability, and speed**.

---

📄 **Document by Mahendar**  
*Azure DevOps Engineer*
