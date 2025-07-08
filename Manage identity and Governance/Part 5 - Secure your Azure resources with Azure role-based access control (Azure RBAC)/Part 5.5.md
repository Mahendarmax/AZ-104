# 📊 Exercise – View Activity Logs for Azure RBAC Changes

**Scenario**:  
At *First Up Consultants*, you're responsible for reviewing **Azure RBAC changes** as part of a **quarterly audit**.  
Your manager wants a report of all **role assignment and custom role definition changes** for the **last month**.

---

## ✅ Step-by-Step: View Activity Logs in Azure Portal

1. Go to the Azure Portal.
2. In the left navigation or search bar:
   - Click **All Services**
   - Search for and select **Activity Log**

![image](https://github.com/user-attachments/assets/2ec043b0-721d-46b1-96e4-37f984205ae0)

![image](https://github.com/user-attachments/assets/de35e486-8130-45c9-8226-68761d6c78be)

---

## 🛠️ Filter Logs

3. Set the **Timespan** filter to **Last month**  
4. In the **Operation** filter, type and select `role`  
5. Select the following **RBAC-related operations**:
   - 🔹 `Create role assignment` (`roleAssignments`)
   - 🔹 `Delete role assignment` (`roleAssignments`)
   - 🔹 `Create or update custom role definition` (`roleDefinitions`)
   - 🔹 `Delete custom role definition` (`roleDefinitions`)

![image](https://github.com/user-attachments/assets/c1c4acf1-b969-4bd6-a652-d2b9fe653237)


![image](https://github.com/user-attachments/assets/3aa27b1a-a562-4edd-9298-b52fc7bbf295)

---

## 📁 View & Download Results

6. View the filtered list of role-related changes
7. Click on any item to see full **Activity Log details**:
   - Who performed the action
   - What resource was affected
   - Timestamp and status

8. Click the **Download as CSV** button to export the report

📷 Screenshot: Detailed view of a selected activity log item

---

## 🧠 Summary

You learned how to:
- ✅ Use **Activity Log** in the Azure Portal to track **RBAC-related changes**
- ✅ Apply filters to isolate **role assignments** and **custom role changes**
- ✅ Export logs as **CSV** for auditing and reporting purposes

---

### 📝 Exam Tips:
- **Azure Activity Log** captures **control plane events**, including RBAC changes
- Always **filter by operation name** to find relevant actions
- You can **download logs** for offline auditing/reporting
