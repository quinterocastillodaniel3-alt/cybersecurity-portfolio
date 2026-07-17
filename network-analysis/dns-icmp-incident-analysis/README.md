# IT/OT Home Lab Network Asset Management & Risk Classification

[![Asset Management](https://img.shields.io/badge/Domain-Asset_Management-blue?style=for-the-badge)](https://www.cisa.gov/cybersecurity-directives)
[![Risk Assessment](https://img.shields.io/badge/Security-Risk_Assessment-darkred?style=for-the-badge)](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-30r1.pdf)
[![IoT Security](https://img.shields.io/badge/Focus-IoT_%26_OT_Security-darkgreen?style=for-the-badge)](https://www.nist.gov/itl/applied-cybersecurity/iot-device-cybersecurity-requirement-catalogs)

## 📌 Project Description
Asset management is a critical pillar of any organizational security framework; you cannot defend resources that are invisible to network administrators. 

In this project, I simulated an asset discovery and risk assessment audit for an engineering home lab and business infrastructure. By mapping network dependencies, identifying physical boundaries, and analyzing threat landscapes across both standard IT systems and Operational Technology (OT) endpoints, I developed a structured asset inventory. Each discovered asset was systematically evaluated and assigned a data sensitivity classification based on the potential impact on Business Continuity, Confidentiality, and Integrity.

---

## 🗺️ Home Lab Asset Inventory

| Asset Component | Network Access | Physical Location | Operational & Security Risk Notes | Sensitivity Classification |
| :--- | :--- | :--- | :--- | :--- |
| **Network Router / Firewall** | Constant | Main Office | Central gateway for all home and lab traffic. Uses isolated VLANs/SSIDs to separate IoT/Manufacturing devices from core data operations. | **Confidential** |
| **Workstation Desktop** | Constant | Main Office | Primary production machine for code development and CAD/mechanical design. Contains sensitive repositories and local backups. | **Secret** |
| **Mobile Endpoint (OPPO A78)** | Intermittent | Mobile / Roaming | Used as the primary device for Multi-Factor Authentication (MFA) tokens and network admin dashboards. High physical loss risk. | **Confidential** |
| **Network Attached Storage (NAS)** | Constant | Server Rack | Houses critical data, mechanical design files, and automated system backups. High-value target for ransomware. | **Secret** |
| **OT Endpoint 1: 3D Printer (Single Filament)** | Intermittent | Workshop | Manufacturing endpoint. Often utilizes unencrypted local web interfaces. Vulnerable to localized network interruption or print-job tampering. | **Restricted** |
| **OT Endpoint 2: Diode Laser Cutter (40x42cm)** | Intermittent | Workshop | Automated fabrication hardware. Requires network segmentation to isolate it from external threats while maintaining local operational availability. | **Restricted** |
| **Smart Security Camera** | Constant | Exterior Perimeter | Legacy IoT device. High vulnerability profile due to firmware decay. Potential vector for unauthorized surveillance or network pivot entry. | **Restricted** |

---

## 🔍 Detailed Assessment of High-Risk Assets

### 1. Network Attached Storage (NAS)
* **Data & Network Profile:** This device stores centralized automated backups, encrypted user data, and proprietary mechanical designs. It maintains a constant, high-throughput network connection via a wired Ethernet port.
* **Risk & Security Analysis:** Serving as the ultimate storage vault, any integrity failure or unauthorized modification (such as ransomware encryption) would result in a catastrophic disruption to operations. 

### 2. Operational Technology (OT) & Manufacturing Endpoints
* **Data & Network Profile:** The 3D printer and diode laser cutter act as local OT endpoints on the network, receiving complex fabrication instructions (G-code) from the main workstation.
* **Risk & Security Analysis:** IoT and manufacturing devices frequently lack built-in robust authentication and often transmit data over unencrypted protocols (e.g., HTTP). If an attacker exploits the network, these devices could be hijacked to halt production, cause physical hardware damage, or serve as a persistent foothold for lateral movement into the main IT network. Strict VLAN segmentation is mandatory.

### 3. Mobile Admin Endpoint
* **Data & Network Profile:** Acts as the mobile authentication hub, carrying TOTP tokens (Authenticator apps) and providing remote access to local network dashboards.
* **Risk & Security Analysis:** The mobility of this asset drastically increases its physical exposure and threat surface. Connecting to untrusted public Wi-Fi networks without an Always-On VPN could compromise admin credentials or allow session hijacking. 

---

## 📊 Sensitivity Classification Criteria Reference

To standardize the risk profile of each device, the following classification matrix was applied during the audit:

* **🔴 Secret:** Critical assets storing highly sensitive, irreplaceable data. Compromise causes severe operational disruption or permanent data loss.
* **🟠 Confidential:** Operational assets containing restricted business information or access tokens. Access is strictly limited and monitored.
* **🟡 Restricted:** Operational OT or IoT assets (like fabrication tools) with limited data access, requiring network isolation due to underlying vulnerability profiles.
* **🟢 Public:** General-use, non-business, or untrusted guest devices requiring total zero-trust isolation from the main network.

---

## 📝 Summary & Security Findings
This network inventory exercise successfully mapped the active perimeter of an engineering home lab, exposing critical dependencies between IT infrastructure and OT manufacturing hardware. 

By evaluating each asset through its connection frequency and operational function, I isolated high-risk entry points—such as the legacy security camera and the fabrication endpoints—from high-value data targets like the NAS. Implementing this proactive inventory and applying a standardized data classification schema is a foundational requirement for deploying effective firewalls, optimizing Access Control Lists (ACLs), and achieving IT/OT convergence security.
