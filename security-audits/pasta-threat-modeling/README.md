# Threat Modeling & Risk Analysis: PASTA Framework

[![Threat Modeling](https://img.shields.io/badge/Security-Threat_Modeling-blue?style=for-the-badge)](https://owasp.org/www-community/Threat_Modeling)
[![Framework](https://img.shields.io/badge/Framework-PASTA-darkgreen?style=for-the-badge)](https://owasp.org/www-project-pasta-threat-modeling/)
[![AppSec](https://img.shields.io/badge/Domain-Application_Security-red?style=for-the-badge)](https://owasp.org/www-project-top-ten/)

## 📌 Project Description
Threat modeling is a foundational component of secure software development (DevSecOps). In this project, I acted as a Security Analyst for a sneaker enthusiast company preparing to launch a new e-commerce mobile application. 

To proactively identify vulnerabilities and assess the application's risk profile, I utilized the **PASTA (Process for Attack Simulation and Threat Analysis)** framework. This seven-stage, risk-centric methodology bridges the gap between technical security flaws and business impact, ensuring the application is secure by design before deployment.

---

## 🏗️ Stage I: Define Business and Security Objectives
The primary goal of this stage is to align security requirements with business objectives. The e-commerce app aims to seamlessly connect buyers and sellers, process financial transactions, and facilitate direct messaging.

**Key Business & Security Requirements:**
* **Transaction Processing:** Securely process financial data while maintaining strict regulatory compliance (e.g., PCI-DSS) to prevent legal liability.
* **Data Privacy:** Ensure confidentiality and integrity of Personally Identifiable Information (PII) so users feel confident their data is handled responsibly.
* **Backend Processing:** High availability and fault tolerance for managing inventory, user ratings, and accounts efficiently.

---

## 💻 Stage II: Define the Technical Scope
Understanding the attack surface requires defining the underlying technological stack. The application utilizes the following core technologies:
* **API (Application Programming Interface):** RESTful endpoints facilitating client-server communication.
* **PKI (Public Key Infrastructure):** Utilizing AES for symmetric encryption and RSA for asymmetric key exchange.
* **Cryptography:** SHA-256 for secure password hashing.
* **Database:** SQL (Structured Query Language) for relational data storage.

**Technology Prioritization:**
Security assessments prioritize the **API** and **SQL** integrations. APIs act as the primary gateway between the mobile client and the backend, making them prime targets for unauthorized data access. Simultaneously, SQL databases hold core user and financial data; insufficient input sanitization presents a critical risk of injection attacks that could compromise the entire system.

---

## 🔄 Stage III: Decompose the Application
During this stage, the application's data handling processes are analyzed using a Data Flow Diagram (DFD) to map trust boundaries.

![PASTA Data Flow Diagram](pasta-data-flow-diagram.png)

**Process Breakdown (Product Search):**
1. The **User** initiates a request by searching for sneakers for sale.
2. The request traverses the trust boundary to the **Product Search Process**, querying the backend **Database**.
3. The database returns listings of current inventory back to the user.

*Note: Each transition point between the user, the process, and the database represents a boundary where data must be validated upon entry and encrypted in transit.*

---

## ⚠️ Stage IV: Threat Analysis
Threat analysis identifies potential actors and attack vectors that pose a risk to the application's data flow.
1. **External Threats:** Cybercriminals attempting to intercept sensitive payment data via Man-in-the-Middle (MitM) attacks, or automated botnets attempting to scrape user data and exhaust server resources via the API.
2. **Internal Threats:** Insider threats or employees falling victim to social engineering, inadvertently granting attackers access to backend administrative panels or the database.

---

## 🕳️ Stage V: Vulnerability Analysis
This stage maps the identified threats to actual weaknesses in the technologies defined in Stage II (referencing standards like the OWASP Top 10).
1. **Weaknesses in the Database:** If user input is not properly sanitized and parameterized, the SQL database is highly vulnerable to **SQL Injection (SQLi)**.
2. **Flaws in the Network / Codebase:** Insecure API endpoints, lack of rate limiting, or misconfigured PKI implementation could lead to unencrypted data transmission, exposing credit card details or session tokens to interception.

---

## 🌳 Stage VI: Attack Modeling
Using an Attack Tree, we visually map how threat actors might logically exploit the identified vulnerabilities to compromise the system.

![PASTA Attack Tree](pasta-attack-tree.png)

**Sample Attack Path Targeting User Data:**
* **Goal:** Compromise User Data (PII/Financial)
  * **Vector 1: SQL Injection**
    * *Root Cause:* Lack of prepared statements and input validation in the backend code.
  * **Vector 2: Session Hijacking**
    * *Root Cause:* Weak login credentials, lack of MFA, or transmission of session tokens over unencrypted channels.

---

## 🛡️ Stage VII: Risk Analysis & Security Controls
To mitigate the threats and vulnerabilities identified in the PASTA framework, the following defense-in-depth security controls must be implemented prior to production launch:
1. **Prepared Statements (Parameterized Queries):** To completely neutralize the risk of SQL injection outlined in the attack tree.
2. **Robust Encryption & Hashing:** Enforce AES for Data at Rest, TLS (via PKI) for Data in Transit, and SHA-256 with a cryptographic salt for secure password storage.
3. **Multi-Factor Authentication (MFA):** To mitigate the risk of session hijacking, credential stuffing, and weak login credentials.
4. **Principle of Least Privilege (PoLP):** Ensure that APIs and backend service accounts only possess the minimum database permissions (e.g., READ-only for search functions) necessary to execute their specific tasks.
