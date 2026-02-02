# idor-password-disclosure-lab
A detailed security lab write-up demonstrating an IDOR vulnerability leading to administrator password disclosure. Performed on PortSwigger Web Security Academy, covering exploitation steps, impact analysis, and mitigation recommendations.

# User ID Controlled by Request Parameter – Password Disclosure

![Platform](https://img.shields.io/badge/Platform-PortSwigger-red)
![Category](https://img.shields.io/badge/Category-Broken%20Access%20Control-blue)
![Level](https://img.shields.io/badge/Level-Apprentice-green)
![Focus](https://img.shields.io/badge/Focus-Offensive%20Security-black)

## 📌 Overview
This repository contains a detailed security lab write-up for the **“User ID controlled by request parameter with password disclosure”** lab from the **PortSwigger Web Security Academy**.

The lab demonstrates a critical **Insecure Direct Object Reference (IDOR)** vulnerability combined with **poor credential handling**, allowing an attacker to retrieve the **administrator’s password** by manipulating a user-controlled request parameter.

---

## 🎯 Lab Objectives
- Log in as a normal user
- Identify and exploit user ID manipulation in request parameters
- Retrieve the administrator’s password
- Gain administrator access
- Delete the user **carlos** to complete the lab

---

## 🧠 Vulnerability Summary
**Vulnerability Types:**
- Broken Access Control (IDOR)
- Sensitive Data Exposure
- Credential Disclosure

**Description:**
The application pre-fills the user’s existing password in a masked HTML input field. By changing the `id` parameter in the account request, an attacker can access another user’s account details — including the administrator’s password — without proper authorization.

> Masked password fields (`type="password"`) do **not** provide security, as values remain visible in the HTML source and HTTP response.

---

## 🛠 Tools & Environment
- Web Browser (Chrome / Firefox)
- Burp Suite (Proxy / Repeater)
- PortSwigger Web Security Academy Lab Environment

---

## 👤 Test Accounts
| Username | Password | Role |
|--------|----------|------|
| wiener | peter | Normal User |
| administrator | Retrieved | Admin |

---

## 🔓 Step-by-Step Exploitation

### Step 1: Log in as Normal User
Log in using:
- **Username:** wiener  
- **Password:** peter  

Navigate to the **My Account** page.

---

### Step 2: Manipulate User ID Parameter
Modify the account page URL:



---

### Step 3: Intercept the Response
Use Burp Suite to inspect the HTTP response.  
The administrator’s password is embedded in a masked input field.

---

### Step 4: Reveal the Password
Inspect the HTML and change:
```html
type="password"

