# 🛡️ Azure Policy Resources - Exam Essentials

Azure Policy helps enforce organizational standards and assess compliance across Azure environments. It works by evaluating resource properties and actions against defined business rules, allowing fine-grained governance and compliance management.

---

## 📘 Key Azure Policy Resources

### 📌 1. Definitions
- Describe **conditions and effects** to apply to Azure resources.
- Defined in **JSON**; stored at **management group** or **subscription** level.
- The **scope** (MG, subscription, RG, resource) determines which resources are evaluated.
- Inheritance applies—lower scopes inherit from higher ones.

---

### 📌 2. Initiatives (Policy Sets)
- A **group of policy definitions** that target broader compliance goals.
- Simplifies management by assigning multiple policies as one unit.
- Can be used for:
  - Regulatory compliance frameworks
  - Organizational standards
- Defined using JSON.
- Types:
  - **Built-in initiatives** – Provided by Azure for common use cases.
  - **Custom initiatives** – User-defined for specific needs.
  - **Microsoft Cloud for Sovereignty** – Prebuilt custom initiatives focused on public sector compliance.

---

### 📌 3. Assignments
- Determine **which resources are evaluated** using a policy or initiative.
- Defined at **scope level** (MG, subscription, RG, or resource).
- Options available during assignment:
  - **Included/Excluded scopes**
  - **enforcementMode** (disabled for testing without enforcement)
  - **Overrides** to change the policy effect without altering the definition
  - **Noncompliance messages** for clarity
  - **Parameters** for dynamic assignment
  - **Managed Identity** required for `deployIfNotExists` remediation

---

### 📌 4. Exemptions
- Exclude specific resources or scopes from compliance evaluations **after** assignment.
- Count toward compliance total but are not evaluated.
- Two exemption categories:
  - **Mitigated** – Policy intent met via another method.
  - **Waiver** – Temporarily allow noncompliance.

---

### 📌 5. Attestations
- Used to **manually set compliance states** for resources targeted by manual policy assignments.
- Each resource needs one attestation per manual policy.
- Best used when human validation is required for compliance state.

---

### 📌 6. Remediations
- Automatically or manually **bring resources into compliance**.
- Works with **`modify`** and **`deployIfNotExists`** effects.
- New and existing resources can be remediated via:
  - **Automatic remediation** at creation
  - **Remediation task** for existing noncompliant resources

---

## ✅ Summary of Azure Policy Control Flow

| Concept | Purpose |
|--------|---------|
| Definitions | Define conditions and effects |
| Initiatives | Group multiple policies for broader goals |
| Assignments | Apply policies/initiatives to resource scopes |
| Exemptions | Exclude specific resources/scopes from evaluation |
| Attestations | Manually confirm compliance for manual policies |
| Remediations | Fix noncompliant resources automatically or manually |

---

📄 **Document by Mahendar**  
*Azure DevOps Engineer*
