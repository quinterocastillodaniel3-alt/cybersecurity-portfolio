# 🐍 Python Core Concepts: Strings, Lists, and Advanced Regex

This repository serves as a reference guide for Python concepts from Module 3 of the Google Cybersecurity Certificate, focusing on data manipulation and advanced pattern matching.

---

## 🛠️ Built-in Functions

The following built-in functions are commonly used to evaluate or convert data in Python.

*   **`str()`**: Converts the input object to a string. 
    *   *Example:* `str(10)` converts the integer `10` to the string `"10"`.
*   **`len()`**: Returns the number of elements in an object.
    *   *Example:* `print(len("security"))` returns and displays `8`, the number of characters in the string.

---

## 🔤 String Methods

The following methods can be applied directly to strings to modify or search their contents.

*   **`.upper()`**: Returns a copy of the string in all uppercase letters.
    *   *Example:* `print("Security".upper())` outputs `"SECURITY"`.
*   **`.lower()`**: Returns a copy of the string in all lowercase letters.
    *   *Example:* `print("Security".lower())` outputs `"security"`.
*   **`.index()`**: Finds the first occurrence of the input in a string and returns its location.
    *   *Example:* `print("Security".index("c"))` finds `"c"` and returns its index of `2`.

---

## 📋 List Methods

The following methods are used to modify or search through lists.

*   **`.insert()`**: Adds an element in a specific position inside the list.
    *   *Example:* `username_list.insert(2, "wjaffrey")` adds `"wjaffrey"` at index 2.
*   **`.remove()`**: Removes the first occurrence of a specific element inside a list.
    *   *Example:* `username_list.remove("elarson")` removes `"elarson"` from the list.
*   **`.append()`**: Adds input to the end of a list.
    *   *Example:* `username_list.append("btang")` adds `"btang"` to the very end of the list.
*   **`.index()`**: Finds the first occurrence of an element in a list and returns its index.
    *   *Example:* `print(username_list.index("tshah"))` returns the index position of `"tshah"`.

---

## ➕ Additional Syntax for Strings and Lists

*   **`+` (Concatenation):** Combines two strings or lists together.
    *   *String Example:* `"IT" + "nwp12"` results in `"ITnwp12"`.
    *   *List Example:* `["elarson"] + ["tshah"]` results in `["elarson", "tshah"]`.
*   **`[]` (Bracket Notation):** Uses indices to extract specific parts (slices) of a string or list.
    *   *Single Index:* `print("h32rb17"[0])` extracts `"h"`.
    *   *Slicing:* `print("h32rb17"[0:3])` extracts `"h32"`. The first index (`0`) is included, but the second index (`3`) is excluded.

---

## 🔍 Advanced Regular Expressions

The `re` module and the following regular expression symbols are critical when searching for complex patterns in strings.

### Core Function
*   **`re.findall()`**: Returns a list of matches to a regular expression.
    *   *Example:* `re.findall("a53", "a53-32c.E")` returns `["a53"]`.

### Metacharacters and Symbols
*   **`\w`**: Matches any alphanumeric character (and the underscore).
*   **`.`**: Matches ALL characters, including symbols and spaces.
*   **`\d`**: Matches all single digits.
*   **`\s`**: Matches all single spaces.
*   **`\.`**: Matches the literal period character (escaped).
*   **`+`**: Represents **one or more** occurrences of a specific character.
    *   *Example:* `re.findall("\w+", "a53-32c.E")` returns `["a53", "32c", "E"]`.
*   **`*`**: Represents **zero, one, or more** occurrences of a specific character.
*   **`{}`**: Represents a specified number of occurrences of a specific character. The exact number is specified within the curly brackets.
    *   *Example:* `re.findall("\w{3}", "a53-32c.E")` matches exactly three alphanumeric characters, returning `["a53", "32c"]`.
