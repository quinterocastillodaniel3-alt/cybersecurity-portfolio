# Importing and Parsing Security Log Files

[![Location](https://img.shields.io/badge/Location-Medell%C3%ADn%2C_Colombia-success?style=for-the-badge&logo=google-maps)](https://www.google.com/maps/place/Medell%C3%ADn,+Antioquia,+Colombia/) [![Education](https://img.shields.io/badge/Degree-Mechatronics_Engineering-blue?style=for-the-badge&logo=prometric)](https://www.itm.edu.co/) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/daniel-quintero-castillo-4090a4399/)

[![Python](https://img.shields.io/badge/Python-File_Handling-blue?style=for-the-badge&logo=python)](https://www.python.org/) [![Log Analysis](https://img.shields.io/badge/Log_Analysis-Parsing-darkgreen?style=for-the-badge)](https://www.cisa.gov/cybersecurity)

## 📌 Project Description
Acting as a security analyst, I practiced using functions and syntax in Python to import and parse security log text files[cite: 15]. The primary goal was to prepare a security log file for analysis and create a separate text file containing IP addresses that are allowed to access restricted information[cite: 15].

---

## 🔍 Phase 1: File Operations & Parsing
The lab tasks focused on securely opening text files, extracting string data, and writing modified content back into the file system.

*   **Reading Files:** Utilized the `with open()` statement alongside the `"r"` parameter to read the contents of a security log[cite: 15]. Applied the `.read()` method to convert and store the entire imported log file as a single string variable[cite: 15].
*   **Parsing Data:** Used the `.split()` method on the string to convert the imported text into a list of strings, splitting the data line by line based on whitespace[cite: 15]. 
*   **Appending Logs:** Opened the log file using the `"a"` parameter to indicate the file was being opened for appending purposes[cite: 15]. Applied the `.write()` method to append a missing entry securely to the end of the log file[cite: 15].
*   **Writing New Files:** Created a new text file named `allow_list.txt` by opening it with the `"w"` parameter[cite: 15]. Used the `.write()` method to inject a string of approved IP addresses into the new text file for the security team[cite: 15].

---

## 📝 Phase 2: Key Takeaways
*   The `with` statement allows analysts to efficiently handle files by automatically closing them after reading or writing[cite: 15].
*   The `open()` function takes the name of the file as the first parameter and a string indicating the purpose of opening the file as the second parameter[cite: 15].
*   Specific string parameters dictate file handling behavior: `"r"` is used for reading, `"a"` is used for appending, and `"w"` is used for writing[cite: 15].
*   The `.read()` method allows you to read in a file, while the `.write()` method allows you to append or write to a file[cite: 15].
*   The `.split()` method allows you to convert a string into a list, separating elements by whitespace if no specific character is designated[cite: 15].
