# 🌐 Network Analysis & Traffic Monitoring

[![Packet Analysis](https://img.shields.io/badge/Skill-Packet_Analysis-blue?style=for-the-badge)](https://en.wikipedia.org/wiki/Packet_analyzer)
[![Network Security](https://img.shields.io/badge/Domain-Network_Security-darkgreen?style=for-the-badge)](https://www.cisa.gov/topics/cyber-threats-and-advisories)
[![IT/OT Convergence](https://img.shields.io/badge/Focus-IT%2FOT_Convergence-red?style=for-the-badge)](https://www.nist.gov/itl/applied-cybersecurity/nist-cybersecurity-iot-program)

Welcome to the **Network Analysis** directory of my cybersecurity portfolio. 

This section serves as a centralized hub for packet inspection, protocol troubleshooting, and network monitoring projects. By applying an engineering mindset that bridges standard Information Technology (IT) environments with Operational Technology (IoT/Mechatronics), the projects housed here demonstrate my ability to analyze traffic patterns, configure Intrusion Detection Systems (IDS), and uncover malicious network behaviors at the packet level.

### 🎯 Core Focus Areas:
* **Packet Inspection & Protocol Analysis:** Deep dives into TCP/IP, DNS, ICMP, and HTTP traffic using industry-standard tools.
* **Intrusion Detection Systems (IDS):** Configuring, tuning, and analyzing logs from open-source network defense tools like Suricata.
* **IT/OT Asset Discovery:** Mapping network dependencies, identifying vulnerabilities in IoT endpoints, and applying segmentation controls.
* **Network Troubleshooting:** Diagnosing service outages, DoS attacks, and anomalous routing behaviors via raw traffic logs.

---

## 🗂️ Directory Index

Below is a breakdown of the network analysis modules and projects available in this directory. Click on any project title to access the detailed analysis, log outputs, and remediation strategies.

### 1. [DNS & ICMP Incident Analysis](./dns-icmp-incident-analysis/README.md)
* **Focus:** Protocol Troubleshooting & Error Diagnostics.
* **Key Topics:** `tcpdump` log analysis, UDP Port 53, ICMP Type 3/Code 3 (Port Unreachable) errors, and service failure identification.

### 2. [IT/OT Home Lab Network Asset Inventory](./home-network-inventory/README.md)
* **Focus:** Asset Management & Risk Classification.
* **Key Topics:** Network mapping, IoT vulnerability profiles, Operational Technology (OT) hardware, and data sensitivity matrices.

### 3. [Network Analyzers Comparison](./network-analyzers-comparison/README.md)
* **Focus:** Security Tooling.
* **Key Topics:** Feature comparisons and use-case scenarios between Wireshark (GUI) and tcpdump (CLI) for network monitoring.

### 4. [Intrusion Detection & Log Analysis with Suricata](./suricata-ids-analysis/README.md)
* **Focus:** IDS Configuration & JSON Parsing.
* **Key Topics:** Custom Suricata rule creation, PCAP analysis, alert generation, and `eve.json` log extraction using `jq`.

### 5. [TCP SYN Flood Analysis (DoS)](./tcp-syn-flood-analysis/README.md)
* **Focus:** Denial of Service & TCP/IP Manipulation.
* **Key Topics:** TCP 3-way handshake mechanics, backlog queue exhaustion, server timeouts, and mitigation controls (SYN Cookies).

### 6. [Wireshark Packet Inspection](./wireshark-packet-inspection/README.md)
* **Focus:** Deep Packet Inspection (DPI).
* **Key Topics:** Identifying network anomalies, filtering traffic streams, and analyzing payload contents.

### 7. [Web Server Compromise & Malware Redirection](./yummy-recipes-incident-report/README.md)
* **Focus:** Attack Chain Analysis.
* **Key Topics:** Brute-force entry, malicious payload delivery, malicious DNS redirection, and account lockout policies.

---
*Note: This repository is actively maintained and updated with new network captures and analytical reports as I continue to expand my threat hunting and traffic monitoring capabilities.*
