# 🧪 Exercise – List Access Using Azure RBAC & Azure Portal

**Scenario**:  
You're part of the **marketing team** at *First Up Consultants*. You've been granted access to a **Resource Group** and now want to:
- 🔍 View your role assignments
- 🔍 View all roles and users at the Resource Group level

> 📝 **Note**: An Azure subscription is required. If you don’t have one:
> - Create a free Azure account
> - Or use the **Azure for Students** offer

---

## ✅ Step 1: List **Your Role Assignments**

1. 🔐 **Sign in** to the [Azure Portal](https://portal.azure.com)
2. Click your **Profile Menu (top-right)** → Select **`...` (More Options)**

![image](https://github.com/user-attachments/assets/23475694-383c-4c36-abc2-4be9972477d1)


3. Click **`My permissions`**
4. The **My Permissions** pane opens → shows:
   - Your **roles**
   - The **scope** (subscription, resource group, etc.)

 `My permissions` panel displays user roles and scopes.

![image](https://github.com/user-attachments/assets/d84e60f2-649a-4728-bed9-27182ebec0ca)



---

## ✅ Step 2: List Role Assignments for a **Resource Group**

![image](https://github.com/user-attachments/assets/38ebaec6-bd8a-4b1f-9ebc-8dc3190f4cff)


1. Use the **Search bar** → Search for **`Resource groups`**
2. Select your desired **Resource Group** (e.g., `example-group`)
3. In the left menu pane, click **Access control (IAM)**

![image](https://github.com/user-attachments/assets/2051f40a-1694-4023-bdbf-08c66de07b8b)


4. Go to the **Role assignments** tab

![image](https://github.com/user-attachments/assets/25c38c4b-1e79-4e82-a096-64edc2663a5d)


📌 This view shows:
- 👥 Who has access
- 📌 At what **scope** (This resource or Inherited)

IAM > Role assignments for a resource group

---

## ✅ Step 3: List **Available Roles**

![image](https://github.com/user-attachments/assets/407b7591-6100-41b1-ae5f-af221115dd2d)


1. In the **Access control (IAM)** pane → Select **`Roles` tab**
2. View:
   - All **built-in** and **custom** roles
   - Click **`View`** next to any role to open details
3. In the **Assignments** tab of a role, see:
   - How many **users** and **groups** have that role

📷 Screenshot: Roles list with assignment counts

---

## 🧠 Summary

You learned how to:
- ✅ List **your assigned roles** in Azure
- ✅ List **role assignments for a resource group**
- ✅ View **all available roles** and their user/group assignments

---

### 📌 Exam Tip:
- Use **IAM** in the Azure portal to manage access.
- Always check the **scope** (e.g., inherited roles vs. directly assigned roles).
- You can’t edit permissions here—just **view and assign** existing roles.

