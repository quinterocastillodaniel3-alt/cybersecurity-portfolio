# Incident Report Analysis: ICMP DoS Attack (NIST CSF)

[![NIST CSF](https://img.shields.io/badge/Framework-NIST_CSF-blue?style=for-the-badge)](https://www.nist.gov/cyberframework)
[![DoS Attack](https://img.shields.io/badge/Attack_Vector-ICMP_Flood-red?style=for-the-badge)](https://www.cisa.gov/news-events/news/understanding-denial-service-attacks)
[![Network Security](https://img.shields.io/badge/Domain-Network_Security-darkgreen?style=for-the-badge)](https://en.wikipedia.org/wiki/Network_security)

## 📝 Incident Summary
A multimedia company experienced a Denial of Service (DoS) attack that compromised the internal network and caused a two-hour service outage. The attack was identified as an **ICMP Ping Flood**, where a malicious actor overwhelmed the network with inbound ICMP packets through an unconfigured firewall. 

The Incident Response (IR) team successfully mitigated the attack by blocking the malicious packets, temporarily taking non-critical services offline to preserve bandwidth, and systematically restoring critical business operations.

---

## 🛡️ NIST Cybersecurity Framework (CSF) Application

The following breakdown demonstrates how the incident was handled and documented using the five core functions of the NIST Cybersecurity Framework.

### 🔍 1. IDENTIFY
Understanding the organizational context, assets, and risks associated with the attack.
* **Threat:** Malicious actor executing a Denial of Service (DoS) attack.
* **Attack Vector:** ICMP Ping Flood.
* **Vulnerability:** An improperly configured network firewall that allowed unrestricted inbound ICMP traffic.
* **Impacted Assets:** Internal network infrastructure, disrupting web design, graphic design, and social media marketing services.

### 🧱 2. PROTECT
Implementing appropriate safeguards to ensure delivery of critical services and prevent similar future attacks.
* **Rate Limiting:** Established a new firewall rule to strictly limit the rate of incoming ICMP packets.
* **Anti-Spoofing Controls:** Configured the firewall to verify source IP addresses on incoming ICMP packets to proactively block spoofed IP traffic.

### 📡 3. DETECT
Developing and implementing activities to identify the occurrence of a cybersecurity event.
* **Network Monitoring Software:** Implemented to establish a continuous traffic baseline and detect anomalous network behavior in real time.
* **IDS/IPS System:** Configured an Intrusion Detection and Prevention System to automatically identify and filter malicious ICMP traffic based on suspicious characteristics and known attack signatures.

### 🛑 4. RESPOND
Taking action regarding a detected cybersecurity incident to contain its impact.
* **Containment:** Immediately blocking all incoming ICMP packets at the firewall level.
* **Mitigation:** Taking all non-critical network services offline to preserve bandwidth and processing power for core business functions.
* **Analysis:** Investigating the firewall logs to confirm the source, scope, and nature of the ping flood.

### 🔄 5. RECOVER
Maintaining plans for resilience and restoring any capabilities or services that were impaired.
* **Prioritized Restoration:** Bringing critical network services back online first to ensure immediate business continuity.
* **Gradual Reconnection:** Safely restoring non-critical services only after the network traffic normalized and the new firewall rules were verified as effective.
* **Post-Incident Review:** Documenting the event, updating the organization's security posture, and applying lessons learned to the incident response playbook.
