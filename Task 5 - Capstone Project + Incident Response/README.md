# 🔐 Web Application Penetration Testing & Incident Response using DVWA

---

## 📌 Project Overview

This project demonstrates an end-to-end **Web Application Penetration Testing and Incident Response process** using **DVWA (Damn Vulnerable Web Application)** in a controlled lab environment.

The objective of this project was to:

- Simulate real-world web application attacks
- Identify common vulnerabilities
- Exploit vulnerabilities in a safe lab
- Perform structured incident detection and response
- Apply mitigation techniques

This project was completed as the **Final Capstone Task** of my Cybersecurity & Ethical Hacking Internship.

---

## 🛠 Lab Environment

- **Operating System:** Kali Linux
- **Target Application:** DVWA (Damn Vulnerable Web Application)
- **Web Server:** Apache2
- **Database:** MariaDB
- **Testing Tool:** Browser + Manual Testing
- **Security Levels Tested:** Low / Medium / High

---

## 🔎 Phase 1: Reconnaissance & Enumeration

* Command used:

```bash
nmap -sV 127.0.0.1
````

### Findings:

* Identified open ports

* Detected Apache running on port 80

* Confirmed web application exposure

## 💥 Phase 2: Exploitation
### 1️⃣ SQL Injection

* Demonstrated authentication bypass

* Retrieved database records

* Showed impact of improper input validation

### 2️⃣ File Upload Vulnerability

* Uploaded malicious PHP file

* Demonstrated Remote Code Execution risk

* Highlighted insecure file handling

### 3️⃣ Weak Authentication Testing

* Tested basic brute-force scenarios

* Identified lack of rate limiting

## 🚨 Phase 3: Incident Detection & Response
### 🔍 Detection

* Analyzed Apache access logs:

```bash
cat /var/log/apache2/access.log
````

* Identified suspicious requests

* Observed malicious patterns in logs

### 🛑 Containment

* Blocked attacker IP using firewall:

```bash
ufw deny from 127.0.0.1
```

### 🔧 Eradication

* Applied secure coding practices

* Increased DVWA security level

* Implemented input validation strategies

### 🔄 Recovery

* Restarted services

* Retested application to confirm mitigation

* Validated system stability after patching

## 🧠 Key Concepts Applied

- Web Application Architecture

- HTTP Protocol & Request Handling

- SQL Injection Mechanics

- File Handling Vulnerabilities

- Secure Coding Principles

- Incident Response Lifecycle

- Detection

- Containment

- Eradication

- Recovery

## 📈 Learning Outcomes

- Practical exposure to offensive security techniques

- Understanding of defensive security mechanisms

- Log monitoring and analysis
  
- Risk assessment and mitigation planning

- Hands-on implementation of incident response

## ⚠ Disclaimer

This project was performed in a controlled lab environment for educational purposes only.

No unauthorized systems were targeted.

## Video Walkthrough
Linkenin Link :

https://www.linkedin.com/posts/tejasri-somarouthu-78aa83355_cybersecurity-cse-penetrationtesting-activity-7433333328193183744-s_5U?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAFidKJoBRLvumfdgwfmIDItuHoJpdXkBZuI

## 📬 Author

Name: Your Name

Course: B.Tech CSE

Focus Area: Cybersecurity & Application Security
