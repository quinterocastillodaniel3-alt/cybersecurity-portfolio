# 🌐 Network Traffic Analysis and Security

Repository dedicated to understanding network traffic, packet inspection, and anomaly detection using command-line tools.

---

## 📡 Network Traffic Fundamentals

Monitoring and understanding traffic is vital in cybersecurity because:
1. It helps identify deviations from expected traffic flows (establishing baselines).
2. It helps detect intrusions and tactics like **lateral movement** (when an attacker expands their unauthorized access by jumping from one host to another within the same network).

### TCP/IP Model and Encapsulation
* **Network Access Layer:** This is the bottom layer of the TCP/IP model, directly responsible for accepting and physically delivering packets across a network medium (whether copper wire, fiber optic, or Wi-Fi).
* **IPv4 Header Anatomy:** A network packet is like a letter; the header is the "envelope" and contains crucial routing information:
  * **IP Addresses:** Identify the source and destination.
  * **Protocols:** Uses a numerical value to represent a specific standard (e.g., the number 6 represents TCP and 17 represents UDP).
  * **Ports:** Indicate the destination logical application or service.
  * **Time to Live (TTL):** A field that determines how long (number of router hops) a packet can travel before being discarded to prevent infinite loops.
  * *Security Note:* The **payload** data, which is the actual message, is **not** part of the header.

---

## 🛠️ Packet Capture and Analysis

Packet capture files (commonly with a `.pcap` extension) provide detailed and complete snapshots of network communications intercepted from an interface. 

Network protocol analyzer tools are available to be used in two main modes:
* **Graphical User Interface (GUI):** Such as Wireshark.
* **Command Line Interface (CLI):** Such as `tcpdump` or `tshark`.

### Using tcpdump
To get verbose output with detailed information about packets listening on all interfaces, the correct command syntax in Linux is:

```bash
sudo tcpdump -i any -v
```
*(Note: The `-i` flag must always be followed by the interface, in this case `any`, and `-v` enables verbose mode).*

**Reading tcpdump logs:**
When examining the following output:
```text
22:00:19.538395 IP 198.168.105.1.41012 > 198.111.123.1.61012: Flags [P.]
```
The source IP address is **198.168.105.1**. In standard nomenclature, the structure always shows `Source > Destination`, separating the IP from the port with a dot.

---

## 🐍 Bonus: Basic Automation with Python and Scapy

For mass analysis of capture files, security analysts often create scripts. Below is a basic example using Python's `Scapy` library to extract and list the source and destination IP addresses from a `.pcap` file:

```python
from scapy.all import rdpcap, IP

def analyze_pcap(file_path):
    # Load the network capture file
    packets = rdpcap(file_path)
    
    print(f"Analyzing: {file_path}\n{'-'*30}")
    
    # Iterate over the packets and print Source -> Destination
    for packet in packets:
        if IP in packet:
            src_ip = packet[IP].src
            dst_ip = packet[IP].dst
            print(f"Traffic detected: {src_ip} -> {dst_ip}")

# Usage example:
# analyze_pcap("incident_capture.pcap")
```
