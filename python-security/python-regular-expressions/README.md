# Parsing Logs with Regular Expressions (RegEx)

[![Location](https://img.shields.io/badge/Location-Medell%C3%ADn%2C_Colombia-success?style=for-the-badge&logo=google-maps)](https://www.google.com/maps/place/Medell%C3%ADn,+Antioquia,+Colombia/) [![Education](https://img.shields.io/badge/Degree-Mechatronics_Engineering-blue?style=for-the-badge&logo=prometric)](https://www.itm.edu.co/) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/daniel-quintero-castillo-4090a4399/)

[![Python](https://img.shields.io/badge/Python-RegEx-blue?style=for-the-badge&logo=python)](https://www.python.org/) [![Threat Hunting](https://img.shields.io/badge/Threat_Hunting-Parsing-darkgreen?style=for-the-badge)](https://www.cisa.gov/cybersecurity)

## 📌 Project Description
In this project, I utilized the `re` module in Python to efficiently extract highly specific data from raw security logs[cite: 17]. The primary objectives were isolating devices that required OS updates and parsing out valid IP addresses to compare them against a known threat list[cite: 17].

---

## 🔍 Phase 1: Pattern Recognition & Log Parsing
The lab required writing custom regex strings to filter unstructured string data.

*   **Device Identification:** Created a target pattern (`r15\w+`) to find all device IDs starting with "r15" followed by any alphanumeric sequence[cite: 17].
*   **IP Extraction (Basic):** Built an initial pattern (`\d\d\d\.\d\d\d\.\d\d\d\.\d\d\d`) to find IPv4 addresses with exactly three digits per segment[cite: 17].
*   **IP Extraction (Dynamic):** Upgraded the pattern using `+` to match segments of varying lengths, and finally refined it to `\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}` to strictly capture valid IPv4 formatting (1 to 3 digits per block)[cite: 17].
*   **Threat Matching:** Used `re.findall()` to generate a clean list of valid IP addresses, then wrote a `for` loop to check if any extracted IPs matched a `flagged_addresses` list, triggering an investigation alert if found[cite: 17].

## 📝 Phase 2: Key Takeaways
*   The `\w` symbol matches any alphanumeric character, while `\d` matches exclusively with digits (0-9)[cite: 17].
*   The `+` symbol matches one or more occurrences of the preceding character, whereas `{x,y}` strictly enforces an occurrence range between `x` and `y`[cite: 17].
*   The `re.findall()` function applies a regex pattern to a string and automatically returns a clean list containing all successful matches[cite: 17].
