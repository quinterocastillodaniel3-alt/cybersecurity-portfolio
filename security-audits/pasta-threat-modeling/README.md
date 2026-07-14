# Threat Modeling with PASTA Framework: E-Commerce Mobile App

## 📌 Project Description
Threat modeling is a foundational component of secure software development. In this project, I acted as a Security Analyst for a sneaker enthusiast company preparing to launch a new e-commerce mobile application. To proactively identify vulnerabilities and assess the application's risk profile, I utilized the **PASTA (Process for Attack Simulation and Threat Analysis)** framework. This seven-stage methodology bridges the gap between technical security risks and business impact, ensuring the application is secure by design before deployment.

---

## 🏗️ Stage I: Define Business and Security Objectives
The primary goal of this stage is to understand why the application was developed and its core functions. The sneaker app aims to seamlessly connect buyers and sellers, process transactions clearly, and facilitate direct messaging.

**Key Business & Security Requirements:**
* **Transaction Processing:** The app must securely process financial transactions while maintaining strict regulatory compliance to avoid legal issues.
* **Data Privacy:** Users must feel confident that their personal and financial data is handled responsibly.
* **Backend Processing:** The architecture requires heavy backend data processing to manage inventory, ratings, and user accounts efficiently.

---

## 💻 Stage II: Define the Technical Scope
Understanding the attack surface requires defining the technological stack. The application utilizes the following core technologies:
* **API (Application Programming Interface)**
* **PKI (Public Key Infrastructure)** utilizing AES and RSA encryption
* **SHA-256 hashing**
* **SQL (Structured Query Language)**

**Technology Prioritization:**
When prioritizing security assessments, I focus primarily on the **API** and **SQL** integrations. APIs act as the main gateway between the mobile client and the backend, making them prime targets for unauthorized data access. Simultaneously, SQL databases hold the core user and inventory data; if the input is not strictly sanitized, it presents a critical risk of injection attacks that could compromise the entire system.

---

## 🔄 Stage III: Decompose the Application
During this stage, we analyze the application's data handling processes using a Data Flow Diagram (DFD). 

![PASTA Data Flow Diagram](pasta-data-flow-diagram.png)

**Process Breakdown (Product Search):**
1. The **User** initiates a request by searching for sneakers for sale.
2. The request hits the **Product search process**, which queries the backend **Database**.
3. The database returns listings of current inventory back to the user.

Each transition point between the user, the process, and the database represents a boundary where data must be encrypted and validated.

---

## ⚠️ Stage IV: Threat Analysis
Threat analysis identifies potential actors and actions that pose a risk to the application's data.
1. **External Threats:** Cybercriminals attempting to intercept sensitive payment data (Man-in-the-Middle attacks) during the transaction process, or automated botnets attempting to scrape user data via the API.
2. **Internal Threats:** Insider threats or employees falling victim to social engineering, inadvertently granting attackers access to the backend database.

---

## 🕳️ Stage V: Vulnerability Analysis
This stage maps the identified threats to actual weaknesses in the technologies listed in Stage II.
1. **Weaknesses in the Database:** If user input is not properly sanitized, the SQL database is highly vulnerable to SQL Injection (SQLi) attacks.
2. **Flaws in the Network / Codebase:** Insecure API endpoints or misconfigured PKI implementation could lead to unencrypted data transmission, exposing credit card details or session tokens.

---

## 🌳 Stage VI: Attack Modeling
Using an Attack Tree, we visually map how threat actors might exploit the vulnerabilities to compromise the system. Applications typically have large, complex attack trees with many branches.

![PASTA Attack Tree](pasta-attack-tree.png)

**Sample Attack Path Targeting User Data:**
* **Goal:** Compromise User Data
  * **Vector 1: SQL Injection**
    * *Root Cause:* Lack of prepared statements in the application codebase.
  * **Vector 2: Session Hijacking**
    * *Root Cause:* Weak login credentials or lack of secure token handling.

---

## 🛡️ Stage VII: Risk Analysis and Impact (Security Controls)
To mitigate the threats and vulnerabilities identified in the PASTA framework, the following security controls must be implemented before launch to reduce risk:
1. **Prepared Statements (Parameterized Queries):** To completely neutralize the risk of SQL injection outlined in the attack tree.
2. **Robust Encryption & Hashing:** Enforce AES for data at rest, TLS (via PKI) for data in transit, and SHA-256 with salt for secure password storage.
3. **Multi-Factor Authentication (MFA):** To mitigate the risk of session hijacking and weak login credentials.
4. **Principle of Least Privilege (PoLP):** Ensure that the APIs and backend service accounts only have the minimum database permissions necessary to execute their specific functions.
