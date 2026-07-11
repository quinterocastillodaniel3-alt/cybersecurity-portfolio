# Incident Response & Data Risk Assessment: Principle of Least Privilege

## 📌 Project Description
As a cybersecurity professional for an Educational Technology (EdTech) company, I was tasked with investigating an internal data breach. The organization develops an automated grading application that handles highly sensitive data from academic institutions, instructors, parents, and students. A data leak occurred when internal product plans and marketing materials were exposed on social media by an external business partner. This project involves analyzing the incident, reviewing the security controls aligned with the **NIST SP 800-53** framework, and proposing control enhancements to enforce the Principle of Least Privilege and prevent future data exposure.

---

## 🔍 1. Incident Analysis (The Problem)
An investigation into the data leak revealed a critical breakdown in access management. A Customer Success Representative was temporarily granted access to a manager's root folder containing sensitive product plans and marketing materials. The manager failed to revoke this access after it was no longer needed. Subsequently, during a sales call, the representative accidentally shared the link to the entire root folder with an external business partner—instead of just the marketing materials—leading to the unauthorized public exposure of internal documents on social media.

---

## 📖 2. Framework Review: NIST SP 800-53 (AC-6)
To address the systemic failures that led to the incident, I reviewed **NIST SP 800-53: AC-6 (Least Privilege)**. This security control mandates that organizations grant users only the absolute minimum access authorizations necessary to perform their designated job functions. It emphasizes that privileges must be strictly controlled, routinely reviewed, and promptly revoked when they are no longer required, thereby limiting the potential damage of accidental sharing or compromised accounts.

---

## 🛡️ 3. Security Control Enhancements (Recommendations)
To align the organization's data handling processes with NIST guidelines and enforce the Principle of Least Privilege, I recommended the following control enhancements:

1. **Implement Time-Bound Access Controls:** Enforce temporary, automated expiration for internal folder sharing. When a user requests access to sensitive documents outside their standard role, the system should automatically revoke that access after a predefined period (e.g., 24 hours), eliminating the reliance on manual revocation by managers.
2. **Mandatory Periodic Privilege Audits (AC-6(7)):** Institute an automated quarterly audit where department managers are required to review and explicitly re-approve the access rights of all team members. Any unverified or obsolete privileges must be automatically purged by the system.

---

## ⚖️ 4. Justification for Remediation
Implementing time-bound access and mandatory periodic privilege reviews directly mitigates the human error vector responsible for this incident. By automating privilege expiration, the organization removes the risk of managers forgetting to revoke access. Furthermore, routine audits ensure that access drift (users accumulating excessive permissions over time) is continuously monitored and corrected. These combined enhancements drastically reduce the attack surface, ensuring that sensitive EdTech data remains isolated and protected against both internal negligence and external exposure.
