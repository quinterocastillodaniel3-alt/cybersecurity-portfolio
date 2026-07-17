# Incident Response: USB Baiting & Malware Risk Analysis

[![Attack Vector](https://img.shields.io/badge/Attack_Vector-USB_Baiting-red?style=for-the-badge)](https://attack.mitre.org/techniques/T1091/)
[![Analysis](https://img.shields.io/badge/Analysis-Sandboxing-blue?style=for-the-badge)](https://en.wikipedia.org/wiki/Sandbox_(computer_security))
[![Security Controls](https://img.shields.io/badge/Controls-Media_Protection-darkgreen?style=for-the-badge)](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final)

## 📌 Project Description
During a simulated security incident, I acted as a Cybersecurity Analyst for a healthcare organization (Rhetorical Hospital) and investigated a suspicious USB flash drive found in the employee parking lot. 

To safely analyze the artifact without risking corporate network infection, I mounted the drive within an isolated, air-gapped Virtual Machine (VM) sandbox. This project explores the forensic contents of the drive, analyzes the potential threat actor's mindset, and outlines the technical and operational security controls necessary to mitigate USB baiting attacks.

---

## 📁 1. Artifact Triage & PII Exposure

![Drive Contents Analysis](jorge-usb-files.png)

The initial sandbox analysis of the USB drive revealed a highly insecure mixture of personal and work-related files belonging to an employee (Jorge). 

* **Corporate Data:** A new hire letter, employee shift schedules, and an employee budget tracker.
* **Personal Data:** Family photos, vacation ideas, and a wedding list.

**Risk Identified:** Storing Personally Identifiable Information (PII) alongside sensitive corporate data on an unencrypted, personal device is a severe policy violation. It exposes both the employee and the hospital to significant privacy risks, regulatory fines, and targeted attacks.

---

## 🧠 2. The Attacker Mindset (Threat Modeling)
Discovering a dropped USB drive typically points to one of two threat scenarios:

1. **The Staged Baiting Attack:** An attacker intentionally planted this drive in the hospital's parking lot. The enticing personal files (like wedding lists and photos) are designed to act as a psychological distraction, convincing the finder that the drive is harmless, while hidden malicious scripts (e.g., AutoRun payloads) silently establish a backdoor into the hospital's network.
2. **The Lost Asset Opportunity:** If this was genuinely lost by the employee and found by a malicious actor, the attacker now has unrestricted access to hospital schedules, internal documents, and PII. This intelligence can be weaponized to craft highly targeted spear-phishing campaigns against Jorge, his relatives, or other hospital staff.

---

## ⚠️ 3. Risk Analysis & Impact
If an unsuspecting employee had bypassed security protocols and connected this device directly to a hospital workstation, the impact could have been catastrophic. Potential consequences include:
* **Initial Access:** Execution of malicious payloads providing remote access to the threat actor.
* **Malware Infection:** Deployment of Ransomware, Rootkits, or Trojans across the hospital's internal network, crippling critical patient-care systems.
* **Data Exfiltration:** Automated scripts copying sensitive Electronic Health Records (EHR) to the external drive.

---

## 🛡️ 4. Security Controls & Remediation
To mitigate the risks associated with removable media and baiting attacks, I recommend implementing the following defense-in-depth controls:

### Technical Controls:
* **Disable Auto-Run:** Globally disable USB auto-run and auto-play features across the domain via Group Policy Objects (GPO).
* **Endpoint Detection and Response (EDR):** Deploy EDR and Data Loss Prevention (DLP) solutions to actively block unauthorized removable media from mounting on any hospital workstation.
* **Device Encryption:** Mandate that any approved corporate USB drives must be strictly hardware-encrypted.

### Administrative & Operational Controls:
* **Data Handling Policies:** Enforce strict Acceptable Use Policies (AUP) that explicitly prohibit the mixing of personal and corporate data on removable media.
* **Security Awareness Training:** Mandate recurring training modules focusing on social engineering, physical security, and the severe dangers of plugging in untrusted external devices.
