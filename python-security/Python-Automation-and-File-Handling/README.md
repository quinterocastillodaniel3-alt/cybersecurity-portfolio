# Python Automation & File Handling for SecOps

[![Location](https://img.shields.io/badge/Location-Medell%C3%ADn%2C_Colombia-success?style=for-the-badge&logo=google-maps)](https://www.google.com/maps/place/Medell%C3%ADn,+Antioquia,+Colombia/) [![Education](https://img.shields.io/badge/Degree-Mechatronics_Engineering-blue?style=for-the-badge&logo=prometric)](https://www.itm.edu.co/) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/daniel-quintero-castillo-4090a4399/)

[![Python](https://img.shields.io/badge/Python-Automation-blue?style=for-the-badge&logo=python)](https://www.python.org/) [![SecOps](https://img.shields.io/badge/SecOps-Threat_Detection-darkgreen?style=for-the-badge)](https://www.cisa.gov/cybersecurity)

## 📌 Project Description
This repository covers the foundational concepts of using Python to automate security tasks, specifically focusing on interacting with log files to detect suspicious network activity and automate incident triage. Understanding how to programmatically open, read, and manipulate files is a mandatory skill for security analysts because almost all relevant cybersecurity information and system events are stored in log files.

---

## 🔍 Phase 1: Automating Threat Detection
Security Operations Centers (SOC) generate massive amounts of log data daily. Python scripts are essential for automating the parsing of these logs to detect potential Indicators of Compromise (IoCs) efficiently. 

By automating log analysis, security teams can rapidly track and flag:
*   **Anomalous Login Times:** Successful or failed authentication attempts occurring completely outside of normal business hours.
*   **Brute Force Attacks:** Multiple failed login attempts targeting a single account or system within a very short timeframe.
*   **Geolocation/IP Anomalies:** Authentication attempts originating from unusual IP addresses, unknown subnets, or unauthorized geographic locations.

---

## 📝 Phase 2: Key Takeaways

### Iteration and Automation
To automate the analysis of thousands of log entries, Python relies on iterative control flow.
*   **The `for` Loop:** This component contributes to automation by allowing a script to perform the exact same action a specific number of times based on a sequence. 
*   **Security Context:** In cybersecurity, `for` loops are constantly used to iterate line-by-line through a massive log file or item-by-item through a list of extracted IP addresses to check against a threat intelligence database.

### Common Log File Formats
Security logs are typically stored in plain text or structured text formats so they can be easily ingested by SIEM platforms or parsed by Python scripts. The most common formats include:
*   **`.txt` (Text Files):** Standard plain text files commonly used for raw syslog output or application logs.
*   **`.csv` (Comma-Separated Values):** Highly structured text files where each line is a record and fields are separated by commas. These are excellent for exporting data from a SIEM or database for automated analysis.
