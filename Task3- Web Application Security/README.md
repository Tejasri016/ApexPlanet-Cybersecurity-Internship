# 🔐 Web Application Security Testing using DVWA & Burp Suite

## 📌 Project Overview

This project demonstrates practical Web Application Security Testing using:

- 🐞 Damn Vulnerable Web Application (DVWA)
- 🔍 Burp Suite Community Edition
- 🐧 Kali Linux
- 🌐 Firefox Browser

The objective of this experiment is to analyze HTTP authentication traffic and demonstrate how login credentials can be intercepted and modified using a proxy-based attack approach.

This project is performed in a controlled lab environment for educational purposes only.

---

##  Tools & Technologies Used

| Tool | Description |
|------|-------------|
| DVWA | Intentionally vulnerable web application |
| Burp Suite | Web proxy tool for intercepting & modifying HTTP requests |
| Kali Linux | Penetration testing operating system| Apache2 | Web server |
| MySQL | Database server |
| Firefox | Web browser for testing |

---

##  Environment Setup

###  Step 1: Start Required Services

Open terminal in Kali Linux and run:

---bash
sudo service apache2 start
sudo service mysql start

### Step 2: Open DVWA in browser
Open firefox and navigate to:

http://127.0.0.1/DVWA

Login using :

Username : admin
Password : password

screenshots/dvwa_home.png

### Step 3: Set security level to low
1. Click on DVWA security
2. Select Low
3. Click Submit
This ensures vulnerabilities are enabled for demonstration purposes

screenshots/security_low.png

Step 4: Configure Browser Proxy for Burp Suite
Go to:
Settings → Network Settings → Manual Proxy Configuration

Set the following:

HTTP Proxy: 127.0.0.1
Port: 8080
This routes browser traffic through Burp Suite.

screenshots/proxy_config.png

### Step 5: Enable Intercept in Burp Suite
Open Burp Suite Community Edition
Navigate to:

Proxy -> Intercept

Turn Intercept ON
Burp will now capture HTTP requests before they reach the server.

screenshots/intercept_request.png

### Step 6: Intercept Login Request
Logout from DVWA
Login again using:
Username: admin
Password: password

Burp will intercept the POST request

Captured request body:
username=admin&password=password&Login=Login

### Observation:
The credentials are transmitted in plain text because the application uses HTTP instead of HTTPS.

screenshots/credentials_visible.png

### Step 7: Perform Request Tampering
Before forwarding the intercepted request:
Modify:
password=password

To:
password=wrongpass
Click Forward.

screenshots/password_modified.png

### Step 8: Observe Authentication Failure
After modifying the password, login fails.

This confirms that:
- HTTP parameters can be modified in transit
- Server processes manipulated input
- Request tampering is possible without encryption

screenshots/8_login_failed.png

### Security Findings
* Login credentials transmitted in plain text
* Authentication request can be intercepted
* HTTP parameters can be modified
* No encryption protection
* Session configuration visible in cookies

### Security Risks
* If deployed without HTTPS:
* Credentials can be captured via packet sniffing
* Man-in-the-Middle (MITM) attacks possible
* Session hijacking risks
* Data tampering during transmission

### Recommended Prevention Techniques
* Implement HTTPS (TLS encryption)
* Use secure and HttpOnly cookies
* Apply strict server-side validation
* Implement strong authentication mechanisms
* Use prepared statements for database queries
* Enforce secure session management

### Learning Outcomes
* Understanding HTTP request structure
* Using Burp Suite for traffic interception
* Performing request tampering
* Identifying insecure authentication mechanisms
* Understanding application-layer vulnerabilities

### Conclusion
This experiment demonstrates how web applications can be vulnerable to interception and request tampering when secure communication protocols are not implemented.
It highlights the importance of encryption, validation, and secure session handling in modern web applications.

