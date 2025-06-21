# 📘 Microsoft Entra ID: Group License Management – Exam Notes

---

## 🧪 Exercise: Change Group License Assignments

### ✔️ Steps:
1. Go to **Microsoft Entra Admin Center**: https://entra.microsoft.com  
2. Navigate to **Groups** > **All groups** > select a group  
3. Go to **Licenses** under **Manage**  
4. Click **+ Assignments** → redirected to:  
5. **Microsoft 365 Admin Center**: https://admin.microsoft.com  
6. Go to **Billing** > **Licenses** > pick a license  
7. Select **Groups** > **+ Assign licenses** > select group > click **Assign**  
8. Review license assignment in both **Microsoft Entra** and **M365 Admin** portals  

---

## ⚠️ Group Licensing Errors and Troubleshooting

### 1. Not Enough Licenses
- **Cause**: Group has more users than available licenses  
- **Fix**: Buy more or free up unused licenses  
- **PowerShell Error**: `CountViolation`

### 2. Conflicting Service Plans
- **Cause**: Incompatible plans assigned (e.g., E1 + E3: Exchange Online Plan 1 vs Plan 2)  
- **Fix**: Disable conflicting plan or remove one  
- **PowerShell Error**: `MutuallyExclusiveViolation`

### 3. Dependency Violations
- **Cause**: Removing a license that supports another service  
- **Fix**: Assign prerequisite or disable dependent service  
- **PowerShell Error**: `DependencyViolation`

### 4. Invalid Usage Location
- **Cause**: Usage location not set or unsupported  
- **Fix**: Set a valid usage location in user profile  
- **PowerShell Error**: `ProhibitedInUsageLocationViolation`

### 5. Duplicate Proxy Addresses
- **Cause**: Users have same `proxyAddress` (Exchange-related)  
- **Fix**: Resolve conflict, then reprocess group/user  

### 6. Attribute Change After License Assignment
- **Observation**: `Mail` or `ProxyAddresses` may update  
- **Note**: This is expected behavior  

### 7. Concurrency Exception
- **Cause**: Same license from multiple groups  
- **Fix**: No action needed; Entra retries automatically  
- **Error**: `LicenseAssignmentAttributeConcurrencyException`

---

## ➕ Assigning Multiple Licenses to a Group

- You can assign multiple licenses (e.g., Office 365 E3 + EMS) to a single group  
- If **any product fails**, **none will be assigned**  
- Review: Go to group > **Licenses** > **Users in error state**

---

## 🗑️ When a Licensed Group is Deleted

- All licenses must be removed before deleting the group  
- If a user has a dependent service, license may be **converted to direct assignment**

---

## 🔄 Products with Prerequisites

Some products (e.g., **Microsoft Workplace Analytics**) are add-ons requiring other services:

### Example:
- Assign:
  - **Office 365 E3** with **Exchange Online Plan 2**
  - **Workplace Analytics**

- Both must be in the **same group**

---

## 🔁 Force License Reprocessing

### For a Group:
- Go to group > **Licenses** > **Reprocess**

### For a User:
- Go to user > **Licenses** > **Reprocess**

---

## 🔀 Migrating from Direct to Group-Based Licensing

### ✅ Recommended Process:
1. Keep existing direct licensing (PowerShell) running  
2. Create licensing groups & add users  
3. Assign same licenses to the group  
4. Verify assignments via **audit logs** or **license state**  
5. Gradually remove direct licenses (start with few users)

### 🧠 Important:
- Group + Direct license of same product = **only one license consumed**
- Use PowerShell to verify license source per user

---

## 🔄 Changing License Plans (e.g., E1 → E3)

### Ensure:
- Current licenses are **group-assigned** (not direct)
- **Enough licenses** for new plan
- No **conflicting or dependent service plans**

> License changes are **applied simultaneously**, so users won't lose service.

---
