# SQL Security Audit & Threat Hunting: Investigative Log Filtering

[![Language](https://img.shields.io/badge/Language-SQL-blue?style=for-the-badge)](https://en.wikipedia.org/wiki/SQL)
[![Threat Hunting](https://img.shields.io/badge/Domain-Threat_Hunting-darkgreen?style=for-the-badge)](https://www.cisa.gov/topics/cyber-threats-and-advisories)
[![Data Audit](https://img.shields.io/badge/Security-Database_Auditing-red?style=for-the-badge)](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-92.pdf)

## 📌 Project Description
As a security professional, interacting directly with raw database logs is a critical skill for investigating potential security incidents, analyzing access anomalies, and auditing system assets. 

In this project, I performed a comprehensive security analysis by querying corporate data from the `employees` and `log_in_attempts` tables. Using structured SQL filtering techniques—including logical operators (**AND**, **OR**, **NOT**) and pattern matching (**LIKE**)—I isolated specific security events, identified unauthorized cross-border access attempts, and extracted structured datasets required for targeted endpoint patching.

---

## 🔍 Threat Hunting & Anomaly Detection

### 1. Identify After-Hours Failed Login Attempts (Brute Force Indicator)
Anomalous sign-in activity was suspected outside of standard business operational hours. To investigate this potential incident, I audited the `log_in_attempts` table to isolate all failed authentication events that occurred after 18:00 (6:00 PM).

**SQL Query:**
```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = 0;
```
* **How it works:** Targets the audit trail table and applies a dual-condition filter. It isolates timestamps strictly after regular business hours (`> '18:00'`) and exclusively returns unsuccessful logins (`success = 0`), which may indicate brute-force or credential-stuffing attacks.

### 2. Timeline Analysis: Isolating Reconnaissance Activity
A confirmed suspicious event occurred on May 9, 2022. To determine if there was network reconnaissance or initial access attempts leading up to the incident, I queried all login activity that took place on that specific day and the preceding 24 hours.

**SQL Query:**
```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```
* **How it works:** Utilizes the `OR` operator to expand the query range. If a log entry matches either the day of the incident or the day prior, it is successfully populated in the final analysis report for the Incident Response (IR) team.

### 3. Geo-Filtering: Anomalous Foreign Traffic
The SOC determined that recent malicious credential-stuffing attempts did not originate from the company's regional offices in Mexico. To focus investigation efforts strictly on foreign traffic anomalies, I filtered out all regional entries.

**SQL Query:**
```sql
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```
* **How it works:** The wildcard operator (`%`) ensures that any variation of the country data (such as `MEX` or `MEXICO`) matches the text pattern. The `NOT` operator effectively drops all authorized internal connections originating from Mexico, highlighting anomalous foreign connections for immediate threat analysis.

---

## 🛡️ Asset Management & Patch Targeting

### 4. Hardware Location Targeting (East Building)
The security operations team required an asset distribution list to execute localized machine and firmware updates specifically for the Marketing department housed within the East Building facilities.

**SQL Query:**
```sql
SELECT *
FROM employees
WHERE department = 'Marketing' AND office LIKE 'Este%';
```
* **How it works:** Combines a strict departmental filter with a physical location wildcard search. This ensures the output only includes personnel working in office spaces starting with "Este" (e.g., Este-170, Este-320), precisely targeting the affected subnet.

### 5. High-Value Target (HVT) Patch Cycle
A separate, high-priority zero-day patch cycle was rolled out specifically targeting endpoints used by personnel handling corporate financial assets and sensitive customer data pipelines.

**SQL Query:**
```sql
SELECT *
FROM employees
WHERE department = 'Ventas' OR department = 'Finanzas';
```
* **How it works:** The `OR` operator aggregates personnel from both the Sales (`Ventas`) and Finance (`Finanzas`) divisions into a single, unified update roster, ensuring all High-Value Targets receive the critical security patch simultaneously.

### 6. Excluding Hardened Endpoints
The Information Technology (IT) department natively handles system hardening protocols and had already received the enterprise security update. I needed to extract a list of all remaining corporate employees who still required manual patching.

**SQL Query:**
```sql
SELECT *
FROM employees
WHERE NOT department = 'Tecnología de la información';
```
* **How it works:** By applying the `NOT` exclusion to the IT department (`Tecnología de la información`), the database systematically isolates all corporate personnel assigned to non-technical, auxiliary, and administrative departments that still require endpoint remediation.

---

## 📝 Summary & Security Impact
Throughout this operational scenario, I leveraged structured SQL queries to dissect potential infrastructure threats and categorize corporate asset directories. 

By mastering basic syntax constructs and advanced filtering parameters, I successfully narrowed down high-volume system logs to reveal specific post-hours operational failures, excluded authorized geographic locations from active threat vectors, and isolated personnel by physical building coordinates for patch management. This demonstrates a strong capability to systematically audit database ecosystems, enforce network security postures, and support rapid incident response workflows natively from the command line.
