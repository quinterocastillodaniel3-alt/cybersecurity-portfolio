# Debugging Python Code for Security Automation

[![Location](https://img.shields.io/badge/Location-Medell%C3%ADn%2C_Colombia-success?style=for-the-badge&logo=google-maps)](https://www.google.com/maps/place/Medell%C3%ADn,+Antioquia,+Colombia/) [![Education](https://img.shields.io/badge/Degree-Mechatronics_Engineering-blue?style=for-the-badge&logo=prometric)](https://www.itm.edu.co/) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/daniel-quintero-castillo-4090a4399/)

[![Python](https://img.shields.io/badge/Python-Debugging-blue?style=for-the-badge&logo=python)](https://www.python.org/) [![Automation](https://img.shields.io/badge/Automation-Testing-darkgreen?style=for-the-badge)](https://csrc.nist.gov/glossary/term/software_testing)

## 📌 Project Description
As a security analyst, I applied debugging strategies to ensure automated processes and scripts run smoothly[cite: 14]. The primary objective was to identify errors in code, such as syntax or logic issues, and resolve them so the programs could successfully evaluate network connections, approve users, and assign security patch schedules[cite: 14].

---

## 🔍 Phase 1: Error Identification & Resolution
During this project, I systematically reviewed broken code blocks to identify the root cause of execution failures and applied the necessary fixes.

*   **Syntax Errors:** Fixed a missing colon (`:`) at the end of a `for` loop header[cite: 14]. Added missing commas and quotation marks to properly format elements within a list of usernames[cite: 14]. Addressed a missing closing parenthesis in a `print()` function call to prevent an unexpected EOF parsing error[cite: 14].
*   **Logic Errors:** Replaced an assignment operator (`=`) with the comparison operator (`==`) inside an `if` statement to correctly evaluate conditions[cite: 14]. Corrected index values to accurately access specific OS patch dates from a `patch_schedule` list by starting at index `0`[cite: 14].
*   **Exceptions:** Resolved an `IndexError: list index out of range` by correcting the index reference to the final element of a 5-element list from `5` to `4`[cite: 14]. Fixed an improperly called string method by rewriting `split.ip_addresses()` to its proper syntax, `ip_addresses.split()`[cite: 14]. Corrected misspelled variable names to prevent reference exceptions[cite: 14].

---

## 📝 Phase 2: Key Takeaways
*   Debugging is an essential practice used by analysts to identify errors in code and fix them to ensure scripts run smoothly[cite: 14].
*   Python executes code from top to bottom and stops once it encounters an error, meaning the outputted error message will typically show the first error it hits[cite: 14].
*   A key strategy for debugging is running the code, examining if it produces the intended results or an error message, and using that information to identify the problematic lines[cite: 14].
*   Common types of errors in Python include syntax errors (e.g., missing punctuation), logic errors (e.g., incorrect list indices), and exceptions (e.g., incorrectly called string methods)[cite: 14].
