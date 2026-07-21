# 🪲 Python Debugging and Log Parsing

This repository serves as a guide for identifying and resolving code errors (debugging) and transforming raw security data into readable formats (parsing). These skills are essential for maintaining reliable automation scripts in a Security Operations Center (SOC).

---

## 🛠️ Debugging Python Code

**Debugging** is the practice of identifying, analyzing, and fixing errors in your code. When automating security tasks, ensuring your code runs exactly as intended is critical.

### Types of Errors

1.  **Syntax Errors:** 
    Occur when the code violates the grammatical rules of the Python language. The script will not run until these are fixed.
    *   *Common Causes:* Missing colons (`:`) at the end of `if` or `for` statements, unclosed strings (missing a closing `"`), or using the wrong keywords (e.g., using `elsif` instead of `elif`).
    *   *Example:* `device_id = "p35rv47` (Missing closing quote).

2.  **Exceptions (Runtime Errors):** 
    Occur when the syntax is correct, but the program encounters an impossible operation during execution, causing it to crash.
    *   *Common Causes:* Accessing a list index that does not exist (`IndexError`), dividing by zero, or trying to open a file that is not there.
    *   *Example:* Calling `username_list[10]` when the list only contains 5 elements.

3.  **Logic Errors:** 
    The most difficult errors to catch. The code runs perfectly without crashing, but it produces the *wrong result*.
    *   *Common Causes:* Flawed mathematical logic, incorrect variable assignments, or passing strings instead of variables.
    *   *Example:* Calling a function with a string literal `welcome_user("first_name")` instead of the variable `welcome_user(first_name)`. Another example is a routing script that accidentally sends Priority 2 tickets to Team A instead of Team B.

### Debugging Strategies
*   **Print Statements:** Using `print()` strategically throughout your code is one of the most effective ways to debug. It helps you identify exactly which sections of the code are functioning correctly and inspect the values of variables at specific points in time.

---

## 📊 Data Parsing and Automation

**Parsing** is the process of converting raw data into a more readable or structured format. In cybersecurity, this usually involves taking massive, unstructured text logs and breaking them down into actionable pieces (like lists of IP addresses or usernames).

### Parsing Workflow Example
To automate the detection of unusual login activity from a raw log file, a standard Python workflow includes:

1.  **Reading the File:** Use a `with open("logs.txt", "r") as file:` statement to open the log file safely, and `.read()` to store its contents as a string variable.
2.  **Splitting the Data (Parsing):** Use the `.split()` method to break the massive string into a Python list (e.g., separating a string of 50 usernames into a list of 50 individual items).
3.  **Iteration:** Use a `for` loop to iterate through every single item in the newly created list.
4.  **Conditionals:** Use an `if` statement inside the loop to check each item against security criteria (e.g., checking if the log entry indicates a failed login attempt or an unusual timestamp).

**Code Snippet:**
```python
# 1. Read the file
with open("auth_logs.txt", "r") as file:
    log_data = file.read()

# 2. Parse the data into a list
login_list = log_data.split()

# 3 & 4. Iterate and evaluate
failed_logins = []
for login in login_list:
    if "failed" in login.lower():
        failed_logins.append(login)
```
