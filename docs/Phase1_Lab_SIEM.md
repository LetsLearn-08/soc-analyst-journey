# 📅 Phase 1 Timeline – SOC Lab Journey
  Focused on lab setup and initial detections

## 📅 Timeline

### Day 1–3: Lab Setup
- Installed **VirtualBox** and created 4 VMs (Windows, Kali, Metasploitable, SIEM).  
- Configured **host-only network** (`192.168.56.0/24`).  
- VM Setup Manual:  
  - [Windows 10 VM]
  - [Kali Linux VM] 
  - [Metasploitable 2 VM] 
  - [Ubuntu SIEM VM] 


---
# 🚀 SOC Journey

This repository documents my modular SOC lab environment, built for learning, detection engineering, and community sharing.

## 📚 Reference Manuals

For detailed setup guides and documentation, please visit my **Pentester Journey repo**:

- [Windows VM Setup Manual](https://github.com/LetsLearn-08/Roadmap---Penetration-Testing/tree/main/windows-vm-setup)
- [Splunk SIEM Setup Manual](https://github.com/LetsLearn-08/Roadmap---Penetration-Testing/tree/main/splunk-vm-setup)
- [Kali Linux Setup Manual](https://github.com/LetsLearn-08/Roadmap---Penetration-Testing/tree/main/kali-linux-setup)
- [Metasploitable2 Lab Manual](https://github.com/LetsLearn-08/Roadmap---Penetration-Testing/tree/main/metasploit-lab)

---

Each link takes you to the folder in the Pentester Journey repo where the full README and manuals are stored.


## Day 4–7: VM Configuration
- **Windows VM** → enabled audit policies, installed Sysmon.  
- **Kali VM** → installed tools (Nmap, Hydra, Nikto).  
- **Metasploitable VM** → imported OVA, confirmed vulnerable services.  


---

## Day 8–11: SIEM Installation
- Installed **Splunk Free** on Ubuntu SIEM VM.  
- Enabled receiving on port 9997.  
- Installed Splunk Add-ons (Windows, Sysmon, Linux).  


---

## Day 12–13: Log Forwarding
- Configured **Splunk Forwarder** on Windows and Linux VMs.  
- Forwarded Windows Event Logs, Sysmon, and Linux syslogs.  


---

## Day 14: Dashboards
- Built dashboards for:
  - **Failed logins** (Windows EventCode 4625, Linux SSH failures).  
  - **Process creation** (Sysmon EventCode 1, Windows EventCode 4688).  
  - **Suspicious traffic** (port scans, brute force attempts).  

---

## Day 15: Attack Simulation & Validation
- Used **Kali** to brute-force SSH and RDP.  
- Ran **Nmap scans** against Windows and Metasploitable.  
- Observed detections in dashboards.  


---

# 🖼️ Screenshots Checklist – SOC Lab Phase 1

This file organizes all proof screenshots for Phase 1 of the SOC Lab Journey.  
Each section contains labeled screenshots that validate setup, configuration, and detections.



All Phase 1 screenshots are stored in the [proof folder](https://github.com/LetsLearn-08/soc-analyst-journey/tree/635dc47ce7096d3f7d03c5f1e9cbb5fea7b3e252/proof).

---

## 📊 Phase 1 Learnings & Troubleshooting Issues

| **Category**         | **Key Learnings**                                                                 | **Common Troubleshooting Issues**                                                                 |
|-----------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| **Lab Setup**         | Hands-on practice beats theory; building VMs makes concepts real.                 | Wrong network mode (NAT vs Host-only), IP conflicts in `192.168.56.0/24`.                         |
| **Windows VM**        | Audit policies + Sysmon provide rich telemetry.                                   | Incorrect Sysmon command syntax, missing NetworkConnect rule, Splunk inputs.conf stanza errors.   |
| **Kali Linux VM**     | Attack simulation (Nmap, Hydra) shows how attackers think.                        | Hydra syntax mistakes, forgetting to enable SSH/RDP services before brute force.                  |
| **Metasploitable VM** | Vulnerable services help visualize exploitation.                                  | OVA import errors, VM not booting due to VirtualBox version mismatch.                             |
| **SIEM (Splunk) VM**  | Logs tell stories; dashboards reveal attack patterns.                             | Splunk listener not enabled on port 9997, forwarder misconfigured, missing add-ons.               |
| **Detection**         | Patterns matter more than single events; dashboards highlight brute force & scans.| Dashboards not updating due to missing log sources or misconfigured forwarders.                   |
| **Documentation**     | Writing configs + saving screenshots makes work reproducible and professional.    | Forgetting to label screenshots consistently, README links breaking due to wrong file paths.      |



---

## ✅ Validation
- [ ] Attack simulation logs visible in Splunk  
- [ ] Dashboards updated with detections  
- [ ] End-to-end SOC workflow proof  

---

## 🌟 Reflection

Phase 1 taught me that **cybersecurity is both technical and human**. By Day 15, I had built a working SOC lab, simulated real attacks, and validated detections. Key reflections:

- **Attacker (Kali)** → showed how easy it is to exploit weak systems.  
- **Defender (SIEM dashboards)** → revealed how detections can stop brute force and scans.  
- **Analyst (me)** → learned to connect the dots and tell the story behind the logs.  

### Achievements
- ✅ Built a modular SOC lab with 4 VMs.  
- ✅ Configured Splunk dashboards to visualize real attacks.  
- ✅ Captured proof screenshots for reproducibility.  

### Growth Mindset
- I realized that **logs tell stories** — every failed login or process creation is a clue.  
- **Patterns matter more than single events** — dashboards helped me see brute force and port scans clearly.  
- **Documentation is critical** — saving configs and screenshots made my work professional and shareable.  

This timeline shows my growth from **setup → detection → documentation**.  
It’s just the beginning — next, I’ll explore **AI-powered detection** to see how machine learning can help SOC analysts.


---

## 🔍 What I Learned

Building this Phase 1 SOC lab taught me more than just commands and configs — it gave me perspective on how attackers and defenders think. Key lessons:

- **Hands-on beats theory**  
  Reading about attacks is one thing, but simulating them in a lab made the concepts real.

- **Logs tell stories**  
  Every login attempt, process creation, and network packet is a clue. Learning to read logs felt like learning a new language.

- **Detection is about patterns**  
  A single failed login isn’t suspicious, but hundreds in a row show brute-force. Dashboards helped me see these patterns clearly.

- **Tools are only half the battle**  
  Splunk and ELK are powerful, but they need good configuration (agents, audit policies, Sysmon) to provide useful data.

- **SOC analyst mindset**  
  Always ask: *Is this normal or suspicious?* Context matters more than raw numbers.

- **AI + SOC synergy**  
  AI can scan logs faster than humans, but analysts provide judgment, creativity, and ethical decision-making. Together they’re stronger.

- **Documentation matters**  
  Writing configs, saving screenshots, and building this README made my work reproducible and professional.

---

## 🚀 Next Steps
- **[Phase 2](https://github.com/LetsLearn-08/soc-analyst-journey/blob/f9ffec93bdebe24a701bbcd499408d64ae84c2a9/docs/Phase2_Log_Analysis.md)**→
- Add **AI anomaly detection** to SIEM logs.
- Expand the SOC lab by integrating machine learning techniques into Splunk.
- Focus: Detect unusual login patterns, process anomalies, and network traffic using AI models. Goal: Show how automation and anomaly detection can enhance analyst  
- **[Phase 3](https://github.com/LetsLearn-08/soc-analyst-journey/blob/f9ffec93bdebe24a701bbcd499408d64ae84c2a9/docs/Phase3_Incident_Response.md) **→
- Automate attack simulations and detection workflows.
- Automated Attack Simulations & Detection Workflows**
- Introduce scripted attack simulations (e.g., brute force, port scans, privilege escalation) and automate detection queries. Focus: Build repeatable workflows that generate consistent    proof for dashboards.
- Goal: Demonstrate how automation reduces manual effort and strengthens SOC playbooks.
- Long-term → Build a platform where anyone can turn their stories into **cybersecurity labs + anime narratives**.

# Logs tell stories, analysts write the truth.
## 📢 Stay Tuned
Follow my journey: **[@Lets Learn-08](https://github.com/LetsLearn-08)**  

