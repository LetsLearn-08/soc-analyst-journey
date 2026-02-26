# 🛡️ SOC Analyst Journey 

[![SOC Analyst](https://img.shields.io/badge/Role-SOC%20Analyst-blue)](https://www.coursera.org/articles/soc-analyst) [![Cybersecurity](https://img.shields.io/badge/Focus-Cybersecurity-green)](https://www.upguard.com/blog/why-is-cybersecurity-important) [![Learning Path](https://img.shields.io/badge/Track-100%20Days-orange)](https://github.com/LetsLearn-08/soc-analyst-journey#-roadmap-100-days) [![Status](https://img.shields.io/badge/Progress-Completed-success)](https://github.com/LetsLearn-08/soc-analyst-journey)

**Turning Alerts Into Action: A Self‑Driven SOC Path**

## 📖 Introduction
This repository documents my self-driven journey into becoming a SOC Analyst in **100 days**.  
It mirrors my pentesting journey notes but focuses on defensive security: labs, SIEM dashboards, incident reports, playbooks, and threat hunting exercises.  
The goal is to be **job-ready as a SOC Analyst** while building a strong foundation to pivot into **Pentesting/Red Teaming**.

---

## 📑 Table of Contents

| Section | Link |
|---------|------|
| 📖 Introduction | [Jump to Introduction](#-introduction) |
| 📝 Summary – Technical Skills | [Jump to Summary](#-summary--technical-skills) |
| 🚀 Roadmap  | [Jump to Roadmap](#-roadmap) |
| 📅 Phase 1: Lab Setup & SIEM | [Phase 1 Documentation](docs/Phase1_Lab_SIEM.md) |
| 📅 Phase 2: Log Analysis & Detection | [Phase 2 Documentation](docs/Phase2_Log_Analysis.md) |
| 📅 Phase 3: Incident Response Playbooks | [Phase 3 Documentation](docs/Phase3_Incident_Response.md) |
| 📅 Phase 4: Threat Hunting & MITRE ATT&CK | [Phase 4 Documentation](docs/Phase4_Threat_Hunting.md) |
| 📅 Phase 5: Advanced SOC + Pentesting Prep | [Phase 5 Documentation](docs/Phase5_Advanced_SOC.md) |
| 📅 Phase 6: EDR Tools | [Phase 6 Documentation](docs/Phase6_EDR.md) | 
| 📅 Phase 7: Vulnerability Management | [Phase 7 Documentation](docs/Phase7_VulnerabilityMgmt.md) |
| 📅 Phase 8: Cloud Security Basics | [Phase 8 Documentation](docs/Phase8_CloudSecurity.md) | 
| 📅 Phase 9: Threat Intelligence | [Phase 9 Documentation](docs/Phase9_ThreatIntel.md) |
| 📂 SOC Analyst Projects – Lab Journey | [Jump to Projects](#-soc-analyst-projects--lab-journey) |
| 🛠️ Tools & Resources | [Jump to Tools](#️-tools--resources) |
| 📝 Notes | [Jump to Notes](#-notes) |
| 🔮 Future Work | [Jump to Future-Work](#-future-work) |
| 🌐 Portfolio Links | [Jump to Portfolio-Links](#-portfolio-links) |

---

### 📝 Summary – Technical Skills

| Phase | Focus Area | Tools / Methods | Key Outcomes |
|-------|------------|-----------------|-----------------|
| Phase 1 | Lab Setup & SIEM | Splunk Enterprise, Sysmon | Log ingestion, dashboards, correlation searches, automated alerts |
| Phase 2 | Log Analysis & Detection | Windows Event Logs, Linux syslogs, firewall logs | Event visibility, detection of suspicious activity |
| Phase 3 | Incident Response Playbooks | SOAR workflows, phishing/brute force/malware playbooks | Triage, escalation, containment |
| Phase 4 | Threat Hunting & MITRE ATT&CK | Suricata IDS, custom rules, ATT&CK mapping | Proactive detection of adversary techniques |
| Phase 5 | Advanced SOC + Pentesting Prep | Nmap, Nessus, exploitation labs | Vulnerability scanning, validation of detections |
| Phase 6 | EDR Tools | Wazuh, OSSEC, Windows Defender logs *(placeholder: Cortex XDR / CrowdStrike)* | Endpoint visibility, host intrusion detection |
| Phase 7 | Vulnerability Management | OpenVAS, Nmap service detection, CVE tracking *(placeholder: Nessus Essentials)* | System hardening, CVE awareness |
| Phase 8 | Cloud Security Basics | Azure Entra ID, AWS IAM, GCP IAM *(placeholder: TryHackMe labs)* | Identity & access management across cloud platforms |
| Phase 9 | Threat Intelligence | AlienVault OTX, Abuse.ch feeds, MITRE ATT&CK Navigator | IOC enrichment, adversary profiling, Splunk integration |

### 🛡️ Core SOC Skills

| Focus Area | Tools / Methods | Key Outcomes |
|------------|-----------------|--------------|
| SIEM & Monitoring | Splunk Enterprise | Log ingestion, dashboards, correlation searches, automated alerts |
| Endpoint Visibility | Sysmon, Wazuh, OSSEC, Windows Defender | Windows Event IDs, custom XML rules, host intrusion detection |
| Threat Intelligence | AlienVault OTX, Abuse.ch, MITRE ATT&CK Navigator | IOC enrichment, adversary profiling, ATT&CK mapping |
| Network Analysis | Wireshark, Suricata IDS, Nmap | Packet capture, IDS rules, service detection |
| Incident Response | SOAR workflows, playbooks | Phishing, brute force, malware triage, escalation paths |
| Vulnerability Management | OpenVAS, Nessus Essentials | System hardening, CVE awareness, vulnerability assessment |
| Cloud Security | Azure Entra ID, AWS IAM, GCP IAM | Identity & access management across cloud platforms |
| Threat Hunting | Splunk queries, MITRE ATT&CK | Proactive detection of adversary techniques |


- I combine hands‑on SOC lab experience with clear documentation and beginner‑friendly manuals.
- This repo demonstrates my ability to detect, analyze, and respond to threats while making complex workflows accessible to recruiters and learners.
- It reflects both technical depth and communication clarity, proving readiness for SOC Analyst roles and a foundation to pivot into Pentesting.

---


## 🚀 Roadmap 

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
### 📅 Phase 6: EDR Tools (Days 76-80)
- Deploy Wazuh (open-source) for endpoint monitoring.
- Configure OSSEC for host intrusion detection.
- Collect and analyze Windows Defender logs.
- *(Placeholder: Cortex XDR / CrowdStrike for enterprise context)*  
- **Deliverable**: Detection reports with screenshots of EDR alerts and rule configurations.
- 📂 [Phase 6 Documentation](docs/Phase6_EDR.md)
---

### 📅 Phase 7: Vulnerability Management (Days 80-85)
- Perform OpenVAS scans for system vulnerabilities.
- Use Nmap for service detection and enumeration.
- Track CVEs using MITRE CVE database.
- *(Placeholder: Nessus Essentials for extended scanning)*  
- **Deliverable**: Vulnerability assessment reports with screenshots + CVE references.
- 📂 [Phase 7 Documentation](docs/Phase7_VulnerabilityMgmt.md)
---

### 📅 Phase 8: Cloud Security Basics (Days 86-95)
- Configure Azure Entra ID sandbox for IAM policies.
- Explore AWS IAM (free tier) for role-based access.
- Test GCP IAM (free tier) for identity management.
- *(Placeholder: TryHackMe Premium labs for advanced scenarios)*  
- **Deliverable**: IAM configuration screenshots + documentation of access policies.
- 📂 [Phase 8 Documentation](docs/Phase8_CloudSecurity.md)
---

### 📅 Phase 9: Threat Intelligence (Days 96-100)
- Integrate AlienVault OTX feeds into Splunk queries.
- Use Abuse.ch feeds for malware and botnet tracking.
- Map adversary techniques with MITRE ATT&CK Navigator.
- Build IOC tables and adversary profiles.  
- **Deliverable**: Threat intelligence report with IOC tables, ATT&CK mappings, and screenshots.
- 📂 [Phase 9 Documentation](docs/Phase9_ThreatIntel.md)
---

## 📂 SOC Analyst Projects – Lab Journey

This repository documents my **hands‑on SOC Analyst journey** through 10 practical projects.  
Each project includes:

| Component | Description | Example Evidence |
|-----------|-------------|------------------|
| 🛠️ Technical Setup & Workflow | Tools like Splunk, Sysmon, Zeek, IDS, and SOAR scripts configured in lab environments. | Config files, SIEM dashboards, IDS rules |
| 📸 Proof Screenshots | Transparent evidence stored in dedicated `proof/` folders. | Screenshots of alerts, logs, dashboards |
| 🎭 Scenario Write‑ups | Real‑life SOC stories involving the *Commoner (employee)*, *Attacker*, *Tier‑1 Analyst*, and *Tier‑2 Analyst*. | Markdown reports mapping incidents to MITRE ATT&CK |


---

# 📅 Project Tracker

This tracker documents my SOC Analyst learning journey — one project per day, each focused on a different MITRE ATT&CK tactic.  
Each row links to the detailed write‑up for that project.

| Day | Project | Tools & Frameworks | Detailed Write‑up |
|-----|---------|---------------------|-------------------|
| 1 | 📨 Phishing Simulation – Reconnaissance | Thunderbird, Sysmon, Splunk | [Project 1](https://github.com/LetsLearn-08/soc-analyst-journey/blob/c42237e461fc94c68b837c110e9acffaab51812c/project1_phishing.md) |
| 2 | 🛡️ Endpoint Detection & Persistence Monitoring | Sysmon, Splunk | [Project 2](https://github.com/LetsLearn-08/soc-analyst-journey/blob/c42237e461fc94c68b837c110e9acffaab51812c/project2_sysmon.md) |
| 3 | 🌐 Network Threat Hunting with Zeek | Zeek, ELK/Splunk | [Project 3](projects/project3_zeek.md) |
| 4 | 🛡️ IDS Deployment & Rule Writing | Suricata, Snort | [Project 4](projects/project4_ids.md) |
| 5 | 🧩 Threat Intelligence Integration | Splunk, MISP | [Project 5](projects/project5_threatintel.md) |
| 6 | 🖥️ Endpoint Detection & Response (EDR) | Wazuh, Windows Defender, Splunk | [Project 6](projects/project6_edr.md) |
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
| [Windows Defender](https://learn.microsoft.com/en-us/windows/security/threat-protection/windows-defender-antivirus/) | Built-in endpoint protection for Windows, providing logs and malware detection. | [Windows Defender Manual](docs/WindowsDefender_Manual.md) | 
| [OpenVAS](https://www.openvas.org/) | Open-source vulnerability scanner for system and network assessments. | [OpenVAS Manual](docs/OpenVAS_Manual.md) | 
| [Nmap](https://nmap.org/) | Network mapper for service detection, port scanning, and vulnerability discovery. | [Nmap Manual](docs/Nmap_Manual.md) |
| [Azure Entra ID](https://learn.microsoft.com/en-us/entra/) | Microsoft’s cloud identity and access management solution. | [Azure Manual](docs/Azure_Manual.md) | 
| [AWS IAM](https://aws.amazon.com/iam/) | Identity and Access Management service for AWS cloud. | [AWS IAM Manual](docs/AWS_IAM_Manual.md) | 
| [GCP IAM](https://cloud.google.com/iam) | Google Cloud’s identity and access management service. | [GCP IAM Manual](docs/GCP_IAM_Manual.md) | 
| [MITRE ATT&CK Navigator](https://attack.mitre.org/resources/navigator/) | Framework for mapping adversary techniques and detection coverage. | [ATTACK Navigator Manual](docs/ATTACK_Navigator_Manual.md) | 
| [Abuse.ch](https://abuse.ch/) | Threat intelligence feeds for malware, botnets, and phishing campaigns. | [Abuse.ch Manual](docs/Abusech_Manual.md) |
--- 

## 📝 Notes

- All labs are self‑built, no external training.
- Documentation style: beginner‑friendly, checklist‑driven, reproducible.
- This repo serves as both a **learning log** and a **portfolio** for recruiters.

This journey is more than just learning tools and writing playbooks—it's about proving that **self‑driven learning can rival formal training**.  
I believe in building my own path: setting up labs, simulating attacks, detecting threats, and documenting every step.  

Every alert I triage, every log I analyze, and every playbook I write is a step closer to becoming a **protector‑hacker**—someone who defends systems today and prepares for offensive security challenges tomorrow.  

**100 days of focus, persistence, and curiosity will transform me from a fresher into a SOC Analyst ready to pivot into Pentesting.**

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


