# 📘 Azure Policy Definitions – Exam-Focused Guide

## 🎯 What is Azure Policy?
- Enforces **rules** and **effects** on Azure resources for compliance.
- Used for **governance**, **cost control**, and **security**.
- Evaluates **new**, **updated**, or **existing** resources.

---

## 🧱 Anatomy of a Policy Definition

A policy definition (in JSON) contains:

| Element         | Description |
|----------------|-------------|
| `displayName`  | Human-readable name (max 128 chars). |
| `description`  | Description of the policy (max 512 chars). |
| `policyType`   | Origin: `BuiltIn`, `Custom`, or `Static`. |
| `mode`         | Evaluation target: `All`, `Indexed`, or specific Resource Provider modes. |
| `version`      | Optional. Tracks version for Built-in policies. |
| `metadata`     | Info like category, preview flag, etc. |
| `parameters`   | Used to generalize the policy definition. |
| `policyRule`   | The logic (`if` condition and `then` effect). |

---

## 🔄 Supported Modes
### Resource Manager Modes:
- `All`: All resource types including groups and subscriptions.
- `Indexed`: All supported types, evaluated at deployment time.

### Resource Provider Modes:
- Fully supported:  
  - `Microsoft.Kubernetes.Data`, `Microsoft.KeyVault.Data`, `Microsoft.Network.Data`
- Preview:  
  - `Microsoft.ManagedHSM.Data`, `Microsoft.DataFactory.Data`

---

## ✅ Policy Rule Example: Allowed Locations
```json
{
  "displayName": "Allowed locations",
  "description": "Restrict resource deployment to allowed regions.",
  "policyType": "BuiltIn",
  "mode": "Indexed",
  "metadata": {
    "version": "1.0.0",
    "category": "General"
  },
  "parameters": {
    "listOfAllowedLocations": {
      "type": "Array",
      "metadata": {
        "description": "Allowed Azure regions",
        "strongType": "location",
        "displayName": "Allowed locations"
      }
    }
  },
  "policyRule": {
    "if": {
      "allOf": [
        { "field": "location", "notIn": "[parameters('listOfAllowedLocations')]" },
        { "field": "location", "notEquals": "global" },
        { "field": "type", "notEquals": "Microsoft.AzureActiveDirectory/b2cDirectories" }
      ]
    },
    "then": { "effect": "deny" }
  }
}
```



## 🔍 Logical Operators in `if` Block

| Operator | Description |
|----------|-------------|
| `not`    | Inverts the result of a condition. |
| `allOf`  | All conditions must be true. |
| `anyOf`  | At least one condition must be true. |

### ✅ Nested Example:
```json
"if": {
  "allOf": [
    {
      "not": {
        "field": "tags",
        "containsKey": "application"
      }
    },
    {
      "field": "type",
      "equals": "Microsoft.Storage/storageAccounts"
    }
  ]
}
```

## 📐 Condition Types

- **Fields**: e.g., `type`, `location`, `tags`, `name`
- **Value**: Static values like strings, numbers
- **Count**: Matches in arrays using `current()`

## 🧪 Evaluation Operators

| Operator | Value Type |
|----------|------------|
| `equals`, `notEquals` | string, int, date |
| `like`, `notLike`     | wildcard match |
| `in`, `notIn`         | array |
| `contains`, `notContains` | substring |
| `containsKey`, `notContainsKey` | tag keys |
| `less`, `greater`, `lessOrEquals`, `greaterOrEquals` | numeric/date |
| `exists`              | boolean |
| `match`, `notMatch`, `matchInsensitively` | regex |

## 🧠 Policy Functions

| Function | Description |
|----------|-------------|
| `addDays(datetime, num)` | Add days to UTC datetime |
| `field("name")`          | Get value of a resource property |
| `utcNow()`               | Current UTC time in ISO 8601 |
| `policy()`               | Policy metadata: `assignmentId`, `definitionId`, etc. |
| `requestContext().apiVersion` | API version of the triggering request |
| `ipRangeContains()`      | Check if an IP range includes another |
| `current()`              | Used in `count` logic for arrays |

## 🎬 Effects (Used in `then` Block)

| Effect             | Description                                        | Type    |
|--------------------|----------------------------------------------------|---------|
| `deny`             | Blocks non-compliant resources                     | Sync    |
| `audit`            | Logs warning, doesn't block resource               | Async   |
| `append`           | Adds fields to resource                            | Sync    |
| `modify`           | Changes resource properties                        | Sync    |
| `auditIfNotExists` | Audits if related resource is missing              | Async   |
| `deployIfNotExists`| Deploys related resource if missing                | Async   |
| `denyAction`       | Blocks specific actions (e.g., delete)             | Sync    |
| `manual`           | Manual compliance attestation                      | Manual  |
| `disabled`         | Deactivates the policy                             | Bypass  |

### 📌 Notes
- `audit`, `deny`, `modify`, `append` → interchangeable.
- `auditIfNotExists` ↔ `deployIfNotExists` → often paired.
- `manual` → unique, non-interchangeable.
- `disabled` → bypasses all enforcement.

## 📎 Example with `value`, `count`, and `current`

```json
{
  "if": {
    "allOf": [
      {
        "value": "[resourceGroup().name]",
        "like": "*netrq"
      },
      {
        "field": "type",
        "notLike": "Network/*"
      }
    ]
  },
  "then": {
    "effect": "deny",
    "details": {
      "count": {
        "field": "Microsoft.Network/virtualNetworks/addressSpace.addressPrefixes[*]",
        "where": {
          "value": "[ipRangeContains('10.0.0.0/24', current('Microsoft.Network/virtualNetworks/addressSpace.addressPrefixes[*]'))]",
          "equals": "greater"
        }
      }
    }
  }
}
```

## 📝 Summary Tips for Exam

- A **policy** = `condition (if)` + `effect (then)`
- Use **parameters** to generalize and reuse policies.
- Understand and read **JSON structure** of policies.
- Know the purpose of `mode`, `policyType`, and `effect` values.
- Be confident in logical operators: `allOf`, `anyOf`, `not`.
- Policy-only functions: `utcNow()`, `field()`, `addDays()` etc.
- **Most restrictive** effect wins if multiple policies apply.
- Use `auditIfNotExists` / `deployIfNotExists` for dependencies.
- Always evaluate **compliance logic** and **scope** of assignment.

---

📄 **Document by Mahendar**  
🎓 *Azure DevOps Engineer*
