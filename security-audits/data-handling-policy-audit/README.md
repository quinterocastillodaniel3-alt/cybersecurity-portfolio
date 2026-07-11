# Data Handling Practices & NIST Compliance Audit

## 📌 Project Description
This project involves auditing an organization's data handling practices following a data leak incident. [cite_start]The objective was to evaluate the incident against the **NIST Cybersecurity Framework (CSF)** [cite: 11][cite_start]—specifically focusing on data security (PR.DS-5) [cite: 13] [cite_start]and the principle of Least Privilege (AC-6)[cite: 13, 25]. By analyzing the control failures, I developed actionable recommendations to enforce stricter data privacy and mitigate the risk of accidental internal data exposure.

---

## 🔍 Incident Summary & Identified Issues
[cite_start]A data leak occurred when a sales manager shared a folder of internal-only documents (including unannounced product files and customer analytics) [cite: 2, 3, 4] [cite_start]with their team but failed to revoke access after the meeting[cite: 4]. [cite_start]Subsequently, during a call with a business partner, a sales representative accidentally shared the link to the entire internal folder instead of the intended promotional materials[cite: 5, 6, 7]. [cite_start]The business partner then posted this link on their company's social media[cite: 8].

[cite_start]**Root Cause Analysis:** Access to the internal folder was not properly limited to the sales team and the manager[cite: 9]. [cite_start]There was a widespread neglect of information confidentiality, and the business partner should never have had permissions that allowed for sharing sensitive information externally[cite: 9].

---

## 📖 NIST SP 800-53: AC-6 Review
[cite_start]To address this systemic failure, I reviewed **NIST SP 800-53: AC-6**, which provides guidelines for securing information privacy by implementing the concept of "Least Privilege"[cite: 9, 14, 18]. [cite_start]The core control dictates that users should only be provided the minimal access and authorization required to complete their specific tasks[cite: 25]. [cite_start]The intention is to prevent a user from operating at privilege levels higher than what is necessary to accomplish business objectives[cite: 25]. [cite_start]The framework also provides specific control enhancements to improve the effectiveness of least privilege implementation[cite: 9, 24].

---

## 🛡️ Control Recommendations
Based on the NIST framework enhancements, I recommended implementing the following controls to prevent future data leaks:
1. [cite_start]**Restrict access to sensitive resources based on user role**[cite: 9, 25].
2. [cite_start]**Automatically revoke access to information after a period of time**[cite: 25].
3. [cite_start]**Regularly audit user privileges**[cite: 9, 25].

---

## ⚖️ Business Justification
Automating security tasks, such as setting automatic expiration dates on access links, is a highly effective way to reduce the likelihood of human error. [cite_start]Furthermore, data leaks can be actively prevented if shared links to internal files are strictly restricted to verified employees only[cite: 9]. [cite_start]Requiring management and security teams to regularly audit access to team files directly limits the exposure of sensitive information [cite: 9] and ensures that the organization maintains robust and compliant data privacy standards.
