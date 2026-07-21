# Access Control & Conditional Statements in Python

[![Location](https://img.shields.io/badge/Location-Medell%C3%ADn%2C_Colombia-success?style=for-the-badge&logo=google-maps)](https://www.google.com/maps/place/Medell%C3%ADn,+Antioquia,+Colombia/) [![Education](https://img.shields.io/badge/Degree-Mechatronics_Engineering-blue?style=for-the-badge&logo=prometric)](https://www.itm.edu.co/) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/daniel-quintero-castillo-4090a4399/)

[![Python](https://img.shields.io/badge/Python-Conditionals-blue?style=for-the-badge&logo=python)](https://www.python.org/) [![Access Control](https://img.shields.io/badge/Access_Control-Logic-darkgreen?style=for-the-badge)](https://owasp.org/www-community/Access_Control)

## 📌 Project Description
In this project, I used conditional statements to ensure specific parameters were met before executing actions. The scenario involved checking user operating systems for required updates and validating login attempts against approved lists and authorized operational hours.

---

## 🔍 Phase 1: Logic & Condition Evaluations
The tasks focused on structuring `if`, `elif`, and `else` statements alongside logical operators to evaluate access policies.

*   **OS Update Verification:** Written conditions to evaluate a `system` variable; if it was `"OS 2"`, no update was required, whereas `"OS 1"` and `"OS 3"` prompted an update message.
*   **Access Control:** Created logic to verify if a given `username` attempting to log in existed within an `approved_list`.
*   **Time-Based Restrictions:** Evaluated a Boolean variable, `organization_hours`, to determine if the access attempt occurred during valid operational times.
*   **Concise Logic:** Used the `and` / `or` logical operators to combine conditions into a single statement, reducing code length while maintaining functionality.

## 📝 Phase 2: Key Takeaways
*   Conditional statements allow you to check whether a specific set of conditions has been met before executing code.
*   The `==` comparison operator is used to evaluate if one specific value equals another.
*   Logical operators, specifically `and` and `or`, permit checking multiple conditions simultaneously within a single statement.
