# Incident Report Analysis: ICMP DoS Attack (NIST CSF)

## 📝 Incident Summary
A multimedia company experienced a Denial of Service (DoS) attack that compromised the internal network and caused a two-hour service outage. The attack was identified as an ICMP Ping Flood, where a malicious actor overwhelmed the network with inbound ICMP packets through an unconfigured firewall. The Incident Response (IR) team mitigated the attack by blocking the malicious packets, temporarily taking non-critical services offline, and restoring critical business operations. 

---

## 🛡️ NIST Cybersecurity Framework (CSF) Application

### 1. IDENTIFY
* **Threat:** Malicious actor executing a Denial of Service (DoS) attack.
* **Attack Vector:** ICMP Ping Flood.
* **Vulnerability:** An improperly configured network firewall that allowed unrestricted inbound ICMP traffic.
* **Impacted Assets:** Internal network infrastructure, disrupting web design, graphic design, and social media marketing services.

### 2. PROTECT
To secure the organization's assets and prevent similar future attacks, the following network hardening configurations were implemented:
* **Rate Limiting:** Established a new firewall rule to strictly limit the rate of incoming ICMP packets.
* **Anti-Spoofing Controls:** Configured the firewall to verify source IP addresses on incoming ICMP packets to block spoofed IP traffic.

### 3. DETECT
To continuously monitor network traffic and identify anomalies quickly, the following detection capabilities were deployed:
* **Network Monitoring Software:** Implemented to establish a traffic baseline and detect anomalous network behavior in real time.
* **IDS/IPS System:** Configured an Intrusion Detection and Prevention System to automatically identify and filter ICMP traffic based on suspicious characteristics and known attack signatures.

### 4. RESPOND
The incident response plan executed during the attack included:
* **Containment:** Immediately blocking all incoming ICMP packets at the firewall level.
* **Mitigation:** Taking all non-critical network services offline to preserve bandwidth and processing power.
* **Analysis:** Investigating the firewall logs to confirm the source and nature of the flood.

### 5. RECOVER
To return the affected systems to normal operation, the recovery process involved:
* **Prioritized Restoration:** Bringing critical network services back online first to ensure business continuity.
* **Gradual Reconnection:** Safely restoring non-critical services once the network traffic normalized and the new firewall rules were confirmed to be effective.
* **Post-Incident Review:** Documenting the event and updating the organization's security posture.
