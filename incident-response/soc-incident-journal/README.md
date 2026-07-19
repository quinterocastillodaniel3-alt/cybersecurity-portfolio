# Incident Handler's Journal & Analysis Log

[![Location](https://img.shields.io/badge/Location-Medell%C3%ADn%2C_Colombia-success?style=for-the-badge&logo=google-maps)](#) [![Education](https://img.shields.io/badge/Degree-Mechatronics_Engineering-blue?style=for-the-badge&logo=prometric)](#) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/daniel-quintero-castillo-4090a4399/)

![Incident Response](https://img.shields.io/badge/Incident_Response-NIST_Framework-blue?style=for-the-badge) ![Network Analysis](https://img.shields.io/badge/Network_Analysis-Wireshark-darkgreen?style=for-the-badge) ![SIEM](https://img.shields.io/badge/SIEM-Wazuh-red?style=for-the-badge)

## 📌 Project Description
In this project, I developed and maintained an Incident Handler's Journal to document security investigations, network analysis, and the deployment of cybersecurity tools. The primary objective was to track anomalous events by applying the phases of the **NIST Incident Response Life Cycle** and document findings in a structured manner for technical and SOC operations teams.

---

## 🔍 Phase 1: Tool Deployment & Network Analysis
During the initial detection phases, I utilized analysis and monitoring tools to identify threats within the network infrastructure.

**Entry 1: Packet Capture and Analysis**
* **Date:** 2026-06-15
* **Description:** During the Detection and Analysis phase of the NIST lifecycle, I used a network protocol analyzer to examine traffic for anomalies. The main objective was to identify insecure protocols and potential data exfiltration from our internal network to suspicious external IP addresses.
* **Tools Used:**
  * **Wireshark:** Employed to inspect real-time network traffic at the packet level.
  * Applied specific display filters (`tcp.port == 80` and `dns`) to isolate unencrypted traffic from normal network noise.
  * Successfully isolated an unusual communication flow, allowing the generation of initial Indicators of Compromise (IoCs).

**Entry 2: Active Monitoring with SIEM**
* **Date:** 2026-07-10
* **Description:** In the Preparation and Detection phases, I configured queries within a SIEM environment to proactively audit operating system logs and identify unauthorized access attempts.
* **Tools Used:**
  * **Wazuh (SIEM):** Utilized for event collection, indexing, and correlation.
  * Executed advanced search queries filtering by the `host.keyword` field and combining logical operators (`fail* AND root`).
  * Confirmed an automated attack pattern, justifying the technical need to apply a strict hardening baseline on the endpoints.

---

## 📘 Phase 2: Incident Escalation & The 5 W's
To guarantee complete context during incident escalation, I structured the investigations of confirmed threats using the 5 W's methodology.

**Entry 3: Malware Infection (Phishing)**
* **Date:** 2026-06-22
* **Description:** Isolation and analysis of a workstation following the execution of a suspicious file reported by the local antivirus.
* **Who:** A financial department analyst reported the anomalous system behavior.
* **What:** Accidental download and execution of a malicious file disguised as a billing document.
* **When:** June 22 at 09:15 AM (start of the workday).
* **Where:** Local workstation (`FIN-PC-04`) located within the internal corporate network.
* **Why/How:** A phishing email bypassed spam filters, persuading the user to execute a hidden payload.

**Entry 4: SSH Brute Force Attack**
* **Date:** 2026-07-18
* **Description:** Response to a brute force attack targeting the superuser account on the mail server. Executed the playbook to block IPs on the firewall and rotate credentials.
* **Who:** External threat actor operating through multiple automated IPs.
* **What:** High volume of failed login attempts directed exclusively at the `root` account.
* **When:** July 18, concentrated in a time window between 02:00 AM and 04:00 AM.
* **Where:** Main mail server exposed to the Internet (`mailsv1`).
* **Why/How:** The attacker exploited the default configuration of port 22, which allowed password login for accounts with elevated privileges.

---

## 📝 Phase 3: Post-Incident Reflections
As part of the **NIST Post-Incident Activity** phase, I highlight the following takeaways from this operations cycle:

> *Event correlation in a massive SIEM environment initially represented a challenge due to the large number of false positives, but overcoming this was fundamental to refining my search logic. I have realized that structured documentation is just as vital as technical mitigation, and that success in the containment phase depends almost entirely on good preventive endpoint hardening. Finally, analyzing traffic with tools like Wireshark was fascinating, as it allows dissecting traffic at a low level to expose anomalies that would otherwise remain completely invisible.*
