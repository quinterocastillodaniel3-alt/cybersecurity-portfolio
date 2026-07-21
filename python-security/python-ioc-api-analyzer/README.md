# Automated Threat Intelligence API Analyzer

[![Location](https://img.shields.io/badge/Location-Medell%C3%ADn%2C_Colombia-success?style=for-the-badge&logo=google-maps)](https://www.google.com/maps/place/Medell%C3%ADn,+Antioquia,+Colombia/) [![Education](https://img.shields.io/badge/Degree-Mechatronics_Engineering-blue?style=for-the-badge&logo=prometric)](https://www.itm.edu.co/) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/daniel-quintero-castillo-4090a4399/)

[![Python](https://img.shields.io/badge/Python-API_Integration-blue?style=for-the-badge&logo=python)](https://www.python.org/) [![Threat Intel](https://img.shields.io/badge/Threat_Intel-VirusTotal-darkgreen?style=for-the-badge)](https://www.virustotal.com/)

## 📌 Project Description
In a real-world Security Operations Center (SOC), manually investigating extracted IP addresses is highly inefficient. This project automates the threat hunting process by taking a list of suspicious IP addresses and programmatically querying a Threat Intelligence API (like VirusTotal) to determine if they are malicious.

---

## 🔍 Phase 1: Key Features & Libraries Used
*   **`requests` Module:** Used to send HTTP GET requests to external APIs securely.
*   **JSON Parsing:** Extracts and parses structured JSON data returned by the API to isolate the specific malicious score of an Indicator of Compromise (IoC).
*   **Automation:** Iterates through a list of IP addresses, automating the triage process and outputting actionable alerts for security teams.

---

## 💻 Phase 2: Python Code Implementation
Below is the functional script demonstrating API interaction and JSON data handling.

```python
import requests
import json

# List of suspicious IP addresses extracted from a log file
suspicious_ips = ["192.168.1.1", "8.8.8.8", "185.153.196.50"]

# Replace 'YOUR_API_KEY' with a valid VirusTotal API Key
API_KEY = "YOUR_API_KEY"
HEADERS = {"x-apikey": API_KEY}

def analyze_ips(ip_list):
    print("Starting automated threat intelligence scan...\n")
    for ip in ip_list:
        url = f"[https://www.virustotal.com/api/v3/ip_addresses/](https://www.virustotal.com/api/v3/ip_addresses/){ip}"
        try:
            response = requests.get(url, headers=HEADERS)
            if response.status_code == 200:
                data = response.json()
                # Parse the JSON response to find the malicious vote count
                malicious_votes = data['data']['attributes']['last_analysis_stats']['malicious']
                
                if malicious_votes > 0:
                    print(f"🚨 ALERT: {ip} is flagged as MALICIOUS by {malicious_votes} security vendors.")
                else:
                    print(f"✅ CLEAR: {ip} appears to be clean.")
            else:
                print(f"⚠️ ERROR: Could not retrieve data for {ip}. Status Code: {response.status_code}")
        except Exception as e:
            print(f"Connection error regarding {ip}: {e}")

# Call the function
analyze_ips(suspicious_ips)
```
