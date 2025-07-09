# 💡 Microsoft Entra Self-Service Password Reset (SSPR) - Exam Notes

## 🎯 Objective:
Enable and configure Self-Service Password Reset (SSPR) for a targeted group of users, then roll it out organization-wide.

---

## ✅ Prerequisites
- Microsoft Entra tenant with **P1 or P2** license (trial or paid).
- User with **Authentication Policy Administrator** role.
- A **non-administrative test user** with a valid license.
- A **security group** containing pilot users (e.g., Marketing team).

---

## ⚙️ SSPR Configuration Steps

### 1. 📍 Navigate
- Go to: `Azure Portal > Microsoft Entra ID > Manage > Password reset`

---

### 2. 🏗️ Properties

![image](https://github.com/user-attachments/assets/97adfe80-7796-40a7-b3a3-d571b7f04c09)


- **Enable SSPR**: Set to `Selected`
- **Assign Group**: Choose security group (e.g., Marketing)
- `None`: Disable SSPR
- `Selected`: Targeted group (pilot)
- `All`: Enable for all users

---

### 3. 🔐 Authentication Methods

![image](https://github.com/user-attachments/assets/38fc2a8b-ea07-4cf8-87ee-7dc9f10fa8b7)


- Set required methods: `1` or `2` (recommended: 2)
- Choose from:
  - Mobile phone
  - Email
  - Security questions
  - Microsoft Authenticator app

---

### 4. 📝 Registration

![image](https://github.com/user-attachments/assets/8b5fc9de-accb-4b9a-94b0-de3dbd203f4c)


- Require users to register at next sign-in: ✅ `Yes`
- Set reconfirmation interval (e.g., `180 days`)

---

### 5. 📩 Notifications

![image](https://github.com/user-attachments/assets/c8d29e11-7468-4ffe-817f-320d22f3a8bc)


- Notify users on password reset: ✅ `Yes`
- Notify admins on admin password reset: ✅ `Yes`

---

### 6. 🎨 Customization (Optional)

![image](https://github.com/user-attachments/assets/f8de16c7-9981-436d-9a75-b29f91a6d5b3)


- Provide helpdesk email/URL (e.g., `support@yourcompany.com`)

---

## 🧪 Testing
- Use non-admin test user.
- Go to: `https://aka.ms/sspr`
- Test registration and password reset functionality.

---

## 🚀 Rollout Strategy
- Start with `Selected` group.
- Monitor feedback.
- Expand to `All` users if successful.

---

## 📌 Notes for Exam (Gunshots)
- SSPR requires **valid license** (P1/P2).
- **Admins have stricter requirements** for SSPR.
- SSPR is **disabled by default** (`None`).
- Use **security groups** for pilot rollouts.
- Reconfirmation helps keep info up to date.
- Notifications improve security awareness.
