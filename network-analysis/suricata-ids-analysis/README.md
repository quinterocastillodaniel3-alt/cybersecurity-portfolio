# Intrusion Detection and Log Analysis with Suricata

![Network Security](https://img.shields.io/badge/Network_Security-IDS-blue?style=for-the-badge)
![Suricata](https://img.shields.io/badge/Tool-Suricata-red?style=for-the-badge)
![JSON Parsing](https://img.shields.io/badge/JSON_Parsing-jq-darkgreen?style=for-the-badge)

## 📌 Project Description
In this scenario, I acted as a security analyst responsible for monitoring network traffic[cite: 1]. The objective was to configure Suricata, an open-source intrusion detection system (IDS), intrusion prevention system (IPS), and network analysis tool, to trigger alerts[cite: 1]. I analyzed packet captures (`sample.pcap`), examined custom rule signatures, and parsed the resulting log files (`fast.log` and `eve.json`) to understand network telemetry and alert generation[cite: 1].

---

## ⚙️ Suricata Rule Anatomy
A Suricata rule (or signature) consists of three main components: an action, a header, and rule options[cite: 1]. 

* **Action:** This determines what happens if all conditions are met[cite: 1]. 
  * Common actions differ among systems but generally include `alert`, `drop`, `pass`, and `reject`[cite: 1]. 
  * The `alert` action inspects traffic and sends an alert upon a match[cite: 1]. 
  * The `drop` action deletes the traffic, but this only occurs when Suricata runs in IPS mode[cite: 1].
* **Header:** This defines the network traffic attributes, including protocols, source/destination IPs, ports, and traffic direction[cite: 1]. 
  * For example, the header `http $HOME_NET any ->$EXTERNAL_NET any` applies specifically to HTTP traffic moving from an internal network to an external one[cite: 1]. 
  * The `$HOME_NET` variable was explicitly defined as the `172.21.224.0/20` subnet to identify the organization's systems[cite: 1].
* **Rule Options:** These are enclosed in parentheses and separated by semicolons, allowing for precise traffic filtering[cite: 1]. 
  * The `msg` option provides the specific text for the alert, such as "GET on wire"[cite: 1]. 
  * The `content` option instructs Suricata to search for specific strings, like the word "GET" within the HTTP method[cite: 1]. 
  * The `sid` represents a unique numeric signature ID that identifies the rule[cite: 1].
  * The `rev` option indicates the revision version of the signature[cite: 1].

---

## 🚀 Execution & Traffic Analysis
To process the network traffic, I executed Suricata using the following command[cite: 1]:

`sudo suricata -r sample.pcap -S custom.rules -k none`[cite: 1]

* **Command Breakdown:** 
  * The `-r` option specified the input file (`sample.pcap`) to mimic live network traffic[cite: 1]. 
  * The `-S` option instructed Suricata to use the custom signatures defined in the `custom.rules` file[cite: 1]. 
  * The `-k none` option disabled checksum checks, as the integrity of the sample capture file did not need to be verified during this simulation[cite: 1].

---

## 📊 Log Analysis & Event Correlation
After executing the rules against the packet capture, Suricata generated output logs in the `/var/log/suricata` directory[cite: 1].

### 1. The `fast.log` File
* Each line in this file corresponds to a specific alert generated when a packet meets the conditions of a rule[cite: 1]. 
* While this format is considered deprecated and not recommended for deep incident response, it is highly useful for quick checks and quality assurance testing[cite: 1].

### 2. The `eve.json` File
* This is the main, standard log file for Suricata events[cite: 1]. 
* It contains highly detailed information about triggered alerts and network telemetry stored in JSON format[cite: 1]. 
* To parse this complex data efficiently, I utilized the `jq` command-line tool to extract specific fields and improve readability[cite: 1].

**Key Findings from `eve.json` Extraction:**
* The severity property for the first triggered alert had a value of 3[cite: 1].
* The alert signature for the first entry was recorded as "GET on WIRE"[cite: 1].
* The destination IP address identified for the final event in the log was `142.250.1.102`[cite: 1].
* By extracting the `flow_id` (a unique 16-digit number assigned to a network flow), I was able to correlate multiple log records belonging to the same sequence of packets between a source and a destination[cite: 1].
