# 🧪 Exercise – Grant Access Using Azure RBAC & Azure Portal

**Scenario**:  
At *First Up Consultants*, your coworker **Alain** needs access to **create and manage Virtual Machines**.  
Your manager asks you to grant access using the **least privilege principle** → so you assign the **Virtual Machine Contributor** role at the **Resource Group** level.

---

## ✅ Step 1: Grant Access

### 🔐 Requirements:
- Must sign in as an admin with:
  - `User Access Administrator` **or**
  - `Owner` role

---

### 🪜 Procedure:

1. 🔎 In the Azure portal, search for **Resource groups**
2. Select the desired **resource group** (e.g., `example-group`)
3. In the left pane, click **Access control (IAM)**
4. Navigate to the **Role assignments** tab
5. Click **Add > Add role assignment**

> ⚠️ If the option is disabled, your account lacks permission to assign roles

---

### 🧭 Assign Role to User:

6. In the **Add role assignment** panel:
   - On **Role tab**: Search and select `Virtual Machine Contributor`
   - Click **Next**
7. On the **Members tab**:
   - Click **Select members**
   - Search and choose `Alain`
   - Click **Select**
   - Click **Next**
8. On **Review + assign** tab:
   - Verify role + user + scope
   - Click **Review + assign**

✅ **Result**:  
Alain is now a **Virtual Machine Contributor** for this resource group and can create/manage VMs **only within this scope**.

📷 Screenshot: Role successfully assigned.

---

## ❌ Step 2: Remove Access

1. In the IAM pane → go to **Role assignments**
2. Click **View Assignments**
3. Search and check the box next to `Alain`'s role assignment
4. Click **Delete**
5. Confirm in the **Remove role assignment** message by clicking **Yes**

📷 Screenshot: Remove role assignment dialog.

---

## 🧠 Summary

In this unit, you learned how to:
- ✅ Grant a user **least privilege access** using the **Virtual Machine Contributor** role
- ✅ Assign the role **at the resource group scope**
- ✅ Remove role assignments if needed

---

### 📝 Exam Tips:
- Use **least privilege** principle for access control.
- Role assignment = **Role + User/Group + Scope**
- Ensure you have proper permissions to **assign** or **remove** roles.
