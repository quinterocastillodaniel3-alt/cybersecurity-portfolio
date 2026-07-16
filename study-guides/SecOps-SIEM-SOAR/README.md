# 🛡️ SecOps: Centralized Management with SIEM and SOAR

Documentation on monitoring architecture, log management, and automated incident response at the Security Operations Center (SOC) level.

---

## 👁️ Intrusion Detection and Prevention

Monitoring and protecting the network perimeter requires specialized systems:
* **IDS (Intrusion Detection System):** Monitors system activity and alerts on possible intrusions. It is a passive technology focused on visibility.
* **IPS (Intrusion Prevention System):** Actively protects the network by blocking malicious traffic in real-time based on predefined rules.

---

## 📊 SIEM Architecture 
*(Security Information and Event Management)*

SIEM tools collect and analyze log data to monitor an organization's critical activities. The data lifecycle within a SIEM includes:

1. **Collection and Aggregation:** Data is collected from different sources (firewalls, servers, applications) and centralized in one single place.
2. **Normalization:** Raw data is cleaned, structured, and transformed to create coherent, standardized records.
3. **Analysis:** The normalized data is analyzed according to rules, baselines, and threat signatures to trigger security alerts.

---

## 🤖 SOAR and Playbooks
*(Security Orchestration, Automation, and Response)*

Platforms that complement the SIEM by actively interacting with the infrastructure to mitigate threats.

* **Core Function:** A suite of applications, tools, and workflows that uses automation to *respond to* security events rapidly (e.g., Analysis and response to a Security Incident).
* **Automated Playbooks:** Predefined workflows that use automation to execute tasks and response actions (e.g., automatically blocking a malicious IP on the firewall or disabling a compromised Active Directory account) without requiring constant human intervention.

---

## 📝 Bonus: Log Normalization (Log Parsing)

An example of how a SIEM ingests and normalizes a raw firewall log for querying.

**1. Raw Log from the Firewall:**
```text
Oct 14 10:25:01 fw-main %PIX-6-302013: Built inbound TCP connection 44921 for outside:192.168.1.50/41012 (192.168.1.50/41012) to inside:10.0.0.5/80 (10.0.0.5/80)
```

**2. Normalized Log (JSON) stored in the SIEM:**
```json
{
  "timestamp": "2026-10-14T10:25:01Z",
  "device_name": "fw-main",
  "event_id": "PIX-6-302013",
  "action": "Built",
  "protocol": "TCP",
  "src_ip": "192.168.1.50",
  "src_port": 41012,
  "dest_ip": "10.0.0.5",
  "dest_port": 80,
  "status": "success"
}
```
*Normalization enables analysts to perform structured searches, such as querying `src_ip="192.168.1.50" AND action="Built"` across millions of events.*
