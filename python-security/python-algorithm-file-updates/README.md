# Algorithm for file updates in Python

[![Location](https://img.shields.io/badge/Location-Medell%C3%ADn%2C_Colombia-success?style=for-the-badge&logo=google-maps)](https://www.google.com/maps/place/Medell%C3%ADn,+Antioquia,+Colombia/) [![Education](https://img.shields.io/badge/Degree-Mechatronics_Engineering-blue?style=for-the-badge&logo=prometric)](https://www.itm.edu.co/) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/daniel-quintero-castillo-4090a4399/)

[![Python](https://img.shields.io/badge/Python-Algorithms-blue?style=for-the-badge&logo=python)](https://www.python.org/) [![Access Control](https://img.shields.io/badge/Access_Control-Automation-darkgreen?style=for-the-badge)](https://www.cisa.gov/cybersecurity)

## 📌 Project description
As a security professional at a healthcare company, my task is to regularly update a file identifying employees who can access restricted patient records. Access is restricted based on their IP addresses. I developed an algorithm that checks whether an allow list of IP addresses contains any IPs identified on a separate remove list. If a match is found, the algorithm removes the unauthorized IP addresses and updates the original file containing the allow list.

---

## 🔍 Open the file that contains the allow list
To begin, I assigned the name of the target file to a variable and used the `with` statement alongside the `open()` function to handle the file securely. 

```python
import_file = "allow_list.txt"
with open(import_file, "r") as file:
```

## 📖 Read the file contents
While the file is open in read mode, I used the `.read()` method to extract its contents and convert them into a string format. This string is then stored in a variable for further processing.

```python
    ip_addresses = file.read()
```

## 🔄 Convert the string into a list
To remove individual IP addresses, the data must be in a list format rather than a single string. I applied the `.split()` method to the `ip_addresses` string to convert it into a list based on whitespace.

```python
ip_addresses = ip_addresses.split()
```

## 🔁 Iterate through the remove list
With the allow list structured properly, I set up a `for` loop to iterate through the `remove_list` (a predefined list containing all IP addresses that must be revoked). I used `element` as the loop variable.

```python
for element in remove_list:
```

## 🗑️ Remove IP addresses that are on the remove list
Inside the loop body, I created a conditional statement to evaluate if the current `element` exists in the `ip_addresses` list. If it does, the `.remove()` method is applied to delete that specific IP address. Applying the `.remove()` method in this way is possible and effective because there are no duplicate entries in the `ip_addresses` list.

```python
    if element in ip_addresses:
        ip_addresses.remove(element)
```

## 💾 Update the file with the revised list of IP addresses
Finally, the algorithm must update the original file. First, I converted the list back into a string using the `.join()` method, applying `"\n"` to separate each IP address on a new line. Then, I used another `with open()` statement with the `"w"` (write) parameter and the `.write()` method to overwrite the file with the revised list.

```python
ip_addresses = "\n".join(ip_addresses)
with open(import_file, "w") as file:
    file.write(ip_addresses)
```

---

## 📝 Summary
This project demonstrates the creation of an automated Python algorithm designed to manage identity and access control files. By utilizing the `with open()` statement, I safely accessed and modified sensitive security documents. I applied `.read()` and `.split()` to parse string data into manageable lists, and leveraged `for` loops combined with conditionals and the `.remove()` method to parse out unauthorized IP addresses. Finally, the `.join()` and `.write()` methods were used to successfully update the original file, establishing an efficient and repeatable process for maintaining network security.
