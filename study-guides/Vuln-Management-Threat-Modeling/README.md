# 🎯 Vulnerability Management and Threat Modeling

This repository serves as a guide on proactive strategies, risk discovery, and structured methodologies to evaluate and reduce an organization's attack surface.

---

## 🧩 Core Cybersecurity Concepts

To properly manage risk, it is vital to differentiate the following concepts:

* **Attack Surface:** The sum of all potential vulnerabilities and entry points that a threat agent could exploit.
* **Attack Vector:** The path or method used by a malicious actor to infiltrate the system (e.g., an online login form without input sanitization or an outdated webpage).
* **Vulnerability:** An inherent weakness in the system or processes. Classic examples include an employee misconfiguring a firewall or a malfunctioning physical door lock.
* **Threat:** The external actor or event attempting to exploit the weakness (e.g., a group of malicious hackers). *Note: Hackers are the threat, not the vulnerability.*

---

## 🔍 Vulnerability Management and Assessment

Vulnerability Management is a continuous (not one-time) process that must consider multiple perspectives. Its main characteristics include discovering new exposed assets and acting as an effective way to limit security risks.

### Risk Assessment
After identifying and analyzing current procedures or systems, a Risk Assessment is performed. Its main objective is to **score vulnerabilities based on their severity and impact**, allowing teams to prioritize which issues to fix first.

---

## 🧠 Attacker Mindset and PASTA Framework

Adopting an offensive mindset (Red Teaming) requires following logical steps to stay ahead of cybercriminals. 

**Phases of the attacker mindset:**
1. Identify a target.
2. **Determine how the target can be accessed.**
3. Evaluate the attack vectors that can be exploited.
4. Find the attack tools and methods.
*(Note: Identifying ways to fix vulnerabilities is a defensive task; therefore, it is not part of the attacker mindset).*

### PASTA Framework
*(Process for Attack Simulation and Threat Analysis)*
It is a risk-centric methodology consisting of seven phases. The systematic creation of an **Attack Tree** (to map how a threat could compromise a target) occurs specifically in the **Attack Modeling** phase.

---

## 📊 CVSS v3.1 Severity Scale (Common Vulnerability Scoring System)

According to the Common Vulnerabilities and Exposures (CVE®) list, each vulnerability receives a standardized score that dictates the urgency of remediation.

| Base Score | Severity Level | Recommended Action and Response Times |
| :---: | :---: | :--- |
| **0.0** | None | Documentation and general information. |
| **0.1 - 3.9** | Low | Routine monitoring. Long-term resolution. |
| **4.0 - 6.9** | Medium | Schedule patch in the next regular maintenance window. |
| **7.0 - 8.9** | High | Priority patching. Accelerate testing and deployment. |
| **9.0 - 10.0** | **Critical** | **Imminent risk. A score of 9 or higher requires company resources to be mobilized to address it immediately.** |
