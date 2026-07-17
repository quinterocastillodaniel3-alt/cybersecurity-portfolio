# Incident Report: TCP SYN Flood (Denial of Service)

[![Attack Vector](https://img.shields.io/badge/Attack_Vector-SYN_Flood-red?style=for-the-badge)](https://attack.mitre.org/techniques/T1498/001/)
[![Protocol](https://img.shields.io/badge/Protocol-TCP-blue?style=for-the-badge)](https://en.wikipedia.org/wiki/Transmission_Control_Protocol)
[![Network Security](https://img.shields.io/badge/Domain-Network_Security-darkgreen?style=for-the-badge)](https://www.cisa.gov/news-events/news/understanding-denial-service-attacks)

## 📌 Incident Summary
A corporate travel website experienced a critical service outage, resulting in "Connection Timeout" errors for legitimate employees and customers. A network traffic analysis revealed that the web server (`192.0.2.1`) was the victim of a targeted **Denial of Service (DoS)** attack, specifically a **TCP SYN Flood**, designed to exhaust the server's connection resources and disrupt business operations.

---

## ⚙️ Technical Analysis: The Attack Mechanism

To understand how the attack caused the malfunction, it is necessary to contrast normal network behavior with the attacker's methodology.

### 1. Normal TCP 3-Way Handshake
When legitimate visitors establish a connection with the web server, the Transmission Control Protocol (TCP) executes a three-step handshake:
1. **SYN (Synchronize):** The client sends a SYN packet to request a connection.
2. **SYN-ACK (Synchronize-Acknowledge):** The server allocates resources (memory in its backlog queue) and replies with a SYN-ACK packet.
3. **ACK (Acknowledge):** The client replies with an ACK packet. The connection is established, and data (like HTTP requests) can flow.

### 2. The SYN Flood Exploitation
During this incident, the threat actor manipulated this foundational protocol:
* The attacker sent an abnormally high, continuous stream of SYN requests to the server's port 443 (HTTPS).
* The server dutifully responded with SYN-ACK packets and allocated memory for each request, waiting for the final ACK confirmation.
* The attacker intentionally ignored the SYN-ACK responses (or utilized spoofed IP addresses, sending the server's responses into a void). 

**The Impact:** The server was forced to leave thousands of "half-open" connections in its backlog queue. Once this queue reached maximum capacity, the server dropped all new, legitimate connection requests from the travel agency's users, resulting in the reported connection timeouts.

---

## 🔬 Evidence and Traffic Log Analysis

### Normal Traffic Pattern
Prior to the incident, network logs confirm legitimate users successfully completing the TCP 3-way handshake (`SYN`, `SYN-ACK`, `ACK`) and requesting the sales webpage:

![Normal Traffic Handshake](normal-traffic.png)

### Attack Traffic Pattern (SYN Flood)
During the incident window, the logs indicate a massive flood of `SYN` requests originating from a single unknown IP address (`203.0.113.0`). The complete absence of `ACK` packets from this IP confirms the malicious intent to exhaust server resources:

![SYN Flood Attack Activity](syn-flood-attack.png)

### 📎 Artifacts
* [Download the full Wireshark TCP log (Excel)](HTTP-log.xlsx)

---

## 🛡️ Recommended Mitigation Strategies
To prevent future SYN Flood attacks from taking the web server offline, the following network hardening controls should be implemented:
* **Enable SYN Cookies:** Configure the server's operating system to utilize cryptographic SYN cookies, allowing the server to avoid allocating memory for a connection until the final ACK is received.
* **Firewall Rate Limiting:** Configure the perimeter firewall or Intrusion Prevention System (IPS) to limit the number of SYN packets accepted from a single IP address within a specific timeframe.
* **Reduce SYN Timeout:** Lower the amount of time the server keeps half-open connections in its backlog queue before dropping them.
