# Cybersecurity Risk Assessment & Registry - Commercial Banking Audit

## 📌 Project Description
Risk assessments are foundational to establishing an adaptive security posture aligned with the **NIST Cybersecurity Framework (CSF)**. Security teams conduct risk assessments to evaluate whether defensive operations are mature enough to prevent cyberattacks, enforce data integrity, and shield fiscal assets. In this project, I simulated a comprehensive risk assessment for a coastal commercial bank serving 2,200 local accounts and operating under strict Federal Reserve capital regulations. I developed a centralized **Risk Register** to evaluate five structural threats against the organization, scoring their individual Likelihood and Impact to mathematically prioritize administrative and technical remediation vectors.

---

## 🏛️ Operating Environment & Risk Factors
Security events manifest when systemic vulnerabilities intersect with opportunistic threat actors or environmental hazards. The bank's risk profile is uniquely shaped by the following organizational factors:
* **Human Perimeter:** A combined staff of 100 on-site employees and 20 remote workers significantly expands the organization's social engineering attack surface.
* **Asset Exposure:** Managing 2,000 individual checking accounts and 200 corporate commercial entities creates a highly lucrative repository of financial data and transactional funds.
* **Geographic & Regulatory Constraints:** The bank is located in a low-crime coastal area, shifting physical threat models from human burglary to environmental supply chain disruptions (e.g., hurricanes). Concurrently, compliance mandates require strict daily liquidity limits, meaning any localized data availability disruption risks massive federal regulatory fines.

---

## 📊 Qualitative Risk Assessment Matrix

The risk priority score is calculated using the standard qualitative risk formula:
$$\text{Likelihood (1-3)} \times \text{Impact/Severity (1-3)} = \text{Risk Priority Score (1-9)}$$

### Risk Register

| Identified Threat Vector | Threat Description | Likelihood (1-3) | Severity / Impact (1-3) | Total Risk Score (1-9) | Priority Level |
| :--- | :--- | :---: | :---: | :---: | :--- |
| **Business Email Compromise (BEC)** | Targeted spear-phishing campaigns leveraging spoofed executive identities to trick internal accounting personnel into authorizing fraudulent wire transfers. | **3** | **2** | **6** | 🟠 **High** |
| **Compromised User Database** | External threat actors brute-forcing or exploiting web application vulnerabilities to extract hashed passwords and credentials of the 2,200 clients. | **2** | **3** | **6** | 🟠 **High** |
| **Financial Records Data Leak** | Accidental internal data exfiltration or privilege misuse leading to the public exposure of the 200 commercial entities' banking history. | **2** | **3** | **6** | 🟠 **High** |
| **Physical Bank Robbery** | Armed entry or physical theft of vault assets during operational hours by a malicious threat group. | **1** | **2** | **2** | 🟢 **Low** |
| **Supply Chain Attack** | Cyberattack on the primary external clearing house or clearing vendor, or environmental disruption (hurricanes) halting asset deliveries. | **2** | **2** | **4** | 🟡 **Medium** |

---

## 🔍 In-Depth Threat Scenario Analysis

### 1. Business Email Compromise (BEC)
* **Risk Context:** With 20 remote employees connecting via distributed networks and 100 local staff members managing daily commercial wires, the probability of human error or social engineering success is high. 
* **Justification:** Staff dealing with high-volume requests can be manipulated via urgent, tailored phishing vectors. While the immediate financial transfer might not break the bank, it creates operational friction and damages local business relationships.

### 2. Compromised User Database & Financial Data Leaks
* **Risk Context:** The bank stores credentials and transaction details for thousands of retail and commercial accounts. 
* **Justification:** The likelihood is moderate due to layered access controls, but the impact is maximal (3). A breach of this nature exposes the firm to immediate regulatory enforcement actions by financial oversight bodies, catastrophic reputation loss among local businesses, and class-action litigation due to the exposure of Personally Identifiable Information (PII).

### 3. Supply Chain Disruption & Physical Robbery
* **Risk Context:** The bank operates in a secure, low-crime coastal town, reducing physical theft likelihood to a bare minimum (1). However, the coastal geography introduces environmental risk vectors.
* **Justification:** External logistical channels and third-party vendors are vulnerable to structural disruptions from seasonal hurricanes. A supply chain halt scored a medium risk (4) because even temporary operational downtime directly impacts the bank's capability to maintain required cash reserves on-site to satisfy Federal Reserve compliance thresholds.

---

## 🎯 Security Strategic Remediation Roadmap
Based on the quantitative risk scores calculated in the matrix, security resource allocation will be prioritized into three immediate tiers:

1. **Immediate Focus (Score 6 - BEC & Database Protection):** Implementation of Mandatory Multi-Factor Authentication (MFA) across all corporate endpoints, role-based access controls (RBAC) on the customer database, and continuous automated phishing simulation exercises for remote and local personnel.
2. **Secondary Focus (Score 4 - Supply Chain Hardening):** Developing secondary redundant communication channels and establishing off-site backup power grids to maintain liquidity workflows during localized coastal environmental incidents.
3. **De-prioritized (Score 2 - Physical Burglary):** Maintaining baseline automated infrastructure monitoring and local police coordination, avoiding further immediate capital expenditures in this vector.

---

## 📝 Summary
By conducting this formal risk assessment, I evaluated the bank’s specific threat vectors against its operational, geographical, and regulatory constraints. Leveraging a standardized Risk Register allowed the cybersecurity team to move from ambiguous security fears to a quantified, prioritizable mitigation roadmap. Restricting high-impact exposures (such as financial data leaks) and high-likelihood vectors (such as BEC) safeguards business continuity, preserves client trust, and ensures the enterprise maintains strict adherence to federal monetary regulations.
