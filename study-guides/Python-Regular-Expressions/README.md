# 🔍 Python Regular Expressions (Regex) for Security

This repository serves as a technical guide for using Regular Expressions (Regex) in Python. In cybersecurity and Security Operations Centers (SOC), Regex is an essential skill for log parsing, data validation, and extracting specific indicators of compromise (IoCs) from massive datasets.

---

## 📦 The `re` Module

Python includes a built-in module for handling regular expressions. Since it is part of the Python Standard Library, it does not require external installation. 

To use it, you must import it at the beginning of your script:
```python
import re
```

---

## 🔣 Common Regex Metacharacters

Metacharacters are the building blocks of regular expressions, allowing you to define dynamic search patterns rather than exact, static strings.

*   **`\w` (Word Character):** Matches any alphanumeric character (letters `a-z`, `A-Z`, numbers `0-9`, and underscores `_`). 
    *   *Matches:* `"FirstName"`, `"3"`, `"user_123"`
    *   *Does NOT match:* `"#name"`, `" "`, `"@admin"`
*   **`\d` (Digit):** Matches any decimal digit (from `0` to `9`).
*   **`+` (One or more):** Matches **one or more** occurrences of the preceding character or group. It ensures that the sequence is not empty.
*   **`*` (Zero or more):** Matches **zero or more** occurrences of the preceding character or group.

---

## 🛠️ Core Functions: `re.findall()`

The most common function used for data extraction is `findall()`. It scans a string from left to right and returns all non-overlapping matches in the form of a list.

**Syntax:**
```python
re.findall(pattern, text)
```
*   `pattern`: The regular expression you want to search for.
*   `text`: The variable containing the string you are searching through.

---

## 🛡️ Practical Application: Parsing Employee IDs

**Scenario:** As a Security Analyst, you need to extract specific employee IDs from a raw log file. The target IDs consist of a mix of numbers and letters, have a minimum length of four characters, and always end with the exact sequence `"a6v"`.

**Solution:** Using the pattern `\w+a6v` ensures that there is at least one alphanumeric character (`\w+`) preceding the required ending, satisfying the minimum length requirement.

**Python Implementation:**
```python
import re

# Raw log data containing various IDs
log_data = "User logged in with ID: admina6v. Failed attempt by user x9a6v. Invalid user #a6v."

# Define the regex pattern
pattern = "\w+a6v"

# Extract matching IDs
matched_ids = re.findall(pattern, log_data)

print(matched_ids)
# Output: ['admina6v', 'x9a6v']
# Note: '#a6v' is excluded because '#' is not a valid word character (\w).
```
