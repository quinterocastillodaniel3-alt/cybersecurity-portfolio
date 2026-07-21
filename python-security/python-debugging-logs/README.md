# Debugging Python Code for Security Automation

[![Location](https://img.shields.io/badge/Location-Medell%C3%ADn%2C_Colombia-success?style=for-the-badge&logo=google-maps)](https://www.google.com/maps/place/Medell%C3%ADn,+Antioquia,+Colombia/) [![Education](https://img.shields.io/badge/Degree-Mechatronics_Engineering-blue?style=for-the-badge&logo=prometric)](https://www.itm.edu.co/) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/daniel-quintero-castillo-4090a4399/)

[![Python](https://img.shields.io/badge/Python-Debugging-blue?style=for-the-badge&logo=python)](https://www.python.org/) [![Automation](https://img.shields.io/badge/Automation-Testing-darkgreen?style=for-the-badge)](https://csrc.nist.gov/glossary/term/software_testing)

## 📌 Project Description
As a security analyst, I applied debugging strategies to resolve syntax, logic, and exception errors in automated Python scripts[cite: 12]. The objective was to identify code issues and adjust them so the programs could successfully evaluate network connections, approve users, and assign security patch schedules[cite: 12].

---

## 🔍 Phase 1: Error Identification & Resolution
During this lab, I systematically reviewed broken code blocks to identify the root cause of execution failures and applied the necessary fixes.

*   **Syntax Errors:** Fixed a missing colon (`:`) at the end of a `for` loop header[cite: 12]. Added missing commas and quotation marks to properly format a list of username strings[cite: 12]. Addressed a missing closing parenthesis in a `print()` function call to prevent an unexpected EOF parsing error[cite: 12].
*   **Logic Errors:** Replaced an assignment operator (`=`) with the comparison operator (`==`) inside an `if` statement to correctly evaluate conditions without breaking the syntax[cite: 12]. Corrected index values to accurately access specific OS patch dates from a `patch_schedule` list by starting at index `0` instead of referencing the wrong elements[cite: 12].
*   **Exceptions:** Resolved an `IndexError: list index out of range` by correcting the index reference to the final element of a 5-element list from `5` to `4`[cite: 12]. Fixed an improperly called string method by rewriting `split.ip_addresses()` to its proper syntax, `ip_addresses.split()`[cite: 12]. Corrected misspelled variable names, such as updating `username_list` to `usernames_list` to prevent reference exceptions[cite: 12].

## 📝 Phase 2: Key Takeaways
*   Debugging is an essential practice used by analysts to identify and fix errors to ensure code runs smoothly and achieves the desired outcome[cite: 12].
*   Python executes code from top to bottom and stops when it encounters an error, meaning the outputted error message will typically show the first error it hits[cite: 12].
*   A key debugging strategy involves running the code, examining if it produces the intended results or an error message, using that information to identify the problematic lines, and running it again after applying fixes[cite: 12].
*   Common errors in Python fall into three categories: syntax errors (e.g., missing punctuation), logic errors (e.g., incorrect list indices), and exceptions (e.g., misspelled variables or incorrectly called methods)[cite: 12].
