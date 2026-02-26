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

```bash
sudo service apache2 start
sudo service mysql start
```
<img width="1920" height="922" alt="image" src="https://github.com/user-attachments/assets/d0c54ee1-e70f-4ca9-8f77-04b3ed6f1843" />

----
### Step 2: Open DVWA in browser
Open firefox and navigate to:

http://127.0.0.1/DVWA

Login using :

Username : admin
Password : password

<img width="1920" height="922" alt="image" src="https://github.com/user-attachments/assets/b2f7749c-5c68-4eee-9316-5ccfacb94c61" />

<img width="1920" height="922" alt="image" src="https://github.com/user-attachments/assets/31207ecd-1bcd-45be-8165-2802cd384171" />

------
### Step 3: Set security level to low
1. Click on DVWA security
2. Select Low
3. Click Submit
This ensures vulnerabilities are enabled for demonstration purposes

<img width="1920" height="922" alt="image" src="https://github.com/user-attachments/assets/9c43af1c-4d98-4b71-8010-81d90d86a7ec" />

----

### Step 4: Configure Browser Proxy for Burp Suite
Go to:
Settings → Network Settings → Manual Proxy Configuration

Set the following:

HTTP Proxy: 127.0.0.1
Port: 8080
This routes browser traffic through Burp Suite.

<img width="1920" height="922" alt="image" src="https://github.com/user-attachments/assets/0b21170c-8865-44e3-b990-2147e87b1b07" />


------
### Step 5: Enable Intercept in Burp Suite
Open Burp Suite Community Edition
Navigate to:

Proxy -> Intercept

Turn Intercept ON
Burp will now capture HTTP requests before they reach the server.
<img width="1920" height="922" alt="image" src="https://github.com/user-attachments/assets/4f2a1edf-2753-4f3c-a03b-8312df01f082" />

<img width="1920" height="922" alt="image" src="https://github.com/user-attachments/assets/13e2ada1-2e19-409e-864b-4d61fe5de7ec" />

<img width="1920" height="922" alt="image" src="https://github.com/user-attachments/assets/b9f7a249-517b-4117-bf1f-bd8cd9cf8e57" />

<img width="1920" height="922" alt="image" src="https://github.com/user-attachments/assets/bb957838-4cb0-4eaa-bb00-c4084e4d6b5f" />


<img width="1920" height="922" alt="image" src="https://github.com/user-attachments/assets/ab3eb59c-7638-4345-a9da-fcc8dc9ff3d4" />

------
### Step 6: Intercept Login Request
Logout from DVWA
Login again using:
Username: admin   
Password: password

Burp will intercept the POST request

Captured request body:
username=admin&password=password&Login=Login

<img width="1920" height="922" alt="image" src="https://github.com/user-attachments/assets/971b228f-30e1-406f-b2be-4f3fdec455a7" />


------
### Observation:
The credentials are transmitted in plain text because the application uses HTTP instead of HTTPS.

<img width="1920" height="922" alt="image" src="https://github.com/user-attachments/assets/ada65ba8-3f67-48f9-8ed1-6e971e22793c" />


-----
### Step 7: Perform Request Tampering
Before forwarding the intercepted request:
Modify:
password=password

To:
password=wrong
Click Forward.

<img width="1920" height="922" alt="image" src="https://github.com/user-attachments/assets/8d2b8e9b-bfb8-4f1f-87e5-01cb91cbb533" />


-----
### Step 8: Observe Authentication Failure
After modifying the password, login fails.

This confirms that:
- HTTP parameters can be modified in transit
- Server processes manipulated input
- Request tampering is possible without encryption

<img width="1920" height="922" alt="image" src="https://github.com/user-attachments/assets/4ebb937b-7307-4813-8626-7313118dc51e" />


-----
### Security Findings
* Login credentials transmitted in plain text
* Authentication request can be intercepted
* HTTP parameters can be modified
* No encryption protection
* Session configuration visible in cookies

------
### Security Risks
* If deployed without HTTPS:
* Credentials can be captured via packet sniffing
* Man-in-the-Middle (MITM) attacks possible
* Session hijacking risks
* Data tampering during transmission

------
### Recommended Prevention Techniques
* Implement HTTPS (TLS encryption)
* Use secure and HttpOnly cookies
* Apply strict server-side validation
* Implement strong authentication mechanisms
* Use prepared statements for database queries
* Enforce secure session management

-------
### Learning Outcomes
* Understanding HTTP request structure
* Using Burp Suite for traffic interception
* Performing request tampering
* Identifying insecure authentication mechanisms
* Understanding application-layer vulnerabilities

-----

### Video Walkthrough
Linkedin link : 
https://www.linkedin.com/posts/tejasri-somarouthu-78aa83355_cybersecurity-websecurity-burpsuite-activity-7432472776881500160-1dT2?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAFidKJoBRLvumfdgwfmIDItuHoJpdXkBZuI

-------
### Conclusion
This experiment demonstrates how web applications can be vulnerable to interception and request tampering when secure communication protocols are not implemented.
It highlights the importance of encryption, validation, and secure session handling in modern web applications.

-----
👩‍💻Name : S. Tejasri

Intern : Cybersecurity & Ethical hacking


