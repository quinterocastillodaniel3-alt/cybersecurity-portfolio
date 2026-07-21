# 🗃️ Python Data Extraction and Manipulation

This repository outlines essential Python techniques for manipulating data structures (Strings and Lists) and extracting specific information using indexing, slicing, and regular expressions. 

These skills are fundamental for tasks such as log parsing, data normalization, and developing custom cybersecurity algorithms.

---

## ⚙️ Core Concepts and Algorithms

In programming, an **algorithm** is a logical sequence of steps designed to solve a specific problem. For example, deciding to use string slicing and a `for` loop to extract specific data from a list of logs constitutes creating an algorithm.

### Essential Built-in Functions
*   **`len()`**: Returns the total number of items in an object.
    *   *Example:* `print(len("125"))` returns `3` because the string contains exactly three characters.

---

## 🔤 String Manipulation and Slicing

Strings are immutable sequences of characters. You can search, modify their output, and extract specific parts using indices.

### String Methods
*   **`.lower()`**: Returns a copy of the string converted entirely to lowercase. Useful for standardizing case-sensitive data (e.g., standardizing `"HG91AB2".lower()` to `"hg91ab2"`).
*   **`.index()`**: Finds the first occurrence of a specified value and returns its exact position (starting at index 0). 
    *   *Example:* In the string `"encryption"`, the character `"c"` is located at index `2`.

### Bracket Notation (Slicing)
Slicing allows you to extract a specific portion of a string using the syntax `[start_index:stop_index]`. 
*   The `start_index` is **included**.
*   The `stop_index` is **excluded**.

**Practical Example: Extracting an Employee ID Segment**
```python
employee_id = "w237x430y567"

# Extract characters at indices 3, 4, 5, and 6
segment = employee_id[3:7] 

print(segment)
# Output: "7x43"
```

---

## 📋 List Operations

Lists are mutable data structures used to store collections of items.

### List Methods
*   **`.append()`**: Adds a single new entry to the very end of a list.

### List Concatenation
You can merge two entirely separate lists into a new one using the addition (`+`) operator.
```python
new_users = ["user1", "user2"]
approved_users = ["admin", "guest"]

# Joining both lists into a single variable
users = new_users + approved_users

print(users)
# Output: ['user1', 'user2', 'admin', 'guest']
```

---

## 🔍 Regex for Information Extraction

Regular Expressions (Regex) provide advanced pattern matching to locate specific data within complex strings.

*   **`re.findall(pattern, string)`**: Scans the given string and returns a **list** of all non-overlapping matches that fit the regular expression pattern.
*   **`\w` (Word Character)**: A critical regex metacharacter that matches **any alphanumeric character** (letters `a-z`, `A-Z`, numbers `0-9`) as well as the underscore (`_`).
