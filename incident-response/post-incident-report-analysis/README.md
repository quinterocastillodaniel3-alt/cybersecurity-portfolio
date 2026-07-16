# Post-Incident Response: Final Report Analysis

![Incident Response](https://img.shields.io/badge/Incident_Response-Post--Incident-blue?style=for-the-badge)
![Web Security](https://img.shields.io/badge/Web_Security-Forced_Browsing-red?style=for-the-badge)
![NIST](https://img.shields.io/badge/Framework-NIST_Lifecycle-darkgreen?style=for-the-badge)

## 📌 Project Description
The final phase of the NIST Incident Response Lifecycle is Post-Incident Activity, which focuses on documenting the breach, analyzing the root cause, and implementing strategic defenses to prevent recurrence. In this project, I acted as a Tier 1 SOC Analyst for a mid-sized retail company conducting a post-incident review of a major data breach involving the e-commerce platform. The objective of this review was to extract the core timeline, assess the operational impact, evaluate the containment response, and document the final security recommendations.

---

## 🔍 Objective 1: Identify What Happened (Root Cause & Impact)
The organization suffered a severe data breach exposing the Personal Identifiable Information (PII) and financial details of approximately 50,000 customers[cite: 7]. 
* **Financial Impact:** The incident resulted in an estimated $100,000 in direct costs and potential loss of revenue[cite: 7].
* **Attack Vector (Root Cause):** The breach was executed via a vulnerability in the e-commerce web application[cite: 7]. The attacker utilized a "forced browsing" attack[cite: 7]. 
* **Exploitation Method:** The threat actor bypassed standard navigation and accessed unauthorized customer transaction data by manipulating the order numbers within the URL string of the purchase confirmation pages[cite: 7].

---

## ⏱️ Objective 2: Identify When It Happened (Timeline)
The incident unfolded over several days due to an initial failure to recognize an extortion attempt:
* **December 22, 2022 (3:13 p.m. PT):** An employee received an external email from an attacker claiming to possess stolen customer data[cite: 7]. The attacker demanded a $25,000 cryptocurrency ransom to prevent public release[cite: 7]. The employee dismissed the email as spam and deleted it[cite: 7].
* **December 28, 2022:** The same employee received a follow-up email from the attacker containing a sample of the stolen data and an escalated ransom demand of $50,000[cite: 7]. The employee subsequently notified the security team[cite: 7].
* **December 28, 2022 (7:20 p.m. PT):** The organization formally declared the security incident[cite: 7].
* **December 28 - 31, 2022:** The security team traveled on-site and conducted the primary investigation to determine the theft's scope and methodology[cite: 7].

---

## 🛡️ Objective 3: Identify Response Actions
Upon validating the threat, the organization executed several remediation and response protocols:
* **Technical Investigation:** The security team analyzed the web server access logs and identified a single log source responsible for an exceptionally high volume of sequential requests for customer orders[cite: 7].
* **Public Relations & Disclosure:** The organization actively collaborated with the PR department to formally disclose the data breach to the affected customers[cite: 7].
* **Customer Mitigation:** To mitigate the personal impact on the victims, the organization offered free identity protection services to all affected customers[cite: 7].

---

## 📈 Objective 4: Identify Future Recommendations
To secure the e-commerce platform and prevent forced browsing attacks or similar web application vulnerabilities in the future, the final report mandates the following actions[cite: 7]:
1. **Proactive Security Testing:** Perform routine vulnerability scans and comprehensive penetration testing on the web infrastructure[cite: 7].
2. **Access Control (Allowlisting):** Implement URL allowlisting mechanisms to restrict access strictly to a specified set of legitimate URLs, automatically blocking any anomalous requests outside this range[cite: 7].
3. **Authentication Enforcement:** Ensure strict session management and verify that only authenticated and properly authorized users can access sensitive content, such as purchase confirmation pages[cite: 7].
