# 🛡️ OpenCart Vulnerability Report (Nikto Scan)

## Input validation
1. Cross-Site Scripting (XSS)
- Where:  User profile fields, search bars, comments, product reviews, etc.
- If OpenCart doesn't properly escape user input in these fields, an attacker might inject a malicious script that executes when other users load the page.

2. SQL Injection (SQLi)
- Where: Login forms, search functionality, URL parameters, or admin panel queries. 

- Example: If OpenCart doesn't sanitize inputs correctly in login forms, an attacker might exploit it by entering SQL injection payloads like ' OR 1=1 -- to bypass authentication. 

3.  Insecure Direct Object References (IDOR)
- Where: URLs with object IDs, such as viewing other users’ orders.
- Example: If OpenCart doesn't properly check for user ownership of resources, attackers could modify order IDs or user IDs in the URL (e.g., order.php?id=1234) to view someone else’s data.
4. Cross-Site Request Forgery (CSRF)
- Where: Forms that modify user data (e.g., change password, change email).

- Example: Without proper CSRF protection, an attacker could trick a logged-in user into submitting a request (like changing their email or password) without their consent.

-      All of the common input validation vulnerabilities mentioned are relevant to OpenCart, especially in areas like user registration, login, product search, file uploads, and the admin panel. Proper validation and security measures need to be in place to mitigate these risks.

- The Report in html (nikto scan)[https://Blazer0928.github.io/opencart-testing/security_report]

**Scan Date**: April 26, 2025  
**Target**: `http://localhost:80/opencart/` (127.0.0.1:80)  
**Web Server**: Apache/2.4.58 (Unix) OpenSSL/1.1.1w PHP/8.1.25 mod_perl/2.0.12 Perl/v5.34.1  
**Scan Duration**: 20 seconds  
**Requests Made**: 7471  
**Findings**: 27

---

## 📋 Summary of Findings

| # | Vulnerability | Description | Risk Level |
|:-|:--------------|:-------------|:----------|
| 1 | X-Powered-By Header Disclosure | Server reveals PHP version (8.1.25). | Info Leakage |
| 2 | Access-Control-Allow-Origin: * | All origins are allowed. | Medium |
| 3 | Missing X-Frame-Options Header | No clickjacking protection. | High |
| 4 | Missing X-Content-Type-Options Header | MIME-type sniffing possible. | Medium |
| 5 | Cookies without HttpOnly Flag (OCSESSID, currency) | Cookies accessible to JavaScript. | Medium |
| 6 | /robots.txt Exposes Directories | 16 entries to explore manually. | Low |
| 7 | Apache mod_negotiation Enabled (MultiViews) | File brute-forcing possible. | Medium |
| 8 | Outdated OpenSSL Version | OpenSSL 1.1.1w detected (latest is 3.x). | Medium |
| 9 | HTTP TRACE Method Enabled | Vulnerable to Cross Site Tracing (XST). | High |
| 10 | Allowed Methods Include TRACE | Bad practice for web servers. | Medium |
| 11 | Response to Unknown HTTP Methods | Server responds to invalid methods. | Medium |
| 12 | Exposed Config Files (`config.php`, `admin/config.php`) | May contain DB credentials. | Critical |
| 13 | Directory Listing Enabled (`/system/`, `/tools/`, `/image/`, `/docs/`) | Sensitive folders browsable. | High |
| 14 | Composer Files Exposed (`composer.json`, `composer.lock`) | Shows dependencies and possibly vulnerabilities. | Medium |
| 15 | `.gitignore` File Found | Directory structure exposed. | Low |
| 16 | `Dockerfile` Exposed | Server/container setup details leaked. | Medium |
| 17 | `README.md` Exposed | Might reveal sensitive installation information. | Info |

---

## 🔍 Detailed Findings

### 1. X-Powered-By Header Disclosure
- **Risk**: Shows PHP version (`PHP/8.1.25`), helping attackers target known vulnerabilities.
- **Fix**: Remove or obfuscate the `X-Powered-By` header.

### 2. Access-Control-Allow-Origin: *
- **Risk**: Anyone can make cross-origin requests to your server.
- **Fix**: Restrict CORS policy to trusted domains.

### 3. Missing X-Frame-Options Header
- **Risk**: Susceptible to Clickjacking attacks.
- **Fix**: Set `X-Frame-Options: SAMEORIGIN` or use CSP frame-ancestors.

### 4. Missing X-Content-Type-Options Header
- **Risk**: MIME sniffing can lead to XSS vulnerabilities.
- **Fix**: Set `X-Content-Type-Options: nosniff`.

### 5. Cookies without HttpOnly Flag
- **Risk**: Cookies can be stolen via client-side scripts.
- **Fix**: Set `HttpOnly` attribute for session cookies.

### 6. robots.txt Exposes Sensitive Paths
- **Risk**: Attackers can find sensitive directories easily.
- **Fix**: Only disallow paths that aren't sensitive, avoid revealing structure.

### 7. Apache mod_negotiation Enabled
- **Risk**: Allows filename guessing via MultiViews.
- **Fix**: Disable `MultiViews` option in Apache configs.

### 8. Outdated OpenSSL Version
- **Risk**: OpenSSL 1.1.1w may have security issues, support is ending.
- **Fix**: Upgrade to OpenSSL 3.x.

### 9. HTTP TRACE Method Enabled (XST)
- **Risk**: Vulnerable to Cross-Site Tracing (XST) attacks.
- **Fix**: Disable TRACE method in Apache/Nginx.

### 10. Allowed Methods Include TRACE
- **Risk**: Server allows dangerous HTTP methods.
- **Fix**: Restrict allowed HTTP methods to GET, POST, HEAD.

### 11. Response to Unknown HTTP Methods
- **Risk**: Weird methods accepted, potential WAF bypass testing.
- **Fix**: Strictly validate HTTP methods.

### 12. Exposed Config Files (`config.php`, `admin/config.php`)
- **Risk**: May reveal database credentials.
- **Fix**: Move sensitive files outside the webroot or protect with .htaccess.

### 13. Directory Listing Enabled
- **Risk**: Allows browsing sensitive server directories.
- **Fix**: Disable `Indexes` option in Apache.

### 14. Exposed Composer Files
- **Risk**: Exposed dependency versions can reveal vulnerable libraries.
- **Fix**: Move `composer.json` and `composer.lock` outside public directories.

### 15. `.gitignore` File Found
- **Risk**: Gives away directory structure information.
- **Fix**: Prevent `.git` related files from being exposed publicly.

### 16. Dockerfile Exposed
- **Risk**: Leaks server and app setup details.
- **Fix**: Restrict access to Dockerfile or move it outside webroot.

### 17. README.md Exposed
- **Risk**: May expose installation steps or software versions.
- **Fix**: Sanitize public documentation before deploying.

---

## 📚 References

- [OWASP Secure Headers Project](https://owasp.org/www-project-secure-headers/)
- [OWASP Cross-Site Tracing (XST)](https://owasp.org/www-community/attacks/Cross_Site_Tracing)
- [Apache Hardening Guide](https://httpd.apache.org/docs/current/misc/security_tips.html)
- [MIME Sniffing Protection](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Content-Type-Options)
- [robots.txt Security Risks](https://developer.mozilla.org/en-US/docs/Glossary/Robots.txt)

---

# 🚀 Recommendations Summary
- Upgrade OpenSSL version.
- Disable HTTP TRACE method.
- Implement secure HTTP headers.
- Secure sensitive files and directories.
- Regularly update OpenCart and server components.

