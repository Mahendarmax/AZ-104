# Define the markdown content for Evaluation of resources through Azure Policy

# ✅ Evaluation of Resources through Azure Policy

## 🎯 Evaluation Triggers

Azure Policy evaluations are triggered by the following actions:

- A policy or initiative is **newly assigned** to a scope.
- An **update** to an existing policy or initiative assignment.
- A resource is **deployed or updated** in a scoped assignment.
- A **subscription is created or moved** within a policy-assigned management group.
- A **policy exemption** is created, updated, or deleted.
- **Machine configuration provider** updates compliance details.
- **Manual trigger** via on-demand scan (`az policy state trigger-scan`).

---

## ⏱️ Evaluation Timing

- **Automatic Scan**: Every 24 hours by default.
- **Manual Scan (Brownfield)**: Trigger via CLI for existing resources.
- **Delay for New Assignment**: Up to 30 mins due to ARM cache (sign-out/in to bypass).
- **Factors Affecting Time**:
  - Size/complexity of policy definitions.
  - Number of policies assigned.
  - Scope of assignment.
  - System load (low priority operation).

---

## 📊 Resource Compliance States

Each evaluated resource is assigned a compliance state:

- ✅ **Compliant**
- ❌ **Non-compliant**
- ⚠️ **Error** – Evaluation or template issue.
- 🔁 **Conflicting** – Contradictory policies (e.g. same tag, different values).
- 🔒 **Protected** – Affected by `denyAction` effect.
- 🛑 **Exempted**
- ❓ **Unknown** – Applies to `manual` effect.

**Compliance % Formula**:  
_Compliant + Exempt + Unknown_ ÷ _Total Evaluated Resources_

---

## 🚦 Enforcement Mode

| Mode      | JSON Value     | Effect Type | Logs | Manual Remediation | Description |
|-----------|----------------|-------------|------|---------------------|-------------|
| Enabled   | `Default`      | Active      | Yes  | Yes                 | Enforces policy effects. |
| Disabled  | `DoNotEnforce` | Inactive    | No   | Yes                 | Evaluates without enforcing. |

- Use `Disabled` for **What-If Testing** before enabling in production.
- Different from `effect: "disabled"` (which skips evaluation entirely).

---

## ✅ Safe Deployment Best Practices

### Step-by-Step Deployment Rings

1. **Create Definition**: Scope = tenant root.
2. **Create Assignment**: Start in Ring 5 with `enforcementMode: Disabled`.
3. **Compliance Check (Ring 5)**.
4. **Health Check (Ring 5)**.
5. **Repeat for Non-Production Rings**.
6. **Update Assignment** if needed.
7. **Enable enforcementMode** for Ring 5.
8. **Repeat Steps 3-4 for all Rings**.
9. **Move to Production Rings** gradually.

---

## 🛠️ Reacting to Policy State Changes

- Azure Policy integrates with **Azure Event Grid**.
- Events pushed to Event Handlers:
  - **Azure Functions**
  - **Logic Apps**
  - **Custom HTTP listener**
  - **Webhooks**
- Benefits:
  - No polling required.
  - Built-in retry & dead-letter support.
  - Efficient and scalable.

---

📄 **Document by Mahendar**  
🎓 *Azure DevOps Engineer*
