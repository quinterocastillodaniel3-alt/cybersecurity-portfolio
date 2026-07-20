# 🐍 Python for Cybersecurity: Automation Basics

This repository serves as a foundational guide for utilizing Python to script security tasks, manage data, and reduce manual effort in cybersecurity operations.

---

## ⚙️ The Role of Python in SecOps

Python is the industry standard for cybersecurity scripting. By writing code to perform repetitive tasks—such as dynamically managing an Access Control List (ACL) or extracting IPs from a massive log file—security analysts achieve **automation**, drastically reducing manual effort and minimizing human error.

---

## 🧱 Basic Syntax and Data Types

Python relies on clean syntax and specific data structures to function properly.

### Data Types
* **Strings:** Text data. Strings must always be enclosed in quotes (`" "`).
  * *Example:* `username = "dtanaka"`
* **Booleans:** Logical values representing `True` or `False`.
  * *Example:* The evaluation `print(10 < 100)` generates a Boolean value of `True`.
* **Lists:** A collection of items. The `type()` function is used to identify the data structure.
  * *Example:* `var2 = ["a","b","c"]` evaluated with `type(var2)` will indicate it contains list data.

---

## 🔀 Control Flow: Conditionals

Conditional statements allow scripts to make decisions based on data. 

**Key Syntax Rules for `if` statements:**
1. The conditional header must always end with a colon (`:`).
2. The code block executing inside the condition **must be indented**.
3. To evaluate equality, use the double equal sign (`==`). Do not use the assignment operator (`=`) or the inequality operator (`!=`) when checking for an exact match.

**Correct Conditional Syntax Example:**
```python
update_status = "incomplete"

if update_status == "incomplete":
    print("schedule update")
```

**Using `else` for alternative outcomes:**
```python
operating_system = "OS 3"

if operating_system == "OS 3":
    print("Updates needed")
else:
    print("No updates needed")
```

---

## 🔄 Iteration: Loops

Loops are used to execute a block of code multiple times. Like conditionals, the code block inside a loop **must be indented**.

### 1. `for` Loops
Used for iterating over a sequence (like a list or a range). 
*Note:* The `range(start, stop)` function includes the start number but excludes the stop number.

**Example: Printing numbers 1, 2, and 3:**
```python
for i in range(1, 4):
    print(i)
```

**Example: Iterating through a list:**
```python
failed_login = ["user1", "admin", "guest"]

for username in failed_login:
    print(username)
```

### 2. `while` Loops
Used to execute a block of code as long as a specified condition remains `True`.

**Example: Loop execution tracking:**
```python
count = 1
while count < 5:
    print("warning")
    count = count + 1
```
*Result:* This loop will print "warning" exactly **4 times** (when count is 1, 2, 3, and 4). Once count reaches 5, the condition `5 < 5` becomes `False` and the loop terminates.
