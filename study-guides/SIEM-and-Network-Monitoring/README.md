# 👁️ SIEM & Network Monitoring Fundamentals

This repository outlines the core concepts of Security Information and Event Management (SIEM) systems, log anatomy, and network monitoring tools used by Security Operations Centers (SOC).

---

## 📜 Log Anatomy and Parsing

Logs are the foundation of network visibility. A comprehensive audit log typically contains the following critical details (answering the Who, What, When, and Where):
* **Date & Time:** When the event occurred (Timestamp).
* **Sender/Source:** The user, system, or process that generated the event.
* **Location:** The origin or destination (e.g., IP addresses, network paths).

### Syslog Structure
Syslog is a standard protocol used to send system log or event messages to a specific server. A standard syslog entry consists of three main parts:
1. **Header:** Contains the timestamp and hostname.
2. **Structured Data:** Provides a standard format for parsing.
3. **Message:** The actual event description.

### Log Normalization
SIEM tools aggregate raw data from thousands of endpoints. **Normalization** is the automated process of converting these disparate raw logs into a consistent, standardized format so they can be easily searched and correlated.

---

## 🛡️ Intrusion Detection Systems (IDS)

Understanding the placement and scope of detection systems is critical for network defense.

* **NIDS (Network-Based IDS):** Collects and monitors network traffic and network data as it flows across the infrastructure.
* **HIDS (Host-Based IDS):** Installed directly on a specific machine (endpoint) and monitors only the activity occurring on that specific host.

---

## 🦑 Suricata & Signature Rules

Suricata is a robust, open-source network threat detection engine capable of generating different types of log data, primarily:
* **Alerts:** Triggered when traffic matches a specific rule.
* **Network Telemetry:** Data regarding network performance and traffic flow.

### Signature Headers
A detection rule (signature) relies on a structured header to evaluate traffic. A standard signature header includes:
* **Action:** What to do if the rule matches (e.g., `alert`, `drop`).
* **Protocol:** The network protocol being inspected (e.g., `tcp`, `udp`, `http`).
* **IP Addresses & Port Numbers:** The source and destination coordinates.

**Rule Options:** To match traffic based on the state and direction of the connection, the **`flow`** rule option is used (e.g., `flow:established,to_server`).

---

## 🛠️ Enterprise SIEM Platforms

Different SIEM vendors utilize different languages and architectures for threat hunting:
* **Splunk:** An analyst using Splunk to search through unstructured "A records" (or raw logs) will typically perform a **Raw log search**.
* **Google Chronicle:** Chronicle relies on **YARA-L**, a specialized language used specifically to define advanced threat detection rules.
