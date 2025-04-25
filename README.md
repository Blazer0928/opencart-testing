# 🛒 OpenCart Functional Testing Repository

## 📌 Overview

This repository contains the functional testing artifacts for the **OpenCart e-commerce platform**, conducted on **April 24–25, 2025**.  
The goal was to validate core modules and ensure a seamless user experience across desktop and mobile platforms.

**Modules Covered**:  
Register, Login, Logout, Search, Home, Product Comparison, Cart, Checkout, My Account, Change Password, Contact Us.

---

## 📁 Repository Structure

opencart-functional-testing/ ├── docs/ # Test plan and summary report ├── test_cases/ # Test cases organized by module (e.g., register.md) ├── bug_reports/ # Bug report sheet and attachments (e.g., screenshots, logs) ├── scripts/ # Placeholder for automation or helper scripts ├── .gitignore # Ignores unnecessary files ├── README.md # Repository overview (this file)


---
---

## 🧪 Test Summary

### ✅ Execution Results
- **Total Test Cases**: 151  
  - ✔️ Pass: **119** (78.8%)  
  - ❌ Fail: **7** (4.6%)  
  - ⚠️ Inaccessible: **25** (16.6%)

### 🧱 Module-wise Breakdown

| Scenario ID | Module               | Test Cases |
|-------------|----------------------|------------|
| TS_001      | Register              | 16         |
| TS_002      | Login                 | 12         |
| TS_003      | Logout                | 8          |
| TS_004      | Search                | 25         |
| TS_005      | Home                  | 20         |
| TS_006      | Product Comparison    | 14         |
| TS_007      | Cart                  | 8          |
| TS_008      | Checkout              | 21         |
| TS_009      | My Account            | 7          |
| TS_010      | Change Password       | 11         |
| TS_011      | Contact Us            | 9          |

---

## 🐞 Key Findings

### 🔴 Critical Issues (P1)
- **REG-001**: Registration confirmation email not sent  
- **TC_CU_006**: Contact form submission fails due to email error  

### 🟠 Major Issues (P2)
- Incorrect success messages for cart with invalid quantities (`CART-002`, `CART-003`)  
- Missing logout confirmation prompt (`TC_LGOUT_006`)  
- Email not carried to password reset page (`TC_PWD_022`)  

### ⚠️ Inaccessible Cases
- 25 test cases, mainly `TC_PWD_001` to `TC_PWD_025`, failed due to **email system failure**

### 🟡 Minor Bugs (P3)
- Special character handling in registration  
- Inconsistent UI feedback in search functionality  
- **Security Risk**: Password visible in page source (`TC_FC_004`)  

### 🐛 Total Bugs Logged
- Critical: **2**  
- Major: **11**  
- Minor: **19**  
- **Total**: 32 bugs

---

## 🛠️ Recommendations

- **Resolve Email System Issues**:  
  Check SMTP settings in `System > Settings > Mail` and review server logs  
  → Retest: `REG-001`, `TC_PWD_001–025`, `TC_CU_006`, `TC_CU_009`

- **Fix Critical Bugs First**:  
  Focus on registration and contact form issues  

- **Re-execute Failed/Inaccessible Test Cases**  
  → 32 cases to be retested after bug fixes

- **Run Regression Testing**  
  → Validate passing tests like `TC_CKOUT_001–021` after fixes  

- **Next Steps**:  
  - Begin performance testing (load, stress)  
  - Consider automation for regression coverage  

---
> Load-Stree Test result are in This page:
<a href = "https://blazer0928.github.io/opencart-testing/">
> 💡 **Contributors are welcome** to improve test coverage, automate scripts, or suggest improvements!

