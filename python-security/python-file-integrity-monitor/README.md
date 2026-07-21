# File Integrity Monitor (FIM) using Hashing

[![Location](https://img.shields.io/badge/Location-Medell%C3%ADn%2C_Colombia-success?style=for-the-badge&logo=google-maps)](https://www.google.com/maps/place/Medell%C3%ADn,+Antioquia,+Colombia/) [![Education](https://img.shields.io/badge/Degree-Mechatronics_Engineering-blue?style=for-the-badge&logo=prometric)](https://www.itm.edu.co/) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/daniel-quintero-castillo-4090a4399/)

[![Python](https://img.shields.io/badge/Python-Cryptography-blue?style=for-the-badge&logo=python)](https://www.python.org/) [![Data Integrity](https://img.shields.io/badge/Data_Integrity-SHA256-darkgreen?style=for-the-badge)](https://csrc.nist.gov/glossary/term/integrity)

## 📌 Project Description
Data integrity is a core pillar of the CIA triad. Attackers often modify critical system files, inject malware, or alter logs to cover their tracks. This Python-based File Integrity Monitor (FIM) reads a target file, calculates its cryptographic SHA-256 hash, and compares it against a known baseline to detect unauthorized modifications.

---

## 🔍 Phase 1: Key Features & Libraries Used
*   **`hashlib` Module:** Implements a secure hash algorithm (SHA-256) to create a unique digital fingerprint of a file.
*   **Binary File Handling:** Uses `open(file, 'rb')` to read the file in binary mode, ensuring accurate hash calculations regardless of file type.
*   **State Comparison:** Evaluates current file states against historical baselines to alert administrators of potential tampering.

---

## 💻 Phase 2: Python Code Implementation
Below is the functional script demonstrating cryptographic hashing for security monitoring.

```python
import hashlib
import os

def calculate_sha256(filepath):
    """Calculates the SHA-256 hash of a given file."""
    sha256_hash = hashlib.sha256()
    try:
        # Read the file in binary mode in chunks to prevent memory overload
        with open(filepath, "rb") as file:
            for byte_block in iter(lambda: file.read(4096), b""):
                sha256_hash.update(byte_block)
        return sha256_hash.hexdigest()
    except FileNotFoundError:
        return None

def monitor_file(filepath, baseline_hash):
    """Compares the current file hash against the baseline."""
    print(f"Monitoring: {filepath}")
    current_hash = calculate_sha256(filepath)
    
    if current_hash is None:
        print("❌ ERROR: File not found or deleted.")
    elif current_hash == baseline_hash:
        print("✅ INTEGRITY VERIFIED: No unauthorized changes detected.")
    else:
        print("🚨 ALERT: File modification detected! Hash mismatch.")
        print(f"Baseline Hash: {baseline_hash}")
        print(f"Current Hash:  {current_hash}")

# Example Usage
target_file = "secure_config.txt"

# Simulate writing a baseline file
with open(target_file, "w") as f:
    f.write("StrictHostKeyChecking yes")

# 1. Calculate the initial baseline hash
baseline = calculate_sha256(target_file)
print(f"Baseline established: {baseline}\n")

# 2. Monitor the file (Should be verified)
monitor_file(target_file, baseline)

# 3. Simulate an attacker modifying the file
with open(target_file, "a") as f:
    f.write("\nPermitRootLogin yes")

print("\n--- After Unauthorized Modification ---")

# 4. Monitor the file again (Should trigger alert)
monitor_file(target_file, baseline)
```
