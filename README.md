# 🛒 OpenCart  Testing Repository

## 📌 Objective
Document various types testing and store results for **OpenCart**, conducted April 24–27, 2025.

1. Functional Testing
2. UI-UX Testing
3. Load-Stress Testing
4. API Testing
5. Security Testing

---

## 🧪 Test Results

| Metric              | Value         |
|---------------------|---------------|
| **Total Test Cases** | 151           |
| **Pass**             | 119 (78.8%)   |
| **Fail**             | 7 (4.6%)      |
| **Inaccessible**     | 25 (16.6%)    |
| **Bugs Logged**      | 32            |

### 🐞 Bugs Categorization

| Severity  | Count |  
|-----------|-------|
| Critical (P3) | 19 |
| Major (P2)    | 11 |
| Minor (P1)    | 2  |

### ✅ Modules Tested
- Register
- Login
- Logout
- Search
- Home
- Product Comparison
- Cart
- Checkout
- My Account
- Change Password
- Contact Us

---

## 🔍 Key Findings

### 🔴 Critical Issues (P3)
- Special characters allowed in registration (`REG-007`)
- Password visible in page source (`TC_FC_004`)
- Search by description/category fails (`TC_SRCH_008`, `TC_SRCH_009`)

### 🟠 Major Issues (P2)
- Invalid cart quantity shows success (`CART-002`, `CART-003`)
- No logout confirmation (`TC_LGOUT_006`)
- Email not pre-filled on password reset page (`TC_PWD_022`)

### ⚠️ Inaccessible Cases
- 25 test cases (e.g., `TC_PWD_001–TC_PWD_025`) due to email system failure

### 🟡 Minor Issues (P1)
- Registration email not sent (`REG-001`)
- Contact form submission fails (`TC_CU_006`)

---

## 🛠️ Recommendations
- Fix the email system (review SMTP settings, check server logs).
- Prioritize fixing critical bugs (`REG-007`, `TC_FC_004`, `TC_SRCH_008`).
- Retest all 32 failed/inaccessible test cases.
- Validate passing test cases through regression testing.

---

## 📂 Repository Structure

- -> Test_cases contains the Functional/UI-UX test cases
- -> Bug-Report directory have the Bug-Report sheet attached to it.
- -> api-testing directory contain the postman json configuration file and API_TESTING_readme.md file for walkthrough
- -> docs directory have the Load testing results
- -> Load_Stree_testing directory contains the load and stress test configuration in .jmx format


## Load-Stress Testing
- The report statistics for stress testing with 100 users [https://blazer0928.github.io/opencart-testing/stress_report]
- The repost statistics for Load testiing with 50 users [https://blazer0928.github.io/opencart-testing/load_report]


## Security Report 
- using a automated vulnerability tester for Security analysis. I used tool called "nikto".
- The report is attached here [https://blazer0928.github.io/opencart-testing/security_report]


