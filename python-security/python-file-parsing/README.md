# Importing and Parsing Security Log Files

[![Location](https://img.shields.io/badge/Location-Medell%C3%ADn%2C_Colombia-success?style=for-the-badge&logo=google-maps)](https://www.google.com/maps/place/Medell%C3%ADn,+Antioquia,+Colombia/) [![Education](https://img.shields.io/badge/Degree-Mechatronics_Engineering-blue?style=for-the-badge&logo=prometric)](https://www.itm.edu.co/) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/daniel-quintero-castillo-4090a4399/)

[![Python](https://img.shields.io/badge/Python-File_Handling-blue?style=for-the-badge&logo=python)](https://www.python.org/) [![Log Analysis](https://img.shields.io/badge/Log_Analysis-Parsing-darkgreen?style=for-the-badge)](https://www.cisa.gov/cybersecurity)

## 📌 Project Description
Acting as a security analyst, I imported and parsed security log text files using Python[cite: 13]. The primary goal was to prepare logs for analysis and create a separate text file documenting IP addresses allowed to access restricted network information[cite: 13].

---

## 🔍 Phase 1: File Operations & Parsing
The lab tasks focused on securely opening text files, extracting string data, and writing modified content back into the file system.

*   **Reading Files:** Utilized the `with open()` statement alongside the `"r"` parameter to read the contents of a security log and automatically close the file after accessing it[cite: 13]. Applied the `.read()` method to convert and store the entire log file as a single string variable[cite: 13].
*   **Parsing Data:** Used the `.split()` method on the string to convert the imported text into a list of strings[cite: 13]. This method successfully parsed the data line by line by relying on whitespace as the default separator[cite: 13].
*   **Appending Logs:** Opened the log file using the `"a"` parameter and applied the `.write()` method to append a missing `missing_entry` log securely to the end of the file[cite: 13].
*   **Writing New Files:** Created a new text file named `allow_list.txt` by opening it with the `"w"` parameter, and then used the `.write()` method to inject a list of approved IP addresses into it for the security team[cite: 13].

## 📝 Phase 2: Key Takeaways
*   The `with` statement allows analysts to efficiently handle files by automatically closing them after executing the nested code block[cite: 13].
*   The `open()` function imports a file and takes the file name as the first parameter, followed by a string indicating its purpose as the second parameter[cite: 13].
*   Specific parameters dictate file handling behavior: `"r"` is used for reading, `"a"` is used for appending, and `"w"` is used for writing or overwriting files[cite: 13].
*   The `.read()` method reads in a file as a string, while the `.write()` method allows data to be written or appended to the file[cite: 13].
*   The `.split()` method in Python allows you to convert a string into a list, defaulting to splitting on whitespace if no specific character is designated[cite: 13].
