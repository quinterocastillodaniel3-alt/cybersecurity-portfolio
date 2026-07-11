# SQL Security Audit: Applying Filters to Investigative Queries

## 📌 Project Description
As a security professional in a large organization, my responsibilities include investigating potential security incidents, analyzing access anomalies, and auditing system assets to ensure overall environment integrity. In this project, I performed a comprehensive security analysis by querying organizational data from the `employees` and `log_in_attempts` tables. Using SQL filtering techniques with **AND**, **OR**, **NOT**, and pattern matching with **LIKE**, I isolated specific security events, identified unauthorized cross-border access attempts, and extracted structured datasets needed for targeted critical system updates.

---

## 🔒 1. Retrieve After-Hours Failed Login Attempts
Anomalous sign-in activity was suspected outside of standard business operational hours. To investigate this potential security incident, I audited the `log_in_attempts` table to isolate all failed login attempts that occurred after 18:00 (6:00 PM).

**SQL Query:**
```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = 0;
```

**How it works:**
* `SELECT *`: Instructs the database engine to retrieve all columns from the target dataset.
* `FROM log_in_attempts`: Targets the login audit trail repository table.
* `WHERE login_time > '18:00'`: Applies a logical filter to isolate timestamps recorded strictly after regular business hours.
* `AND success = 0`: Integrates a second condition using the `AND` operator, ensuring the query only returns results where the login was unsuccessful (using `0` to denote `FALSE`).

---

## 📅 2. Retrieve Login Attempts on Specific Dates
A confirmed suspicious event occurred on May 9, 2022. To determine if there was reconnaissance activity leading up to the incident, I reviewed all login attempts that took place on that specific day as well as the calendar day prior.

**SQL Query:**
```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

**How it works:**
* `WHERE login_date = '2022-05-09'`: Sets a filter condition for the exact day of the reported incident.
* `OR login_date = '2022-05-08'`: Uses the `OR` operator to expand the query range to include the preceding 24 hours. If an event matches either date condition, it is successfully populated in the final analysis report.

---

## 🌍 3. Retrieve Login Attempts Outside of Mexico
The Incident Response team determined that recent malicious credential-stuffing attempts did not originate from the company's regional offices in Mexico. To focus investigation efforts on foreign traffic anomalies, I filtered out all regional entries mapped to Mexico.

**SQL Query:**
```sql
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```

**How it works:**
* `LIKE 'MEX%'`: The wildcard operator (`%`) ensures that any variation of the country data (such as `MEX` or `MEXICO`) matches the text pattern.
* `NOT`: Modifies the pattern match condition to return the inverse dataset. This effectively drops all internal connections originating from Mexico and highlights foreign connections for threat analysis.

---

## 🏢 4. Retrieve Employees in Marketing and East Building
The security team required an asset distribution list to execute localized machine and firmware updates for the Marketing department within the East Building facilities.

**SQL Query:**
```sql
SELECT *
FROM employees
WHERE department = 'Marketing' AND office LIKE 'Este%';
```

**How it works:**
* `FROM employees`: Shifts the query focus to the corporate staff directory table.
* `department = 'Marketing'`: Targets personnel assigned exclusively to the Marketing sector.
* `AND office LIKE 'Este%'`: Combines the department filter with a physical location wildcard search. This ensures the output only includes personnel working in office spaces starting with "Este" (e.g., Este-170, Este-320), filtering out other buildings.

---

## 💼 5. Retrieve Employees in Finance or Sales
A separate, high-priority patch cycle was rolled out specifically targeting endpoints used by personnel handling corporate financial assets and customer pipelines.

**SQL Query:**
```sql
SELECT *
FROM employees
WHERE department = 'Ventas' OR department = 'Finanzas';
```

**How it works:**
* `WHERE department = 'Ventas'`: Filters for personnel within the Sales division.
* `OR department = 'Finanzas'`: Extends the scope to include the Finance division. The `OR` operator aggregates personnel from both distinct administrative departments into a single unified update log.

---

## 🛠️ 6. Retrieve All Employees Not in IT
The Information Technology department handles system hardening protocols natively and had already received an enterprise security update. I needed to extract a list of all remaining corporate employees who still required the patch.

**SQL Query:**
```sql
SELECT *
FROM employees
WHERE NOT department = 'Tecnología de la información';
```

**How it works:**
* `WHERE NOT`: Evaluates the statement condition and excludes any records that meet the specified string.
* `department = 'Tecnología de la información'`: Specifies the IT department. By applying `NOT`, the database isolates all corporate personnel assigned to non-technical, auxiliary, and administrative departments that still require manual endpoint hardening.

---

## 📝 Summary
Throughout this operational scenario, I leveraged structured SQL queries to dissect potential infrastructure threats and categorize corporate asset directories. By implementing basic syntax constructs and filtering parameters, I was able to narrow down high-volume system logs to reveal specific post-hours operational failures, exclude specific geographic locations from active investigation vectors, and isolate personnel parameters by physical building coordinates and departmental duties. Mastering these fundamental data extraction methods allows me to systematically audit database ecosystems, enforce network security postures, and support rapid incident response workflows.
