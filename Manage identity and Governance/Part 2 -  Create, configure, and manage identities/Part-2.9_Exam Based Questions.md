
---
## ❓ Exam Question

**Q:** An administrator discovers users in a licensing error state due to `LicenseAssignmentAttributeConcurrencyException`.  
What is the recommended course of action?

### ✅ Correct Answer:
> **Allow Microsoft Entra ID to retry processing the user license automatically.**

## 📌 Exam Point Summary

- This error occurs due to **simultaneous/conflicting license assignments** (e.g., group-based and manual).
- ✅ **Recommended Action**: Allow **Microsoft Entra ID to automatically retry** the processing.
- ❌ Manual intervention is **not required** unless the error persists for an extended time.
---

## ❓ Exam Question

**Q:** During a group-based license assignment in Microsoft Entra ID, you encounter a `DependencyViolation` error.  
What should your first action be?

### ✅ Correct Answer:
> **Ensure that all required service plans are assigned before removing dependent licenses.**

---

## 📌 Exam Point Summary

- The `DependencyViolation` error occurs when a **dependent service plan is removed before its prerequisite**.
- ✅ First, verify that **required (parent) service plans are assigned** before removing any **dependent (child) plans**.
- This ensures that licensing dependencies are respected and avoids assignment conflicts.
