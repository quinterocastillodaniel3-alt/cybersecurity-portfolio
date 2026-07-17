# Data Handling Practices & NIST Compliance Audit

[![Framework](https://img.shields.io/badge/Framework-NIST_SP_800--53-blue?style=for-the-badge)](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final)
[![Domain](https://img.shields.io/badge/Domain-GRC_%26_Compliance-darkgreen?style=for-the-badge)](https://en.wikipedia.org/wiki/Governance,_risk_management,_and_compliance)
[![Principle](https://img.shields.io/badge/Security_Principle-Least_Privilege-red?style=for-the-badge)](https://www.cisa.gov/uscert/bsi/articles/knowledge/principles/least-privilege)

## 📌 Project Description
This project documents a comprehensive security audit of an organization's data handling practices following a data leak incident. The primary objective was to evaluate the incident against the **NIST Cybersecurity Framework (CSF)**—specifically focusing on data security (PR.DS-5) and the principle of Least Privilege (AC-6). 

By analyzing the administrative and technical control failures, I developed actionable recommendations to enforce stricter data privacy policies and mitigate the risk of internal data exposure.

---

## 🔍 Incident Summary & Root Cause Analysis

### The Incident
A severe data leak occurred when a sales manager shared a cloud folder containing internal-only documents (including unannounced product schematics and customer analytics) with their immediate team. The manager failed to revoke this open access after the project meeting concluded. 

Subsequently, during a call with an external business partner, a sales representative accidentally shared the URL to the entire internal folder instead of the intended promotional materials. The business partner, unaware of the confidentiality, posted this link on their company's public social media channels.

### Root Cause Analysis
The investigation revealed a systemic failure in Identity and Access Management (IAM):
* **Excessive Permissions:** Access to the internal folder was not properly restricted to the authorized sales team. The business partner was able to view the contents because the folder's share settings allowed "Anyone with the link" to access it, rather than restricting it to verified corporate accounts.
* **Access Drift:** There was a widespread neglect of information confidentiality. Permissions were granted for a specific event (the meeting) but were never audited or revoked afterward.

---

## 📖 Framework Application: NIST SP 800-53 (AC-6)
To address this systemic failure, I evaluated the organization's policies against **NIST SP 800-53: AC-6 (Least Privilege)**. 

This core security control dictates that organizations must provide users with only the minimal access and authorization necessary to complete their specific business tasks. The intention is to prevent a user (or an external partner) from operating at privilege levels higher than required, drastically reducing the blast radius of human error or compromised accounts.

---

## 🛡️ Remediation & Security Controls
Based on the NIST framework enhancements, I recommended implementing the following technical and administrative controls to prevent future data leaks:

1. **Implement Role-Based Access Control (RBAC):** Restrict access to sensitive resources strictly based on the user's verified role within the organization directory. External sharing must be disabled by default for internal project folders.
2. **Deploy Time-Bound Access:** Automate the revocation of access to highly sensitive information. When temporary access is granted, the system should automatically expire the link or permissions after a predefined period (e.g., 24 or 48 hours).
3. **Mandatory Access Reviews (Privilege Auditing):** Enforce automated quarterly audits where department managers must review and explicitly re-approve the access rights of all team members to shared drives.

---

## ⚖️ Business Justification & Impact
Automating security tasks—such as setting automatic expiration dates on access links—is a highly effective strategy to remove the reliance on human memory and reduce operational risk. 

By strictly restricting shared links to authenticated employees and enforcing routine privilege audits, the organization directly limits the exposure of proprietary intellectual property. These remediation steps not only prevent accidental data leaks but also ensure the organization maintains robust, provable compliance with modern data privacy standards.
