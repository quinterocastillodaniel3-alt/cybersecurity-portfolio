# Incident Handler's Journal: Healthcare Ransomware Attack

[![Incident Response](https://img.shields.io/badge/Incident_Response-Critical-red?style=for-the-badge)](https://www.cisa.gov/stopransomware)
[![Ransomware Analysis](https://img.shields.io/badge/Ransomware_Analysis-Malware-darkred?style=for-the-badge)](https://www.cisa.gov/stopransomware/ransomware-guide)
[![NIST SP 800-61](https://img.shields.io/badge/Framework-NIST_SP_800--61-blue?style=for-the-badge)](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf)

## 📌 Project Description
As part of an incident response simulation, I acted as an Incident Handler for a small U.S. healthcare clinic specializing in primary care. The clinic suffered a severe ransomware attack that paralyzed business operations and restricted access to critical patient medical records. 

I utilized an Incident Handler's Journal to methodically document the initial triage phase, capturing the core facts of the breach to establish a baseline for the forensic investigation and containment strategy.

---

## 🔬 NIST Incident Response Lifecycle: Detection & Analysis
This journal entry represents the **Detection and Analysis** phase of the NIST SP 800-61 Incident Response Life Cycle. The primary objective at this stage is to accurately identify the scope of the compromise, document the indicators, and prepare for the immediate transition into the **Containment, Eradication, and Recovery** phases.

---

## 📓 Incident Log Entry

| Field | Details |
| :--- | :--- |
| **Date** | July 15, 2026 |
| **Entry ID** | IR-2026-001 |
| **Description** | Initial incident report documenting a ransomware infection and operational shutdown at a primary care clinic, initiated via spear-phishing. |
| **Tool(s) used** | Initial Triage / Incident Handler's Journal. |
| **Current Status** | System isolation in progress; External IR assistance requested. |

### 🧭 The 5 W's (Threat Context)
* **Who:** An organized hacking group known for targeting the healthcare and transportation sectors.
* **What:** Employees lost access to critical computer files, including Electronic Health Records (EHR). A ransom note appeared on screens demanding a large sum of money for the decryption key, causing a complete operational halt.
* **When:** Tuesday morning at approximately 9:00 a.m.
* **Where:** A small U.S. healthcare clinic specializing in primary care services.
* **Why (Attack Vector):** Attackers breached the network by sending targeted phishing emails to several employees. These emails contained a malicious attachment that, once downloaded, installed the ransomware payload on local machines and propagated laterally through the network.

### 🛑 Immediate Next Steps
The organization was forced to proactively shut down its IT systems to contain the encryption spread. External organizations were contacted for technical assistance. **Immediate actions include:**
1. Secure compromised workstations to preserve volatile forensic evidence (RAM/Cache).
2. Extract and analyze the malicious email header.
3. Assess the integrity of offline backups to determine recovery viability without paying the ransom.

---

## 🛠️ Proposed Investigative Tooling
To advance this investigation beyond manual documentation, the following technical tools would be deployed in a live SOC environment:
* **SIEM (e.g., Splunk / Microsoft Sentinel):** To trace network logs and identify the exact moment the malicious attachment communicated with the attacker's Command and Control (C2) server.
* **EDR (Endpoint Detection and Response):** To logically isolate the infected host machines from the rest of the clinic's network (Network Containment) to prevent further lateral movement.
* **Malware Sandboxing (e.g., Any.Run / VirusTotal):** To safely detonate and analyze the email attachment's behavior, extracting verifiable Indicators of Compromise (IoCs) such as dropped hashes and contacted IP addresses.

---

## 🎓 Lessons Learned & Strategic Recommendations
To prevent future occurrences of similar ransomware attacks, the following long-term mitigations should be implemented during the Post-Incident Activity phase:
1. **Email Gateway Hardening:** Implement advanced anti-phishing filters and attachment sandboxing to block malicious payloads before they reach employee inboxes.
2. **Security Awareness Training:** Mandate routine, healthcare-specific phishing simulation training for all clinical and administrative staff.
3. **Immutable Offline Backups:** Ensure that all patient data and critical infrastructure configurations are backed up to off-site, immutable servers (Write-Once-Read-Many) that cannot be reached or encrypted by network-based ransomware.
4. **Network Segmentation:** Segment the clinic's network to isolate critical patient record databases from regular administrative workstations, limiting the ransomware's blast radius.
