
# 📊 OpenCart Load & Stress Testing Report

This report documents **load and stress testing** conducted on a local instance of the OpenCart e-commerce platform using **Apache JMeter 5.6.3**. The objective was to assess performance under increasing user load and identify any bottlenecks or failures in the system.

---

## 📌 Test Metadata

| Field              | Details                        |
|--------------------|--------------------------------|
| **Tool**           | Apache JMeter 5.6.3            |
| **Platform**       | OpenCart (local instance)      |
| **Test File**      | `loadtesting_result.jtl`       |
| **Test Duration**  | 25/04/25, 2:44 pm – 2:46 pm     |
| **Users Simulated**| 50 (Load), 100 (Stress)        |
| **Checkout Type**  | Guest Checkout                 |
| **Product Tested** | Product ID 43                  |

---

## 🧪 Test Flow (Simulated User Actions)

1. **Browse Homepage**  
2. **View Product (ID: 43)**  
3. **Add to Cart** (POST with product ID, quantity)  
4. **View Cart**  
5. **Start Checkout**  
6. **Guest Checkout** (POST with user details)

---

## 📈 Results Overview

- **Load Test**: 50 users, 50-second ramp-up  
- **Stress Test**: 100 users, 100-second ramp-up  
- **Timings**: 2000–3000 ms between actions  

> **View full HTML dashboards:**

> - 📈 [View Load Report](https://Blazer0928.github.io/opencart-testing/docs/load_report/index.html)
> - 📈 [View Stress Report](https://Blazer0928.github.io/opencart-testing/docs/load_report_stress/index.html)
---

## 📉 Key Performance Insights

### ✅ Test Summary

| Metric                  | Value                    |
|--------------------------|--------------------------|
| **Total Duration**       | ~2 minutes               |
| **Success Rate**         | Majority successful      |
| **Guest Checkout Errors**| Detected (404/500)       |

### 📊 Dashboard Highlights

- 📌 **Requests Summary**: Pie chart of successful vs. failed requests  
- ⚡ **Response Time Trends**: Response time breakdown per action  
- 📈 **Throughput**: Transactions per second  
- 🔍 **Top Errors**: Most failing endpoints and error codes  
- 🧮 **APDEX Score**: Application performance index (user satisfaction)

---

## 🐞 Notable Errors

- **Guest Checkout**
  - ❌ 404 Error (invalid/missing route)
  - 🔧 May need CSRF token or correct parameters

- **Add to Cart**
  - ❌ 500 Internal Server Error
  - 📌 Check request method (POST) and parameter integrity

---

## 🔧 Troubleshooting Recommendations

- ✅ **Verify Routes** in browser (`/index.php?route=checkout/guest`)  
- ✅ **Check CSRF Tokens** – use Regex Extractor in JMeter if needed  
- ✅ **Enable Guest Checkout** in OpenCart Admin settings  
- ✅ **Review Logs**:  
  `/opencart/system/storage/logs/error.log`  

---

## 📂 Resources & Artifacts

| File/Directory                      | Description                                         |
|-------------------------------------|-----------------------------------------------------|
| `opencart_local_test.jmx`          | JMeter test plan (load & stress groups)            |
| `load_results.jtl`                 | Load test raw output                                |
| `stress_results.jtl`               | Stress test raw output                              |
| `Load_stress_testing/load_report/` | HTML dashboard for load test                        |
| `Load_stress_testing/load_report_stress/` | HTML dashboard for stress test              |

---

## 🎯 Performance Goals

- ⏱️ **Response Time**: < 500ms for all endpoints  
- ❌ **Error Rate**: 0% (ideal)  
- 📊 **Throughput**: Stable at both 50 and 100 concurrent users

---

## 📬 Need Help?

If you encounter issues or want assistance analyzing the results:

- Share screenshots from the HTML report (charts, errors)
- Provide URLs that failed in JMeter (View Results Tree)
- Attach `error.log` and OpenCart version
- Confirm Guest Checkout status in admin panel

---

## 📈 Quick Links

 
> - 📈 [View Load Report](https://Blazer0928.github.io/opencart-testing/docs/load_report/index.html)
> - 📈 [View Stress Report](https://Blazer0928.github.io/opencart-testing/docs/load_report_stress/index.html)

---

**🧪 Happy Testing!**  
Optimize performance, debug smartly, and keep OpenCart lightning fast 🚀.
