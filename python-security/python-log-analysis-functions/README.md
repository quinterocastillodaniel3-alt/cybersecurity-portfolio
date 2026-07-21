# Advanced Functions & Login Analysis

[![Location](https://img.shields.io/badge/Location-Medell%C3%ADn%2C_Colombia-success?style=for-the-badge&logo=google-maps)](https://www.google.com/maps/place/Medell%C3%ADn,+Antioquia,+Colombia/) [![Education](https://img.shields.io/badge/Degree-Mechatronics_Engineering-blue?style=for-the-badge&logo=prometric)](https://www.itm.edu.co/) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/daniel-quintero-castillo-4090a4399/)

[![Python](https://img.shields.io/badge/Python-Data_Analysis-blue?style=for-the-badge&logo=python)](https://www.python.org/) [![Log Analysis](https://img.shields.io/badge/Log_Analysis-Metrics-darkgreen?style=for-the-badge)](https://www.cisa.gov/cybersecurity)

## 📌 Project Description
This project focuses on using both built-in and user-defined Python functions to analyze lists of failed login attempts[cite: 14]. The objective was to identify malicious patterns and compare daily user login metrics against historical averages[cite: 14].

---

## 🔍 Phase 1: Data Parsing & Mathematical Logic
The tasks involved applying functions to extract statistical extremes and calculate ratios.

*   **Built-in Functions:** Used `sorted()` to arrange a chronological list of failed login attempts in ascending numerical order[cite: 14].
*   **Outlier Identification:** Applied the `max()` function to instantly isolate the highest number of failed logins from the dataset[cite: 14].
*   **Parameter Handling:** Defined `analyze_logins()` to accept multiple parameters: `username`, `current_day_logins`, and `average_day_logins`[cite: 14].
*   **Return Statements:** Calculated the `login_ratio` within the function and used the `return` keyword to output the result for external use[cite: 14].
*   **Threshold Alerts:** Implemented a conditional statement to trigger a security alert if the returned `login_analysis` variable equaled or exceeded a ratio of 3[cite: 14].

## 📝 Phase 2: Key Takeaways
*   Functions can take in multiple parameters, execute calculations, and output a specific result using the `return` keyword instead of just printing it[cite: 14].
*   Built-in functions like `sorted()` and `max()` are critical for efficiently identifying anomalies and extremes within security datasets[cite: 14].
*   Output from functions can be directly assigned to variables for further conditional processing[cite: 14].
