# 🔐 What is Self-Service Password Reset (SSPR) in Microsoft Entra ID?

**Scenario**:  
You're seeking ways to **reduce help desk load** and **improve user experience** by enabling users to **reset their own passwords** securely via Microsoft Entra ID.

---

## ✅ Why Use SSPR?

- 🔁 Users can reset passwords via **browser** or **Windows sign-in screen**
- ☎️ Reduces IT help-desk burden
- ⚡ Faster recovery = improved productivity
- 🌐 Supports all apps using **Microsoft Entra ID** (e.g., Azure, M365)

---

## ⚙️ How SSPR Works

1. **Initiate Reset**  
   - Go to password reset portal or click `Can't access your account?`

2. **Localization**  
   - Portal displays in browser's language

3. **Verification**  
   - Username + CAPTCHA

4. **Authentication**  
   - User verifies identity (e.g., OTP, security Qs)

5. **Reset Password**  
   - Enter and confirm new password

6. **Notification**  
   - Email/SMS confirms password reset

💡 *You can customize branding with your logo on the reset screen.*

---

## 🔐 Authentication Methods (Choose ≥ 2)

| Method                  | Registration                                 | Authentication Flow                                 |
|------------------------|----------------------------------------------|-----------------------------------------------------|
| Mobile App (Notification) | Register via Microsoft Authenticator       | Approve push notification                          |
| Mobile App (Code)        | Register via Microsoft Authenticator       | Enter time-based code from app                     |
| Email                    | Provide external email                     | Enter verification code sent to email              |
| Mobile Phone             | Provide mobile number                      | Enter code from SMS or receive a call              |
| Office Phone             | Provide landline number                    | Receive automated call & press `#`                 |
| Security Questions       | Setup predefined Q&A                       | Answer correctly during reset                      |

> 🚫 *Security Qs and SMS are least secure. Use them only with other strong methods.*

---

## 🔁 Minimum Method Requirements

- Set **minimum methods to 1 or 2**
- Set **min # of questions to register & answer** (if using security questions)
- Once users configure enough methods → ✅ *Registered for SSPR*

---

## ✅ Best Practices & Recommendations

- ✔️ Require **2 or more authentication methods**
- ⭐ Use **Mobile App** as primary
- ⚠️ Avoid SMS and Security Questions when possible
- 🔐 Admin accounts:
  - Always require **2 methods**
  - ❌ Cannot use Security Questions

---

## 🔔 Notifications

Admins can enable:

- 📧 **Notify users** on password resets (to alert user of potential misuse)
- 📩 **Notify all admins** if an **admin password** is reset

---

## 📜 Licensing Requirements

| Feature                              | Required License                        |
|-------------------------------------|------------------------------------------|
| Password **change** (signed-in user) | ✅ Any edition (including Free)           |
| Password **reset** (signed-out user) | 🔒 Entra ID P1 / P2 / M365 Biz/Apps      |
| Password **writeback to on-prem**    | 🔒 Entra ID P1 / P2 / M365 Biz/Apps      |

---

## 🔧 Deployment Options

| Option             | Description                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| **Entra Connect**  | For syncing password changes back to **on-prem Active Directory**           |
| **Cloud Sync**     | Used for **disconnected domains** (e.g., post-merger environments)          |
| Hybrid Deployments | Use both Entra Connect & Cloud Sync **side-by-side** to target different users |
| High Availability  | Cloud Sync provides better uptime as it's not tied to a single instance     |

---

## 📌 Summary

- SSPR empowers users to **reset passwords** without admin intervention
- It uses **multi-factor authentication** to ensure security
- Admins can control methods, notifications, and policies
- Requires appropriate **Microsoft Entra ID P1/P2** licenses

---

### 📝 Exam Tip:
> Always enable **at least two authentication methods**, prefer **authenticator app over SMS**, and enforce **stronger policies for admin accounts**.
