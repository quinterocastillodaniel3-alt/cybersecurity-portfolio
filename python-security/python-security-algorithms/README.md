# Security Algorithms & Identity Verification

[![Location](https://img.shields.io/badge/Location-Medell%C3%ADn%2C_Colombia-success?style=for-the-badge&logo=google-maps)](https://www.google.com/maps/place/Medell%C3%ADn,+Antioquia,+Colombia/) [![Education](https://img.shields.io/badge/Degree-Mechatronics_Engineering-blue?style=for-the-badge&logo=prometric)](https://www.itm.edu.co/) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/daniel-quintero-castillo-4090a4399/)

[![Python](https://img.shields.io/badge/Python-Algorithms-blue?style=for-the-badge&logo=python)](https://www.python.org/) [![IAM](https://img.shields.io/badge/IAM-Access_Control-darkgreen?style=for-the-badge)](https://csrc.nist.gov/glossary/term/identity_and_access_management)

## 📌 Project Description
This project focuses on developing a step-by-step algorithmic solution to automate identity and access management[cite: 16]. The objective was to build a verification script that confirms if a user is approved on the system and validates whether they are logging in from their specifically assigned device[cite: 16].

---

## 🔍 Phase 1: List Synchronization & Nested Logic
The tasks involved managing parallel lists and constructing deep conditional logic.

*   **List Operations:** Maintained synchronized `approved_users` and `approved_devices` lists by using `.append()` for new hires and `.remove()` for departing employees[cite: 16].
*   **Cross-Referencing:** Used `.index(username)` to locate a user's position in the first list, then applied that same index integer to verify the corresponding hardware in the devices list[cite: 16].
*   **Nested Conditionals:** Built a complete `login(username, device_id)` function encompassing outer conditionals (to check if the user exists) and inner conditionals (to verify hardware match)[cite: 16].
*   **Complex Routing:** Utilized `if`, `elif`, and `else` alongside the `and` operator to route authentication flows and trigger specific access denial or approval messages[cite: 16].

## 📝 Phase 2: Key Takeaways
*   Algorithms are step-by-step procedures used by security analysts to resolve specific operational problems[cite: 16].
*   Parallel lists can be synchronized by leveraging identical index values to pair related datasets[cite: 16].
*   Nested conditionals (placing an `if` statement inside another) provide a granular way to handle multi-factor verification scenarios[cite: 16].
