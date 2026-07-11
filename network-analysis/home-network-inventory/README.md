# Home Office Network Asset Management & Risk Classification

## 📌 Project Description
Asset management is a critical pillar of any organizational security framework. It is impossible to defend resources that are untracked or invisible to network administrators. In this project, I simulated an asset discovery and risk assessment audit for a home-based business infrastructure. By mapping network dependencies, defining asset ownership, identifying physical boundaries, and analyzing threat landscapes, I developed a structured asset inventory. Each discovered asset was systematically evaluated and assigned a data sensitivity classification based on the potential impact on Business Continuity, Confidentiality, and Integrity if compromised.

---

## 🗺️ Home Network Asset Inventory

| Asset Component | Network Access | Asset Owner | Physical Location | Operational & Security Risk Notes | Sensitivity Classification |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Network Router** | Constant | Business Owner | Main Office | Central gateway for all home and business traffic. Uses isolated VLANs/SSIDs to separate smart home devices from business operations. Higher risk of unauthorized network enumeration if exposed. | **Confidential** |
| **Workstation Desktop** | Constant | Business Owner | Main Office | Primary production machine. Contains sensitive corporate assets, client logs, source repositories, and local system backups. Local data must remain isolated. | **Secret** |
| **Guest Smartphone** | Intermittent | Guest User | Living Room | Untrusted personal device using standard Wi-Fi. High risk of missing critical security patches or harboring malware. Restricted from accessing internal network segments. | **Public** |
| **Network Attached Storage (NAS)** | Constant | Business Owner | Main Office / Server Rack | Houses critical data, operational intellectual property, and automated system backups. Connected via Ethernet. High target for ransomware or data exfiltration. | **Secret** |
| **Corporate Smart Laptop** | Daily / Mobile | Business Owner | Main Office / Remote | Connects frequently via Wi-Fi and external remote networks. Stores temporary business cache and handles operational access. Requires strict host-based defense monitoring. | **Confidential** |
| **Smart Security Camera** | Constant | Business Owner | Perimeter / Exterior | IoT device connected via Wi-Fi. High vulnerability profile due to legacy firmware risks. Potential vector for unauthorized physical surveillance or network pivot entry. | **Restricted** |

---

## 🔍 Detailed Assessment of Discovered Assets

### 1. Network Attached Storage (NAS)
* **Data & Network Profile:** This device stores centralized automated backups, encrypted user data, and business-critical documentation. It maintains a constant, high-throughput network connection via a wired Ethernet port to ensure immediate data availability.
* **Risk & Security Analysis:** Since it serves as the ultimate storage vault for the home business, any integrity failure or unauthorized modification (such as ransomware encryption) would result in a catastrophic disruption to business operations. 

### 2. Corporate Smart Laptop
* **Data & Network Profile:** Used on a daily basis for active business operations, email communications, and code development. It utilizes wireless connections (Wi-Fi) and shifts between the trusted home perimeter and untrusted remote networks (public Wi-Fi).
* **Risk & Security Analysis:** The mobility of this asset increases its physical exposure and threat surface. Weak endpoint management or a careless posture toward public access points could compromise user credentials or allow session hijacking.

### 3. Smart Security Camera (IoT Asset)
* **Data & Network Profile:** Constantly streaming video feeds to a cloud dashboard over a wireless network connection. It is permanently mounted on the building's exterior perimeter.
* **Risk & Security Analysis:** IoT assets are notorious targets for botnets and lateral movement. If an attacker exploits outdated firmware on this device, they could gain a foothold on the wireless segment and use it to pivot toward more critical endpoints, directly impacting network confidentiality.

---

## 📊 Sensitivity Classification Criteria Reference

To standardize the risk profile of each device, the following classification matrix was applied during the audit:

* **🔴 Secret:** Critical assets storing highly sensitive, irreplaceable data. Compromise causes severe operational disruption or permanent data loss.
* **🟠 Confidential:** Operational assets containing restricted business information. Access is strictly limited to authorized personnel.
* **🟡 Restricted:** Low-risk operational or IoT assets with limited data access, but requiring network isolation due to underlying vulnerability profiles.
* **🟢 Public:** General-use, non-business, or untrusted guest devices. Their compromise poses no direct risk to core organizational data integrity.

---

## 📝 Summary & Security Findings
This network inventory exercise successfully mapped the active perimeter of a home office environment, exposing critical dependencies between everyday consumer electronics and core business systems. By evaluating each asset through its connection frequency, proximity, and ownership, I isolated high-risk entry points—such as IoT smart devices—from high-value data targets like the NAS and Workstation. Implementing this proactive inventory and applying a standardized data classification schema is a foundational requirement for deploying effective firewalls, optimizing access control lists (ACLs), and conducting continuous network vulnerability monitoring.
