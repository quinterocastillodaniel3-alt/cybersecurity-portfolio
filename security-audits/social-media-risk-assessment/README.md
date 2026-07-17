# Incident Post-Mortem & Risk Assessment: Social Media Data Breach

[![Incident Response](https://img.shields.io/badge/Security-Incident_Response-blue?style=for-the-badge)](https://www.cisa.gov/safecom/incident-response)
[![IAM & MFA](https://img.shields.io/badge/Domain-IAM_%26_MFA-darkgreen?style=for-the-badge)](https://www.nist.gov/itl/applied-cybersecurity/tig/back-basics-multi-factor-authentication)
[![Network Security](https://img.shields.io/badge/Infrastructure-Network_Defense-red?style=for-the-badge)](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-41Rev1.pdf)

## 📌 Incident Summary & Vulnerability Analysis
A social media enterprise recently experienced a critical data exfiltration incident, resulting in the compromise of sensitive customer Personally Identifiable Information (PII), specifically user names and residential addresses. 

A post-incident security audit of the network infrastructure revealed four critical vulnerabilities that facilitated the breach:
1. **Credential Sharing:** Widespread employee practice of sharing account passwords.
2. **Default Credentials:** The primary Database Administrator (DBA) account was left utilizing factory-default credentials.
3. **Perimeter Defense Failure:** Network firewalls lacked established Access Control Lists (ACLs) to filter inbound and outbound traffic.
4. **Lack of Authentication Depth:** Multi-Factor Authentication (MFA) was completely absent across the enterprise.

---

## 🛡️ Strategic Remediation Plan
To address the root causes of the data breach, secure the network perimeter, and achieve regulatory data privacy compliance, the following infrastructure hardening methods must be implemented immediately.

### 1. Multi-Factor Authentication (MFA) & Strict IAM Policies
* **Security Justification:** Implementing MFA directly mitigates the risks associated with compromised or shared passwords. Even if an unauthorized threat actor obtains legitimate credentials, network access is blocked without the secondary authentication token (e.g., TOTP authenticator app or hardware key). Paired with strict Identity and Access Management (IAM) policies, this ensures non-repudiation and individual accountability.
* **Operational Cadence:** MFA must be enforced **continuously** at all login gateways. IAM privileges and user roles must be audited **quarterly** to prevent access drift.

### 2. Secure Baseline Configurations & Credential Hardening
* **Security Justification:** The data exfiltration was directly exacerbated by an exposed database utilizing default credentials. Updating the corporate baseline configuration to force a password reset upon initial deployment eliminates this critical attack vector. Furthermore, a system-wide policy that rejects weak passwords, enforces cryptographic complexity, and prevents the reuse of historical passwords hardens all service and user accounts.
* **Operational Cadence:** Default passwords must be rotated **immediately** during system provisioning. Automated password rotation and complexity requirements must be enforced **every 90 days**.

### 3. Perimeter Defense & Firewall Rule Implementation
* **Security Justification:** A firewall without explicit rules functions merely as a router, providing zero security value. Establishing strict firewall rules and implementing port filtering will block anomalous network traffic from penetrating or leaving the private network. By adopting an **"Implicit Deny" (Default Deny)** posture, only explicitly verified and necessary traffic is permitted to traverse specific, monitored ports.
* **Operational Cadence:** Firewall traffic should be monitored **continuously** via automated SIEM alerts. Rule sets and ACLs must be manually reviewed and audited **monthly**, or immediately following any significant architectural change or threat intelligence alert.
