# Incident Report: Web Server Compromise & Malware Redirection

[![Web Security](https://img.shields.io/badge/Web_Security-Brute_Force-red?style=for-the-badge)](https://owasp.org/www-community/attacks/Brute_force_attack)
[![Malware Analysis](https://img.shields.io/badge/Malware-Payload_Delivery-darkred?style=for-the-badge)](https://attack.mitre.org/tactics/TA0002/)
[![Network Analysis](https://img.shields.io/badge/Network_Analysis-tcpdump-blue?style=for-the-badge)](https://www.tcpdump.org/)

## 📌 Incident Summary
Customers of the corporate portal *yummyrecipesforme.com* reported that after visiting the website, they were prompted to download a file to access free recipes. Upon execution, the file caused system performance degradation and forcefully redirected their browsers to a different, untrusted website. Simultaneously, the website owner reported losing access to the backend administrative panel.

---

## 🔍 Investigation Findings
A forensic analysis of the web server and network traffic revealed the complete attack chain:

* **Attack Vector (Initial Access):** A former employee executed a brute-force attack against the website's administrative login page. The attack succeeded because the default administrative password had never been changed, and the server lacked rate-limiting controls.
* **Payload (Execution):** Once authenticated as an administrator, the threat actor altered the website's source code by embedding a malicious JavaScript function. This script prompted visitors to download a fake "browser update" executable. 
* **Persistence & Denial of Service:** The attacker subsequently changed the admin password, completely locking out the legitimate owner and preventing immediate remediation.

---

## 📡 Network Protocol Analysis
Based on the `tcpdump` traffic logs and sandbox execution of the payload, the following network protocols were actively utilized during the incident:

* **DNS (Domain Name System - Port 53):** Identified when the compromised client requested IP resolution for the legitimate domain (`yummyrecipesforme.com`) and later for the malicious domain (`greatrecipesforme.com`).
* **HTTP (Hypertext Transfer Protocol - Port 80):** Identified when the browser requested the webpage (`GET / HTTP/1.1`) and initiated the download of the malicious executable file.
* **TCP (Transmission Control Protocol):** Identified by the `Flags [S]` (SYN) and `[.]` (ACK) indicating the connection handshakes between the client and both the legitimate and malicious web servers.

---

## 🔬 Evidence and Traffic Log Analysis

### 1. Initial Legitimate Traffic
The `tcpdump` logs initially show the user's machine making a normal DNS request for the legitimate website (`yummyrecipesforme.com`) and receiving the correct IP address (`203.0.113.22`):

![Initial DNS Request](yummy-dns-request.png)

### 2. Malicious Redirection
After the payload is executed, the logs show the browser being forced to make a new DNS request for the attacker's domain (`greatrecipesforme.com`). It resolves to a different IP (`192.0.2.17`), followed immediately by anomalous HTTP traffic directed to this malicious server:

![Malicious Redirection](greatrecipesforme.png)

### 📎 Artifacts
* [Download the full tcpdump traffic log](tcpdump%20registro%20de%20tr%C3%A1fico.pdf)

---

## 🛡️ Remediation & Mitigation Strategy
To resolve the vulnerability that facilitated this compromise, the organization must implement the following security controls:

1. **Account Lockout Policies (Rate Limiting):** Implement a strict lockout policy that limits the number of failed login attempts. For example, after 3 to 5 incorrect password attempts, the account or the originating IP address should be temporarily locked for 30 minutes. This makes brute-forcing mathematically impractical by halting the automated guessing process.
2. **Disable Default Credentials:** As a mandatory baseline configuration, the system must force administrators to change default passwords upon their first login.
3. **Enforce Password Complexity:** Implement Identity and Access Management (IAM) policies requiring minimum length, alphanumeric characters, and symbols to ensure resistance against dictionary attacks.
