# Data Leak Assessment & Incident Response: Principle of Least Privilege

[![NIST SP 800-53](https://img.shields.io/badge/Framework-NIST_SP_800--53-blue?style=for-the-badge)](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final)
[![IAM](https://img.shields.io/badge/Domain-Identity_%26_Access_Management-darkgreen?style=for-the-badge)](https://en.wikipedia.org/wiki/Identity_and_access_management)
[![Least Privilege](https://img.shields.io/badge/Security_Principle-Least_Privilege-red?style=for-the-badge)](https://www.cisa.gov/uscert/bsi/articles/knowledge/principles/least-privilege)

## 📌 Project Description
As a cybersecurity professional for an Educational Technology (EdTech) company, I was tasked with investigating an internal data breach. The organization develops an automated grading application that handles highly sensitive data from academic institutions, instructors, parents, and students. A data leak occurred when internal product plans and marketing materials were inadvertently exposed on social media by an external business partner. 

This project involves analyzing the incident, reviewing the security controls aligned with the **NIST SP 800-53** framework, and proposing control enhancements to enforce the Principle of Least Privilege and prevent future data exposure.

---

## 🔍 1. Incident & Root Cause Analysis
To understand how the leak occurred, I conducted a post-incident review to separate the event from the underlying systemic failure.

* **The Incident (Impact):** During a sales call, a Customer Success Representative accidentally shared a URL link to a complete root folder with an external business partner, instead of just the specific marketing materials. The partner subsequently shared this link on social media, exposing internal product plans to the public.
* **Root Cause Analysis:** The investigation revealed a critical breakdown in Identity and Access Management (IAM). The representative had been temporarily granted access to a manager's root folder. However, the manager failed to revoke this access after it was no longer needed (Access Drift). The human error of sharing the wrong link was only possible because the excessive permissions were left unchecked.

---

## 📖 2. Framework Review: NIST SP 800-53 (AC-6)
To address the systemic failures that led to the incident, I evaluated the organization's policies against **NIST SP 800-53: AC-6 (Least Privilege)**. 

This control mandates that organizations grant users only the absolute minimum access authorizations necessary to perform their designated job functions. It emphasizes that privileges must be:
* Strictly controlled and mapped to roles.
* Routinely reviewed.
* Promptly revoked when no longer required, thereby limiting the blast radius of compromised accounts or insider errors.

---

## 🛡️ 3. Security Control Enhancements (Recommendations)
To align the organization's data handling processes with NIST guidelines and enforce the Principle of Least Privilege, I proposed the following technical and administrative controls:

1. **Implement Time-Bound Access Controls:** 
   Enforce temporary, automated expiration for internal folder sharing. When a user requests access to sensitive documents outside their standard role, the system should automatically revoke that access after a predefined period (e.g., 24 hours), completely eliminating the reliance on manual revocation by managers.
2. **Mandatory Periodic Privilege Audits (AC-6(7)):** 
   Institute an automated quarterly audit where department managers are required to review and explicitly re-approve the access rights of all team members. Any unverified or obsolete privileges must be automatically purged by the system.

---

## ⚖️ 4. Justification for Remediation
Implementing time-bound access and mandatory periodic privilege reviews directly mitigates the human error vector responsible for this incident. By automating privilege expiration, the organization removes the risk of managers forgetting to revoke access. Furthermore, routine audits ensure that access drift is continuously monitored and corrected. These combined enhancements drastically reduce the attack surface, ensuring that sensitive EdTech data remains isolated and protected against both internal negligence and external threats.
