# Phishing Incident Response & Playbook Execution

![Incident Response](https://img.shields.io/badge/Incident_Response-Playbook-blue?style=for-the-badge)
![SOC Operations](https://img.shields.io/badge/SOC_Operations-Tier_1-darkgreen?style=for-the-badge)
![Malware](https://img.shields.io/badge/Malware-Password_Protected-red?style=for-the-badge)

## 📌 Project Description
In this project, I acted as a Tier 1 Security Operations Center (SOC) Analyst responding to a potentially malicious email alert (Ticket ID: A-2703)[cite: 7]. The objective was to evaluate the alert, analyze the email components, and execute the organization's Standard Operating Procedure (SOP) using a Phishing Playbook[cite: 6]. Based on the investigation findings, I formally updated the incident ticket and escalated the threat to Tier 2 for containment.

---

## 🔍 Phase 1: Alert Evaluation & Email Analysis
Upon receiving the alert, I evaluated the email metadata and body to identify Social Engineering tactics and Indicators of Compromise (IoCs)[cite: 6]. 

**Alert Details:**
* **Ticket ID:** A-2703[cite: 7]
* **Severity:** Medium[cite: 7]
* **Sender:** `Def Communications <76tguyhh6tgftrt7tg.su>` (IP: `114.114.114.114`)[cite: 7]
* **Recipient:** `hr@inergy.com`[cite: 7]
* **Subject:** `Re: Infrastructure Egnieer role`[cite: 7]

**Red Flags Identified:**
1. **Domain Mismatch:** The sender domain (`76tguyhh6tgftrt7tg.su`) consists of random alphanumeric characters and originates from a suspicious Top-Level Domain (.su), which does not match a legitimate applicant's profile[cite: 7].
2. **Fabricated Thread (RE:):** The subject line attempts to trick the HR department into believing this is an ongoing conversation by prepending "Re:"[cite: 7].
3. **Spelling & Grammar:** The subject contains typos ("Egnieer"), and the body contains poor grammar ("I am writing for to express")[cite: 7].
4. **Suspicious Attachment:** The email includes an executable file disguised as a resume (`bfsvc.exe`). Furthermore, the attacker password-protected the file (`paradise10789`) to actively evade automated email antivirus scanners and Secure Email Gateways (SEGs)[cite: 7].

---

## 📘 Phase 2: Playbook Execution
To ensure a standardized response, I followed the organization's Phishing Flowchart (Version 1.0)[cite: 6]:

* **Step 3.0 (Check for Attachments):** Confirmed the presence of an executable attachment (`bfsvc.exe`)[cite: 6, 7].
* **Step 3.1 (Verify Malicious Intent):** Cross-referenced the attachment's SHA256 hash (`54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b`) with Threat Intelligence platforms (VirusTotal)[cite: 6, 7]. The hash was positively identified as known malware.
* **Step 3.2 (Update and Escalate):** Because the attachment was confirmed malicious and a user may have interacted with it, the playbook mandates immediate escalation[cite: 6].

---

## 📝 Phase 3: Final Ticket Resolution
To complete the workflow, I updated the incident management system with clear, actionable intelligence for the Tier 2 analysts.

* **Ticket Status:** **ESCALATED**[cite: 6]
* **Ticket Comments:**
  > *This alert was triggered by a highly suspicious email targeting the HR department with a password-protected executable attachment (`bfsvc.exe`) disguised as a resume. I am escalating this ticket because the attachment's SHA256 hash (`54e6ea47eb...`) is a verified known malicious indicator, and the use of an encrypted payload suggests a deliberate attempt to bypass our automated security controls. Immediate isolation of the recipient's host machine (IP: `176.157.125.93`) is recommended to prevent potential malware execution and lateral movement.*[cite: 7]

## 🛡️ Key Takeaways
This exercise demonstrates the critical importance of adhering to procedural playbooks in a SOC environment. By systematically evaluating the alert, verifying the IoCs, and documenting the findings precisely in the ticket, I ensured a rapid and structured handover to the incident response team, minimizing the organization's exposure time to an active threat.
