# Incident Response: Spear-Phishing & Social Engineering Analysis

[![Spear-Phishing](https://img.shields.io/badge/Attack_Vector-Spear--Phishing-red?style=for-the-badge)](https://attack.mitre.org/techniques/T1566/002/)
[![Social Engineering](https://img.shields.io/badge/Tactic-Social_Engineering-orange?style=for-the-badge)](https://www.cisa.gov/news-events/news/avoiding-social-engineering-and-phishing-attacks)
[![Credential Harvesting](https://img.shields.io/badge/Impact-Credential_Harvesting-darkred?style=for-the-badge)](https://attack.mitre.org/techniques/T1056/)

## 📌 Project Description
As a Security Analyst for a financial institution (Imaginary Bank), I was tasked with investigating a suspicious email escalated by the Chief Financial Officer (CFO). The email appeared to be an internal communication from the board of directors urging the executive to install a new collaboration software called "ExecuTalk." 

This project breaks down the forensic analysis of the email to extract Indicators of Compromise (IoCs), expose the social engineering tactics used by the threat actor, and determine the necessary containment actions to protect the organization's endpoints and identities.

---

## 📧 Phase 1: Email Header Analysis
The first step in triage is analyzing the email header metadata. Threat actors routinely attempt to spoof addresses, but header analysis often reveals their true origin and intent.

**Suspicious Email Header:**
> **From:** imaginarybank@gmail.org
> **Sent:** Saturday, December 21, 2019 15:05:05
> **To:** cfo@imaginarybank.com
> **Subject:** RE: You have been added to an ecsecutiv groups

### 🚩 Indicators of Compromise (IoCs):
1. **Domain Mismatch:** Legitimate corporate infrastructure does not route internal requests through public or free email domains. The sender utilized `@gmail.org` instead of the verified `@imaginarybank.com` tenant.
2. **Spelling and Grammar Errors:** The subject line contains glaring typos ("ecsecutiv groups"), which is highly uncharacteristic of official, board-level communications.
3. **Fabricated Thread (RE:):** The subject is prepended with "RE:" to trick the victim into believing this is part of an ongoing, legitimate conversation they simply overlooked, lowering their initial skepticism.

---

## 🎭 Phase 2: Body & Social Engineering Tactics
Threat actors rely heavily on psychological manipulation. The body of the email was meticulously crafted to bypass human filters by appearing legitimate while simultaneously inducing panic.

**Email Body Extract:**
> *Conglaturations! You have been added to a collaboration group 'Execs'*
> *Download ExecuTalk to your computer.*
> *Mac® | Windows® | Android™*
> *Your team needs you! This invite will expire in 48 hours, so act fast.*

### 🔍 Deception Tactics Used:
* **Brand Legitimacy (Authority):** The attacker used official-looking brand labeling, copyright symbols (©, ™, ®), and explicit download options for major operating systems. This creates the illusion of an established, cross-platform enterprise tool.
* **Sense of Urgency (Scarcity):** By stating *"Your team needs you! This invite will expire in 48 hours,"* the attacker manufactures a false sense of urgency, pressuring the executive to act impulsively without verifying the request through standard IT Helpdesk channels.

---

## 🎣 Phase 3: Payload & URL Analysis
Investigating the download options required safely hovering over the embedded hyperlinks (link inspection) without executing the payload in a production environment. 

![Fake Login Page](image_37ad5a.png)

### 🚩 Critical Finding: Credential Harvesting URL
While the login form visually mimics a legitimate enterprise Single Sign-On (SSO) portal—complete with corporate branding and OAuth options like "Continue with Google"—**the primary IoC is the URL itself**. 

The page is hosted on `my.site.net/pwnexecs/`. When accessing internal corporate SaaS services, the URL must align with the organization's verified domain structure or a trusted vendor's domain. The use of a generic, unverified hosting site confirms this is a rogue landing page designed exclusively to capture the CFO's username and password (Credential Harvesting).

---

## 🛡️ Remediation & Mitigation Strategy
**Action Taken: Quarantine & Alert**

Based on the overwhelming evidence of domain spoofing, social engineering (urgency), and a malicious credential-harvesting URL, this email was classified as a highly targeted **Spear-Phishing attack**.

Immediate response procedures included:
1. **Containment (Quarantine):** The email hash, sender IP, and malicious URL were added to the secure email gateway's (SEG) blocklist. The email was actively purged from the CFO's inbox and globally across the organization to prevent lateral exposure.
2. **Threat Intelligence & Awareness:** The extracted IoCs were documented and ingested into the SIEM. A targeted security bulletin was issued to the executive team, reminding them to exercise caution and verify unexpected software installation requests directly with IT operations.
