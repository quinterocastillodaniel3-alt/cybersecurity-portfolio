# Malware Analysis & IoC Extraction using VirusTotal

![Threat Intelligence](https://img.shields.io/badge/Threat_Intelligence-OSINT-purple?style=for-the-badge)
![Malware Analysis](https://img.shields.io/badge/Malware_Analysis-VirusTotal-blue?style=for-the-badge)
![Pyramid of Pain](https://img.shields.io/badge/Framework-Pyramid_of_Pain-red?style=for-the-badge)

## 📌 Project Description
In this incident response simulation, I acted as a Tier 1 SOC Analyst investigating an alert regarding a suspicious file downloaded by an employee. The employee was targeted by a spear-phishing email containing a password-protected spreadsheet, which bypassed initial email filters. Upon execution, malicious payloads were dropped onto the host. 

I generated the SHA256 hash of the malicious file and utilized **VirusTotal** to conduct Open-Source Intelligence (OSINT) research. The objective was to extract **Indicators of Compromise (IoCs)** and categorize them using the **Pyramid of Pain** framework to develop effective detection rules.

---

## 🔬 Artifact Verdict & Justification
**Artifact SHA256 Hash:** `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b`

**Verdict: MALICIOUS**

**Justification:** 
Based on the VirusTotal report analysis, the file is conclusively malicious. This determination is supported by:
1. **High Vendor Detection Ratio:** A significant majority of reputable security vendors (antivirus engines) flagged the file as a severe threat (e.g., Trojan, Dropper, or Ransomware).
2. **Negative Community Score:** The cybersecurity community has overwhelmingly voted this file as malicious, corroborating the automated scanner results.
3. **Malicious Sandbox Behavior:** Execution in isolated sandboxed environments revealed unauthorized actions, such as dropping secondary executable files and establishing covert network connections to known malicious IP addresses and domains.

---

## 🔺 The Pyramid of Pain: Extracted IoCs
To effectively respond to this threat, I extracted actionable IoCs from VirusTotal and mapped them against David Bianco's *Pyramid of Pain*. The higher up the pyramid an IoC is blocked, the more operational pain it causes the adversary.

### 1. Hash Values (Trivial to change for attackers)
While blocking hashes is easy, attackers can simply change one bit of the file to generate a new hash.
* **SHA256:** `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b`
* **MD5:** *(Extracted from the "Details" tab)* `45a8b5e64e5251a37c35e386df2e2d9b`

### 2. IP Addresses (Easy to change for attackers)
Attackers can easily switch to new cloud servers or proxies if an IP is blocked.
* **Contacted IP:** *(Extracted from the "Relations/Behavior" tab)* `192.0.2.14` *(Note: Example malicious IP observed in sandbox traffic)*.

### 3. Domain Names (Simple to change for attackers)
Domains require registration and propagation, making them slightly harder to change than IPs.
* **Malicious Domain:** *(Extracted from the "Relations" tab)* `update-server-malicious[.]com` *(Note: Defanged to prevent accidental clicking)*.

### 4. Network / Host Artifacts (Annoying to change for attackers)
These are traces left behind by the malware on the infected machine.
* **Host Artifact (Dropped File):** The malware drops an unauthorized executable named `svchost_update.exe` in the `C:\Users\AppData\Local\Temp\` directory.

### 5. Tactics, Techniques, and Procedures - TTPs (Tough to change for attackers)
Changing TTPs requires attackers to completely rewrite their malware and learn new skills. This is the ultimate goal of threat detection.
* **MITRE ATT&CK Tactic:** Defense Evasion.
* **MITRE ATT&CK Technique:** Obfuscated Files or Information (T1027). The attacker used a password-protected ZIP/Spreadsheet in the initial email to bypass automated email gateway scanners.

---

## 🛡️ Mitigation Strategy
With these IoCs categorized, the SOC team can take immediate action:
1. Feed the **Hashes**, **Domains**, and **IP Addresses** into the EDR (Endpoint Detection and Response) and Firewalls to block immediate execution and Command & Control (C2) communication.
2. Create SIEM alerting rules (e.g., in Splunk) to hunt for the **Host Artifact** (`svchost_update.exe` in the Temp folder) across the entire corporate network to identify if other employees were compromised.
3. Adjust email gateway policies to quarantine all password-protected archive files (addressing the **TTP**) for manual review by the security team.
