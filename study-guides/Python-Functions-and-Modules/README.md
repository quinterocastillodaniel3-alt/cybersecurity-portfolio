# 🐍 Python Functions, Modules, and Best Practices

This repository serves as a reference guide for structuring Python code efficiently. It covers the creation of reusable code blocks, the use of external libraries, and adherence to industry-standard styling guidelines.

---

## 🛠️ Functions

A **function** is a reusable section of code designed to perform a specific task. Using functions prevents code duplication and makes scripts easier to troubleshoot.

### Built-in Functions
Python comes with several pre-defined functions that are always available:
* `max()`: Returns the largest item in an iterable or the largest of two or more arguments. For example, `print(max(1, 3, 7))` outputs `7`.
* `type()`: Returns the data type of the given object. Proper syntax requires parentheses, e.g., `type([55, 81, 17])` evaluates a list.

### User-Defined Functions
To create your own function, you must use the **`def`** keyword followed by the function name.

**Example: A basic subtraction function**
```python
# 'num' is the parameter (the variable in the definition)
def subtract(num):
    total = 100 - num
    return total

# '9' is the argument (the actual data passed into the function)
result = subtract(9)
print(result) # Outputs: 91
```

---

## 📦 Modules and Libraries

To expand Python's capabilities beyond built-in functions, we use modules and libraries.

* **Module:** A simple Python file (ending in `.py`) that contains additional functions, variables, classes, and any type of executable code.
* **Library:** A collection of modules that provide pre-written code users can access and incorporate into their programs.

### The Python Standard Library vs. Third-Party Libraries
* **Standard Library:** Comes pre-installed with Python. It includes modules like:
  * `time` (for time-related tasks)
  * `re` (for Regular Expressions)
  * `csv` (for reading and writing CSV files)
* **Third-Party Libraries:** Must be installed separately (usually via `pip`). A prime example is **NumPy**, which is widely used for data analysis and numerical computing but is *not* part of the standard library.

---

## 📝 Code Style and PEP 8

Writing code that works is only half the job; writing code that is readable is equally important. **PEP 8** is the official style guide for Python code.

### Why use a Style Guide?
1. It makes your code more **consistent**.
2. It makes it **easier for other programmers to understand** and collaborate on your code.

### Indentation Rules
Unlike other languages that use brackets `{}` to define code blocks, Python uses indentation (spaces). Proper indentation is mandatory.
```python
# Correct Indentation Example
if username == "elarson":
    print("Welcome, elarson!")
```

### Best Practices for Comments
Comments explain the "why" behind the code. When writing comments, always ensure you:
* **Make them clear:** Avoid ambiguous explanations.
* **Keep them up to date:** Outdated comments are worse than no comments at all, as they can mislead other developers.
