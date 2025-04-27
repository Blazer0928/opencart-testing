# 🧾 OpenCart Functional Testing Summary Report

## 📌 Overview

This report summarizes the functional testing of the OpenCart e-commerce platform, conducted on **April 24–25, 2025**. Testing covered 11 key modules:

> Register, Login, Logout, Search, Home, Product Comparison, Cart, Checkout, My Account, Change Password, and Contact Us.

---

## 🧪 Test Execution

- **Total Test Cases**: 151  
- **Status**:
  - ✅ Pass: **119** (78.8%)  
  - ❌ Fail: **7** (4.6%)  
  - ⚠️ Inaccessible: **25** (16.6%)  

### 🧱 Modules Tested

| Module              | Test Cases |
|---------------------|------------|
| Register            | 16         |
| Login               | 12         |
| Logout              | 8          |
| Search              | 25         |
| Home                | 20         |
| Product Comparison  | 14         |
| Cart                | 8          |
| Checkout            | 21         |
| My Account          | 7          |
| Change Password     | 11         |
| Contact Us          | 9          |

---

## 🚨 Key Findings

### 🔴 Critical Issues (P1)
- **Registration confirmation email not sent**  
  - ID: `REG-001`, Bug: `BUG_001`
- **Contact form submission fails (email error)**  
  - ID: `TC_CU_006`, Bug: `BUG_006`

### 🟠 Major Issues (P2)
- Incorrect success messages for invalid cart quantities  
  - IDs: `CART-002`, `CART-003`
- No logout confirmation prompt  
  - ID: `TC_LGOUT_006`
- Email not carried to password reset page  
  - ID: `TC_PWD_022`

### ⚠️ Inaccessible Test Cases
- **25 test cases**, mainly under **Change Password** (`TC_PWD_001` to `TC_PWD_025`), failed due to **email system issues**.

---

## 🐞 Total Bugs Logged

- **Critical (P1)**: 2  
- **Major (P2)**: 11  
- **Minor (P3)**: 19  
- **Total**: **32 Bugs**

---

## 🛠️ Recommendations

### 📨 Resolve Email System Issues
- Investigate SMTP config (`System > Settings > Mail`) & check server logs.
- Retest: `REG-001`, `TC_PWD_001–025`, `TC_CU_006`, `TC_CU_009`.

### 🛑 Fix Critical Bugs First
- Prioritize: `REG-001` and `TC_CU_006`.

### 🔁 Re-execute Failed & Inaccessible Test Cases
- Total of **32 test cases** need retesting post-fix.

### 🔄 Regression Testing
- Revalidate previously passed cases (e.g., `TC_CKOUT_001–021`).

### 🧪 Next Steps
- Begin **performance testing** (load/stress) after resolving critical bugs.
- Consider **automation** for regression testing workflows.

---



