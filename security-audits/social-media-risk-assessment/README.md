# Security Risk Assessment Report: Social Media Organization Data Breach

## Incident Overview
A social media organization recently experienced a significant data breach, compromising customers' personal information (names and addresses). A security audit of the network revealed four critical vulnerabilities that facilitated the breach:
1. Employees sharing passwords.
2. The database administrator password was left as default.
3. Firewalls lacked established rules to filter inbound and outbound traffic.
4. Multi-Factor Authentication (MFA) was not implemented.

---

## Part 1: Select up to three hardening tools and methods to implement 

To address the root causes of the data breach and secure the overall network, the following hardening methods must be implemented immediately:

1. **Implementation of Multi-Factor Authentication (MFA) and Strict IAM Policies.**
2. **Baseline Configuration Updates (Enforcing Strong Password Policies and removing default credentials).**
3. **Firewall Maintenance and Port Filtering.**

---

## Part 2: Explain your recommendations

### 1. Multi-Factor Authentication (MFA) and IAM Policies
* **Why it is effective:** Implementing MFA directly mitigates the risks associated with employees sharing passwords. Even if an unauthorized user obtains a password, they will not be able to access the network without the secondary authentication device (like a hardware token or authenticator app). Coupled with strict Identity and Access Management (IAM) policies, we can ensure each employee uses a unique, untransferable login.
* **Frequency:** MFA must be enforced **continuously** for all logins. IAM policies should be audited **quarterly** to ensure privileges are still appropriately assigned.

### 2. Baseline Configuration Updates (Password Policies)
* **Why it is effective:** The breach was exacerbated by a database administrator using default credentials. Updating the baseline configuration to force a password change upon first login eliminates this critical vulnerability. Furthermore, a system-wide policy that rejects weak passwords and prevents the reuse of old passwords will harden all accounts across the network.
* **Frequency:** Default passwords must be changed **immediately** upon system deployment. Password rotation and complexity requirements should be enforced automatically by the system **every 90 days**.

### 3. Firewall Maintenance and Port Filtering
* **Why it is effective:** Without rules, a firewall is virtually useless. Establishing explicit firewall rules and implementing Port Filtering will block unauthorized or malicious network traffic from entering or leaving the private network. By adopting a "default deny" policy, only necessary, verified traffic will be allowed to pass through the specific required ports.
* **Frequency:** Firewall maintenance should be performed **continuously** through automated monitoring. Rule sets should be manually reviewed and updated **monthly**, or immediately following any significant infrastructure change or security alert.
