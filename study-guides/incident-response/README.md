# 🛡️ Study Guide: Security Incident Management and Response

This repository contains fundamental notes on cybersecurity incident management, based on the NIST lifecycle and best practices for documentation and triage in a Security Operations Center (SOC).

---

## 🔄 Incident Response Lifecycle Phases (NIST)

The NIST (National Institute of Standards and Technology) framework establishes four main, cyclical, and continuous phases for incident management:

1. **Preparation:** Establishing policies, tools, and training teams before a security event occurs.
2. **Detection and Analysis:** Confirming if an alert is a real incident and understanding its scope.
   * **Key tasks:** Collecting and analyzing network logs to verify the alert, and identifying affected devices or systems.
3. **Containment, Eradication, and Recovery:** A grouped technical phase to stop the threat and restore business operations.
   * **Containment:** Isolating affected systems (e.g., disconnecting them from the network) to limit and prevent further damage.
   * **Eradication:** Eliminating the root cause (e.g., completing vulnerability scans and applying patches).
   * **Recovery:** Returning systems to normal operations (e.g., reinstalling the operating system of a computer infected by malicious software).
4. **Post-Incident Activity:** Reviewing the incident handling process to identify areas for improvement.

---

## 🚨 Triage and SOC Operations

Triage is the process of prioritizing incidents based on their level of importance or urgency to optimize the security team's response.

* **Initial Reception:** When an analyst receives a new alert (such as the detection of a malware download or a phishing attempt), the first step of the process is always to **receive and evaluate** the initial information before assigning priorities or adding context.
* **Automation (SOAR):** To handle high volumes of alerts, automated playbooks are used. These stand out because they **use automation to execute tasks and standard, rapid response actions**.

---

## 📝 Documentation and Chain of Custody

Meticulous documentation is the backbone of incident response and a vital tool for legal and regulatory defense.

* **The Final Report:** This is the document that provides a comprehensive review of an incident. It always includes an **Executive Summary**, which contains a high-level overview intended for the board or management.
* **Transparency:** Allowing auditors access to any relevant information and records during an annual audit generates a clear benefit of organizational **transparency**.
* **Utility of Transparent Documentation:**
   * Meeting the strict requirements of cybersecurity insurance.
   * Providing solid evidence for legal proceedings.
   * Demonstrating compliance with current regulatory requirements.
* **Chain of Custody:** This is the chronological record of the handling of evidence. Inconsistencies or failures in the collection and recording of evidence cause the chain of custody to be **broken**, which invalidates the evidence in official settings.

---

## 🧠 Lessons Learned Meeting (Post-mortem)

Once the incident is resolved, the security team must meet to analyze the response. 

* **Timeline:** Best practices require this meeting to be held within **two** weeks following the incident.
* **Main Objectives:**
   * Identify areas for improvement.
   * Review and reflect on a security incident.
* **Constructive Approach:** The meeting seeks to resolve process failures (asking questions like: *"What could have been done differently?"* to, for example, expedite backups), and should never be used to identify a guilty employee.
