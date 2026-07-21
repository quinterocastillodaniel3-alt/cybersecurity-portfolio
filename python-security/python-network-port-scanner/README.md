# Custom Network Port Scanner

[![Location](https://img.shields.io/badge/Location-Medell%C3%ADn%2C_Colombia-success?style=for-the-badge&logo=google-maps)](https://www.google.com/maps/place/Medell%C3%ADn,+Antioquia,+Colombia/) [![Education](https://img.shields.io/badge/Degree-Mechatronics_Engineering-blue?style=for-the-badge&logo=prometric)](https://www.itm.edu.co/) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/daniel-quintero-castillo-4090a4399/)

[![Python](https://img.shields.io/badge/Python-Networking-blue?style=for-the-badge&logo=python)](https://www.python.org/) [![Vulnerability Management](https://img.shields.io/badge/Vulnerability_Scanning-Reconnaissance-darkgreen?style=for-the-badge)](https://www.cisa.gov/cybersecurity)

## 📌 Project Description
Reconnaissance is the first step in both offensive and defensive cybersecurity operations. Identifying open ports on a server is critical to discovering exposed services and potential vulnerabilities. This custom Python script acts as a lightweight port scanner to audit specific network endpoints.

---

## 🔍 Phase 1: Key Features & Libraries Used
*   **`socket` Module:** Provides low-level network interface access, enabling Python to establish TCP connections over IPv4.
*   **Timeout Handling:** Implements `settimeout()` to prevent the script from hanging on firewalled or unresponsive ports, ensuring rapid execution.
*   **Error Handling:** Uses `connect_ex()` instead of `connect()`, which returns an error indicator (0 for success) rather than raising exceptions, making the scanner much more efficient and stable.

---

## 💻 Phase 2: Python Code Implementation
Below is the functional script demonstrating network interactions and TCP connection attempts.

```python
import socket
import sys
from datetime import datetime

# Define target IP and the common ports to scan
# (e.g., 21=FTP, 22=SSH, 80=HTTP, 443=HTTPS, 3389=RDP)
target_ip = "127.0.0.1" # Using localhost for safe testing
ports_to_scan = [21, 22, 80, 443, 3389]

def scan_ports(target, ports):
    print("-" * 50)
    print(f"Scanning Target: {target}")
    print(f"Time started: {datetime.now()}")
    print("-" * 50)
    
    try:
        for port in ports:
            # Create an IPv4 (AF_INET) and TCP (SOCK_STREAM) socket
            s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            # Set a 1-second timeout so the script doesn't hang on filtered ports
            socket.setdefaulttimeout(1)
            
            # connect_ex returns 0 if the connection was successful
            result = s.connect_ex((target, port))
            if result == 0:
                print(f"🔓 Port {port}: OPEN")
            else:
                print(f"🔒 Port {port}: Closed or Filtered")
            
            s.close()
            
    except KeyboardInterrupt:
        print("\nExiting program.")
        sys.exit()
    except socket.gaierror:
        print("Hostname could not be resolved.")
        sys.exit()
    except socket.error:
        print("Could not connect to the server.")
        sys.exit()
        
    print("-" * 50)
    print("Scan completed.")

# Execute the scanner
scan_ports(target_ip, ports_to_scan)
```
