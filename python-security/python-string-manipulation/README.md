# String Manipulation & Data Extraction

[![Location](https://img.shields.io/badge/Location-Medell%C3%ADn%2C_Colombia-success?style=for-the-badge&logo=google-maps)](https://www.google.com/maps/place/Medell%C3%ADn,+Antioquia,+Colombia/) [![Education](https://img.shields.io/badge/Degree-Mechatronics_Engineering-blue?style=for-the-badge&logo=prometric)](https://www.itm.edu.co/) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/daniel-quintero-castillo-4090a4399/)

[![Python](https://img.shields.io/badge/Python-Strings-blue?style=for-the-badge&logo=python)](https://www.python.org/) [![Data Formatting](https://img.shields.io/badge/Data_Formatting-Parsing-darkgreen?style=for-the-badge)](https://owasp.org/www-community/)

## 📌 Project Description
In this project, I automated the formatting of employee IDs and extracted specific components from device IDs and URLs using string operations[cite: 15]. Becoming comfortable with string manipulation is essential since most security logs and identifiers are stored as text data[cite: 15].

---

## 🔍 Phase 1: Slicing & Type Conversion
The lab required leveraging string indices and built-in methods to isolate necessary data.

*   **Type Conversion:** Used `str()` to convert a four-digit integer employee ID into a string format[cite: 15].
*   **Length Verification:** Applied the `len()` function within an `if` statement to check if the ID was less than five digits long[cite: 15].
*   **Standardization:** Concatenated the character `"E"` to the front of non-compliant IDs to enforce a new standardized format[cite: 15].
*   **String Slicing (Bracket Notation):** Extracted specific characters from a `device_id` string using precise index values (e.g., `device_id[0:3]`)[cite: 15].
*   **Dynamic Extraction:** Utilized the `.index()` method to locate the starting position of `.com` in a URL, using that variable to slice out the core domain name dynamically[cite: 15].

## 📝 Phase 2: Key Takeaways
*   String indexing in Python begins at `0`, and when slicing using bracket notation (e.g., `[0:3]`), the ending index is exclusive[cite: 15].
*   The `.index()` method finds the first occurrence of a specified substring and returns its starting location[cite: 15].
*   The `len()` function accurately returns the total number of characters contained within a string[cite: 15].
