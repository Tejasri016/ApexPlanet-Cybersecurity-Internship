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

`bash
sudo service apache2 start
sudo service mysql start

### Step 2: Open DVWA in browser

