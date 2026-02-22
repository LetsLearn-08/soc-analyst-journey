# 🛡️ SOC Analyst Journey (75-Day Fast Track)

[![SOC Analyst](https://img.shields.io/badge/Role-SOC%20Analyst-blue)](https://www.coursera.org/articles/soc-analyst) [![Cybersecurity](https://img.shields.io/badge/Focus-Cybersecurity-green)](https://www.upguard.com/blog/why-is-cybersecurity-important) [![Learning Path](https://img.shields.io/badge/Track-75%20Days-orange)](https://github.com/LetsLearn-08/soc-analyst-journey#-roadmap-75-days) [![Status](https://img.shields.io/badge/Progress-Completed-success)](https://github.com/LetsLearn-08/soc-analyst-journey)

**Turning Alerts Into Action: A Self‑Driven SOC Path**

## 📖 Introduction
This repository documents my self-driven journey into becoming a SOC Analyst in **75 days**.  
It mirrors my pentesting journey notes but focuses on defensive security: labs, SIEM dashboards, incident reports, playbooks, and threat hunting exercises.  
The goal is to be **job-ready as a SOC Analyst** while building a strong foundation to pivot into **Pentesting/Red Teaming**.

---

## 📑 Table of Contents

| Section | Link |
|---------|------|
| 📖 Introduction | [Jump to Introduction](#-introduction) |
| 📝 Summary – Technical Skills | [Jump to Summary](#-summary--technical-skills) |
| 🚀 Roadmap (75 Days) | [Jump to Roadmap](#-roadmap-75-days) |
| 📅 Phase 1: Lab Setup & SIEM | [Phase 1 Documentation](docs/Phase1_Lab_SIEM.md) |
| 📅 Phase 2: Log Analysis & Detection | [Phase 2 Documentation](docs/Phase2_Log_Analysis.md) |
| 📅 Phase 3: Incident Response Playbooks | [Phase 3 Documentation](docs/Phase3_Incident_Response.md) |
| 📅 Phase 4: Threat Hunting & MITRE ATT&CK | [Phase 4 Documentation](docs/Phase4_Threat_Hunting.md) |
| 📅 Phase 5: Advanced SOC + Pentesting Prep | [Phase 5 Documentation](docs/Phase5_Advanced_SOC.md) |
| 📂 SOC Analyst Projects – Lab Journey | [Jump to Projects](#-soc-analyst-projects--lab-journey) |
| 🛠️ Tools & Resources | [Jump to Tools](#️-tools--resources) |
| 📝 Notes | [Jump to Notes](#-notes) |
| 🔮 Future Work | [Jump to Future-Work](#-future-work) |
| 🌐 Portfolio Links | [Jump to Portfolio-Links](#-portfolio-links) |

---

### 📝 Summary – Technical Skills

**Core SOC Skills**
- **SIEM & Monitoring:** Splunk Enterprise (log ingestion, dashboards, correlation searches, automated alerts).  
- **Endpoint Visibility:** Sysmon (Windows event IDs, custom XML rules for process, network, and registry monitoring).  
- **Threat Intelligence:** AlienVault OTX (IOC enrichment, watchlists, integration into Splunk queries).  
- **Network Analysis:** Wireshark (packet capture, traffic inspection, detection of suspicious connections).  
- **Incident Response:** Playbooks for phishing, brute force, malware; triage workflows and escalation paths.  
- **Threat Hunting:** MITRE ATT&CK mapping, proactive Splunk queries, detection of adversary techniques.  

**Supporting Skills**
- **Log Analysis:** Windows Event Logs, Linux syslogs, firewall logs.  
- **Detection Rules:** PowerShell abuse, privilege escalation, SSH brute force, suspicious Nmap scans.  
- **Documentation:** Checklist-driven, reproducible `.md` files with recruiter-ready summaries.  
- **Proof Management:** Organized screenshots in `proof/` folder linked to each phase.  
- **Pentesting Prep (Intermediate):** Vulnerability scanning with Nmap/Nessus, exploitation labs for validation.  

**Value Statement**
- I combine hands-on SOC lab experience with clear documentation and beginner-friendly manuals.  
- This repo demonstrates my ability to **detect, analyze, and respond to threats** while making complex workflows accessible to recruiters and learners.  
- It reflects both **technical depth** and **communication clarity**, proving readiness for SOC Analyst roles and a foundation to pivot into Pentesting.

---

## 🚀 Roadmap (75 Days)

### 📅 Phase 1: Lab Setup & SIEM (Days 1–15)
- Build virtual lab with Windows, Kali, and Metasploitable VMs.
- Install and configure ELK Stack or Splunk Free.
- Forward logs from Windows Event Logs, Linux syslogs, and firewall logs.
- Create dashboards for login attempts, process creation, and suspicious traffic.
- **Deliverable**: GitHub repo showing lab setup + SIEM dashboards.
- 📂 [Phase 1 Documentation](docs/Phase1_Lab_SIEM.md)

---

### 📅 Phase 2: Log Analysis & Detection (Days 16–30)
- Analyze Windows logs: failed logins, privilege escalation, PowerShell abuse.
- Analyze Linux logs: SSH brute force, sudo misuse, cron jobs.
- Firewall logs: detect Nmap scans, suspicious traffic.
- **Deliverable**: 3–5 incident reports with screenshots + detection steps.
- 📂 [Phase 2 Documentation](docs/Phase2_Log_Analysis.md)

---

### 📅 Phase 3: Incident Response Playbooks (Days 31–45)
- Simulate attacks: phishing, brute force, malware (EICAR).
- Write playbooks: step‑by‑step response guides for each scenario.
- Document escalation paths (Tier‑1 → Tier‑2 SOC workflow).
- **Deliverable**: GitHub folder of playbooks + incident response reports.
- 📂 [Phase 3 Documentation](docs/Phase3_Incident_Response.md)

---

### 📅 Phase 4: Threat Hunting & MITRE ATT&CK (Days 46–60)
- Study MITRE ATT&CK framework.
- Map lab attacks to ATT&CK techniques.
- Write SIEM queries for proactive detection.
- **Deliverable**: Threat hunting queries + ATT&CK mapping documentation.
- 📂 [Phase 4 Documentation](docs/Phase4_Threat_Hunting.md)

---

### 📅 Phase 5: Advanced SOC + Pentesting Prep (Days 61–75)
- Configure SIEM automation: alerts and correlation rules.
- Integrate open‑source threat intelligence feeds into SIEM.
- Pentesting basics: vulnerability scanning (Nmap, Nessus), exploitation labs.
- **Deliverable**: Automated alert rules + vulnerability assessment reports.
- 📂 [Phase 5 Documentation](docs/Phase5_Advanced_SOC.md)

---

## 📂 SOC Analyst Projects – Lab Journey

This repository documents my **hands‑on SOC Analyst journey** through 10 practical projects.  
Each project includes:
- **Technical setup & workflow** → showing how tools like Splunk, Sysmon, Zeek, IDS, and SOAR scripts are used.  
- **Proof screenshots** → stored in dedicated folders for transparency.  
- **Scenario write‑ups** → real‑life stories involving the *Commoner (employee)*, *Attacker*, *Tier‑1 Analyst*, and *Tier‑2 Analyst*, showing how incidents unfold in daily SOC operations.  

---

# 📅 Project Tracker

This tracker documents my SOC Analyst learning journey — one project per day, each focused on a different MITRE ATT&CK tactic.  
Each row links to the detailed write‑up for that project.

| Day | Project | Tools & Frameworks | Detailed Write‑up |
|-----|---------|---------------------|-------------------|
| 1 | 📨 Phishing Simulation – Reconnaissance | Thunderbird, Sysmon, Splunk | [Project 1](projects/project1_phishing.md) |
| 2 | 🛡️ Endpoint Detection & Persistence Monitoring | Sysmon, Splunk | [Project 2](projects/project2_endpoint.md) |
| 3 | 🌐 Network Threat Hunting with Zeek | Zeek, ELK/Splunk | [Project 3](projects/project3_zeek.md) |
| 4 | 🛡️ IDS Deployment & Rule Writing | Suricata, Snort | [Project 4](projects/project4_ids.md) |
| 5 | 🧩 Threat Intelligence Integration | Splunk, MISP | [Project 5](projects/project5_threatintel.md) |
| 6 | ⚙️ SOAR Playbook Automation | Python, Splunk Phantom | [Project 6](projects/project6_soar.md) |
| 7 | ☁️ Cloud Security Monitoring – Lateral Movement | AWS CloudTrail, Azure Sentinel | [Project 7](projects/project7_cloud.md) |
| 8 | 📎 Malware Analysis – Payload Delivery | Cuckoo Sandbox, Sysmon | [Project 8](projects/project8_malware.md) |
| 9 | 🚨 Incident Response Simulation – Containment | Sysmon, Zeek, Splunk | [Project 9](projects/project9_incident_response.md) |
| 10 | 🎯 Honeypot Deployment & Deception | Cowrie Honeypot | [Project 10](projects/project10_honeypot.md) |

---

### 🎭 Storytelling Approach
Each project is told as a **mini SOC drama**:
- 👤 **Commoner (Employee/User)** → the everyday person who unknowingly interacts with the attack.  
- 🎭 **Attacker** → the threat actor initiating the campaign.  
- 👩‍💻 **Tier‑1 Analyst** → the first responder, triaging alerts.  
- 👨‍💻 **Tier‑2 Analyst** → the investigator, confirming and escalating.  

This format helps beginners understand **SOC Analyst responsibilities** while showing recruiters my ability to interpret technical skills and apply tools in real‑world scenarios.

---

📌 By the end of this journey, this repo will serve as a **portfolio of real SOC incidents**, blending technical depth with creative storytelling.


## 🛠️ Tools & Resources

| Tool | Resource | Manual Link |
|------|----------|-------------|
| [Splunk](https://www.splunk.com/) | Official SIEM and observability platform for log ingestion, correlation, and incident detection. | [Splunk Manual](Splunk_Manual.md) |
| [Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon) | Microsoft Sysinternals tool for monitoring process creation, network connections, and event logging. | [Sysmon Manual](Sysmon_Manual.md) |
| [Wireshark](https://www.wireshark.org/) | Leading open-source network protocol analyzer for packet capture and traffic inspection. | [Wireshark Manual](Wireshark_Manual.md) |
| [AlienVault OTX](https://cybersecurity.att.com/open-threat-exchange) | Crowd-sourced threat intelligence platform providing Indicators of Compromise (IOCs). | [OTX Manual](OTX_Manual.md) |
| [Incident Response](https://www.ibm.com/topics/incident-response) | IBM’s guide to incident response: structured processes for detecting, containing, and resolving cyberattacks. | [Incident Response Manual](INCIDENT-RESPOND-LABSETUP-MANUAL.md) |

--- 

## 📝 Notes
- All labs are self‑built, no external training.
- Documentation style: beginner‑friendly, checklist‑driven, reproducible.
- This repo serves as both a **learning log** and a **portfolio** for recruiters.

This journey is more than just learning tools and writing playbooks—it's about proving that **self‑driven learning can rival formal training**.  
I believe in building my own path: setting up labs, simulating attacks, detecting threats, and documenting every step.  

Every alert I triage, every log I analyze, and every playbook I write is a step closer to becoming a **protector‑hacker**—someone who defends systems today and prepares for offensive security challenges tomorrow.  

**75 days of focus, persistence, and curiosity will transform me from a fresher into a SOC Analyst ready to pivot into Pentesting.**

----

## 🔮 Future Work
- Launch separate repo for Azure Sentinel labs.
- Expand IOC enrichment with more threat intel feeds.
- Add beginner‑friendly manuals for additional free tools (e.g., Nessus, Elastic SIEM).

---

## 🌐 Portfolio Links
- [GitHub Profile](https://github.com/LetsLearn-08?tab=repositories)  
- [LinkedIn Profile](https://www.linkedin.com/in/tanuja-reddy-03aa7b38a)


# **From alerts to action — this repo proves my ability to detect, analyze, and respond to threats with clarity and precision.**


