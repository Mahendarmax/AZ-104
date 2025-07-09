# 🎨 Exercise – Customize Directory Branding in Microsoft Entra ID

## 🎯 Goal:
Add your organization’s branding to the Microsoft Entra sign-in page to ensure users trust the login experience.

---

## 📁 Required Image Files

| Image Type       | Format     | Dimensions      | Size Limit |
|------------------|------------|------------------|------------|
| Background Image | PNG or JPG | 1920 x 1080 px   | < 300 KB   |
| Company Logo     | PNG or JPG | 32 x 32 px       | < 5 KB     |

---

## 🔹 Step 1: Sign In and Navigate

- Sign in to the [Azure Portal](https://portal.azure.com).
- Navigate to: `Microsoft Entra ID > Manage > Company branding`
- If in the wrong directory:  
  - Go to **Azure profile > Switch directory**

---

## 🔹 Step 2: Configure Branding

<img src="https://github.com/user-attachments/assets/fcdb80b0-23f2-4b76-8799-9d4b01958f46" width="650">

- Click: **Customize**
- Upload:
  - ✅ **Favicon** → Select your 32x32 logo image
  - ✅ **Background image** → Select your 1920x1080 background image
- Choose or confirm the **Page background color**
- Click: **Review + Create > Create**

---

## 🔹 Step 3: Test the Branding

![image](https://github.com/user-attachments/assets/9e3907b4-414e-483b-ba6a-5e362ed22869)


- Open: `https://login.microsoft.com`
- Sign in with: `balas@<organization-domain>.onmicrosoft.com`
- Confirm:
  - Custom **background image**
  - Custom **favicon/logo**
- Click: **Forgot my password**
  - Branding should appear on the reset page as well

<img src="https://github.com/user-attachments/assets/52525745-08ac-4e62-9101-78afb0506b1f" width="650">

---

## 📌 Key Notes for Exam

- Only **PNG or JPG** formats are allowed.
- Image sizes must not exceed:
  - Background: **300 KB**
  - Logo: **5 KB**
- Custom branding applies to:
  - Sign-in pages
  - Password reset pages
- Accessible through:  
  `Microsoft Entra ID > Company branding`

