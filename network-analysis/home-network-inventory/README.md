# Network Incident Analysis: DNS & ICMP Troubleshooting

[![Network Analysis](https://img.shields.io/badge/Network_Analysis-tcpdump-blue?style=for-the-badge)](https://www.tcpdump.org/)
[![Protocol](https://img.shields.io/badge/Protocol-DNS-darkgreen?style=for-the-badge)](https://en.wikipedia.org/wiki/Domain_Name_System)
[![Protocol](https://img.shields.io/badge/Protocol-ICMP-red?style=for-the-badge)](https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol)

## 📌 Project Description
This project documents the technical analysis of a network outage involving a DNS service failure and ICMP error responses. The investigation was conducted by analyzing network packet captures using `tcpdump` to trace the affected protocols, identify the root cause of the connection drop, and propose remediation steps.

---

## 🚨 The Scenario
Users reported that they were entirely unable to access the corporate recipe portal: `www.yummyrecipesforme.com`. 

Instead of the webpage loading, their browsers eventually timed out, and network diagnostics returned the following error:
> **"Destination Port Unreachable"**

---

## 🔬 Technical Analysis & Evidence
To understand the scope of the issue, a packet capture was initiated on the client's network interface to monitor the outgoing and incoming traffic flow.

### Protocols Observed in the Capture:
* **DNS (Domain Name System):** Used by the client to resolve the target URL into an IP address.
* **UDP (User Datagram Protocol):** The transport-layer protocol used to send the DNS query.
* **ICMP (Internet Control Message Protocol):** Used by network devices to report errors and diagnostic information.

### 🚩 Key Findings:
1. **The Request:** The packet capture revealed that the client device successfully sent a standard DNS query (via **UDP Port 53**) to the organization's internal DNS server (`203.0.113.2`), asking for the IP address of `www.yummyrecipesforme.com`.
2. **The Failure:** The DNS server did not respond with a DNS resolution packet. Instead, it immediately returned an **ICMP Type 3, Code 3** message indicating: `UDP Port 53 Unreachable`.
3. **The Impact:** Because the client could not resolve the domain name to an IP address, the subsequent HTTP/HTTPS TCP handshake could not even be initiated, resulting in the browser timeout.

---

## 🧠 Root Cause Assessment
The ICMP "Port Unreachable" error explicitly signifies that the routing to the server is working (the server exists and is reachable on the network layer), but the specific service (DNS) is not actively listening on the expected port, or it is actively being blocked at the transport layer.

**Probable Root Causes:**
1. **Service Failure:** The `bind9` or equivalent DNS daemon on the server (`203.0.113.2`) has crashed, was stopped manually, or failed to start after a reboot.
2. **Firewall Misconfiguration:** A host-based firewall (like `ufw` or `iptables`) on the DNS server was recently updated and is now rejecting incoming UDP traffic on port 53.
3. **Configuration Error:** The DNS service was reconfigured and is listening on the wrong network interface.

---

## 🛠️ Recommended Remediation Steps
To restore service and prevent future outages, the IT Operations team should execute the following steps:
1. **Service Check:** SSH into the DNS server (`203.0.113.2`) and verify the status of the DNS daemon (e.g., `systemctl status named` or `systemctl status systemd-resolved`).
2. **Port Verification:** Run `netstat -tuln | grep 53` or `ss -tuln` to confirm that the server is actively listening on UDP port 53.
3. **Firewall Audit:** Review local and perimeter firewall rules to ensure that traffic targeting UDP port 53 is explicitly allowed from the internal client subnets.
4. **Log Review:** Inspect `/var/log/syslog` or DNS-specific logs to identify exactly when and why the service stopped or started rejecting connections.
