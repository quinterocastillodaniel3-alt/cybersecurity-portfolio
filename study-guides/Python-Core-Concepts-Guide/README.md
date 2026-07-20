# 🐍 Python Core Concepts: Functions, Imports, and Comments

This repository serves as a reference guide for Python concepts from Module 2 of the Google Cybersecurity Certificate.

---

## 🛠️ User-Defined Functions

The following keywords are used when creating user-defined functions:

*   **`def`**: Placed before a function name to define a function.
    *   Example: `def greet_employee():` defines the `greet_employee()` function.
    *   Example with parameters: `def calculate_fails(total_attempts, failed_attempts):` defines a function that includes the two parameters of `total_attempts` and `failed_attempts`.
*   **`return`**: Used to return information from a function. When Python encounters this keyword, it exits the function after returning the information.
    ```python
    def calculate_fails(total_attempts, failed_attempts):
        fail_percentage = failed_attempts / total_attempts
        return fail_percentage # Returns the value of the fail_percentage variable
    ```

---

## 🧮 Built-in Functions

The following built-in functions are commonly used in Python:

*   **`max()`**: Returns the largest numeric input passed into it. For example, `print(max(10, 15, 5))` returns `15` and outputs this value to the screen.
*   **`min()`**: Returns the smallest numeric input passed into it. For example, `print(min(10, 15, 5))` returns `5` and outputs this value to the screen.
*   **`sorted()`**: Sorts the components of a list (or other iterable).
    *   Numeric sort example: `print(sorted([10, 15, 5]))` sorts the elements of the list from smallest to largest and outputs the sorted list of `[5, 10, 15]` to the screen.
    *   Alphabetical sort example: `print(sorted(["bmoreno", "tshah", "elarson"]))` sorts the elements in the list in alphabetical order and outputs the sorted list of `["bmoreno", "elarson", "tshah"]` to the screen.

---

## 📦 Importing Modules and Libraries

The `import` keyword is used to import a module from the Python Standard Library or to import an external library that has already been installed. It searches for a module or library in a system and adds it to the local Python environment.

**Import Syntax Examples:**
*   `import statistics`: Imports the `statistics` module and all of its functions from the Python Standard Library.
*   `from statistics import mean`: Imports the `mean()` function of the `statistics` module from the Python Standard Library.
*   `from statistics import mean, median`: Imports the `mean()` and `median()` functions of the `statistics` module from the Python Standard Library.

---

## 📝 Comments

A comment is a note programmers make about the intention behind their code. 

*   **Single-line comments (`#`)**: Starts a line that contains a Python comment. For example, `# Print approved usernames` contains a comment that indicates the purpose of the code that follows it is to print approved usernames.
*   **Documentation strings (`"""`)**: Starts and ends a multi-line string that is often used as a Python comment. Multi-line comments are used when you need more than 79 characters in a single comment.
