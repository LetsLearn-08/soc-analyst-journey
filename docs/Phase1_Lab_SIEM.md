# 📅 Phase 1 Timeline – SOC Lab Journey

## 📅 Timeline

### Day 1–3: Lab Setup
- Installed **VirtualBox** and created 4 VMs (Windows, Kali, Metasploitable, SIEM).  
- Configured **host-only network** (`192.168.56.0/24`).  
- VM Setup Manual:  
  - [Windows 10 VM]
  - [Kali Linux VM] 
  - [Metasploitable 2 VM] 
  - [Ubuntu SIEM VM] 
- Proof: [Architecture Diagram](docs/architecture-diagram.png)

---

# 🚀 SOC Journey

This repository documents my modular SOC lab environment, built for learning, detection engineering, and community sharing.

## 🔗 Linked Subprojects (from Pentester Journey)

- [Windows 10 SOC Lab](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/windows-vm-setup/README.md)
  - [Windows Installation Guide](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/windows-vm-setup/markdown/windows-install.md)
  - [Guest Additions Setup](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/windows-vm-setup/markdown/guest-additions.md)
  - [SOC Preparation](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/windows-vm-setup/markdown/soc-prep.md)
  - [Lab Status](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/windows-vm-setup/markdown/status.md)

- [Splunk SIEM Lab](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/splunk-vm-setup/README.md)
  - [Splunk Installation Guide](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/splunk-vm-setup/markdown/splunk-install.md)
  - [Windows Integration](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/splunk-vm-setup/markdown/splunk-integration.md)
  - [Dashboards & Alerts](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/splunk-vm-setup/markdown/splunk-dashboards.md)
  - [Lab Status](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/splunk-vm-setup/markdown/status.md)

- [Kali Linux Lab](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/kali-vm-setup/README.md)
  - [Kali Installation Guide](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/kali-vm-setup/markdown/kali-install.md)
  - [Host‑Only Networking](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/kali-vm-setup/markdown/host-only-networking.md)
  - [Troubleshooting Guide](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/kali-vm-setup/markdown/troubleshooting.md)
  - [Lab Status](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/kali-vm-setup/markdown/status.md)

- [Metasploitable2 Lab](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/metasploitable2-vm-setup/README.md)
  - [Overview & Safety Notes](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/metasploitable2-vm-setup/markdown/metasploitable-overview.md)
  - [Nmap Workflow](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/metasploitable2-vm-setup/markdown/nmap-workflow.md)
  - [Findings Summary](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/metasploitable2-vm-setup/markdown/findings-summary.md)
  - [NSE Script Template](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/metasploitable2-vm-setup/markdown/nse-template.md)
  - [Lab Status](https://github.com/LetsLearn-08/pentester-journey/blob/main/docs/metasploitable2-vm-setup/markdown/status.md)



## Day 4–7: VM Configuration
- **Windows VM** → enabled audit policies, installed Sysmon.  
- **Kali VM** → installed tools (Nmap, Hydra, Nikto).  
- **Metasploitable VM** → imported OVA, confirmed vulnerable services.  
- Proof: [Windows Audit Policy Screenshot](screenshots/windows-audit-policy.png)

---

## Day 8–11: SIEM Installation
- Installed **Splunk Free** on Ubuntu SIEM VM.  
- Enabled receiving on port 9997.  
- Installed Splunk Add-ons (Windows, Sysmon, Linux).  
- Proof: [Splunk Web Login Screenshot](screenshots/splunk-login.png)

---

## Day 12–13: Log Forwarding
- Configured **Splunk Forwarder** on Windows and Linux VMs.  
- Forwarded Windows Event Logs, Sysmon, and Linux syslogs.  
- Proof: [Forwarder Config File](configs/linux/forwarder-commands.sh)

---

## Day 14: Dashboards
- Built dashboards for:
  - **Failed logins** (Windows EventCode 4625, Linux SSH failures).  
  - **Process creation** (Sysmon EventCode 1, Windows EventCode 4688).  
  - **Suspicious traffic** (port scans, brute force attempts).  
- Proof:  
  - [Failed Logins Dashboard](screenshots/windows-failed-logons.png)  
  - [Process Creation Dashboard](screenshots/process-creation.png)  
  - [Suspicious Traffic Dashboard](screenshots/port-scan-detection.png)

---

## Day 15: Attack Simulation & Validation
- Used **Kali** to brute-force SSH and RDP.  
- Ran **Nmap scans** against Windows and Metasploitable.  
- Observed detections in dashboards.  
- Proof: [Linux Auth Failures Screenshot](screenshots/linux-auth-failures.png)

---

## 📌 Proof of Work

Here are direct links to the evidence of my lab setup and detections:

- **[Windows Failed Logins Screenshot](screenshots/windows-failed-logons.png)**  
  Shows multiple failed login attempts detected in Splunk/ELK.

- **[Linux Auth Failures Screenshot](screenshots/linux-auth-failures.png)**  
  Captures SSH brute-force attempts from Kali against Linux.

- **[Process Creation Screenshot](screenshots/process-creation.png)**  
  Displays Sysmon logs of suspicious processes (e.g., PowerShell, Notepad).

- **[Suspicious Traffic Screenshot](screenshots/port-scan-detection.png)**  
  Visualizes Nmap port scans from Kali against Metasploitable.

- **[Sysmon Config File](configs/windows/sysmon-config.xml)**  
  The exact Sysmon configuration I used to enrich Windows logs.

- **[Splunk Saved Searches](configs/siem/savedsearches.txt)**  
  Queries used to build dashboards for login attempts, process creation, and traffic anomalies.

- **[Forwarder Commands](configs/linux/forwarder-commands.sh)**  
  Commands used to configure Splunk Forwarders on Linux machines.

---

## 🌟 Reflection

This Phase 1 journey taught me that **cybersecurity is both technical and human**.By Day 15, I had:  
- The attacker (Kali) shows me how easy it is to exploit weak systems.  
- The defender (SIEM dashboards) shows me how to catch those attacks.  
- The analyst (me) learns to connect the dots and tell the story.
- A working **SOC lab** with 4 VMs.  
- A **SIEM dashboard** showing real attacks.  
- Proof of detections saved in this repo.  
This timeline shows my growth from setup → detection → documentation. 

This is just the beginning — next, I’ll explore **AI-powered detection** to see how machine learning can help SOC analysts.

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
- Phase 2 → Add **AI anomaly detection** to SIEM logs.  
- Phase 3 → Automate attack simulations and detection workflows.  
- Long-term → Build a platform where anyone can turn their stories into **cybersecurity labs + anime narratives**.

# Logs tell stories, analysts write the truth.
## 📢 Stay Tuned
Follow my journey: **[@Lets Learn-08](https://github.com/LetsLearn-08)**  

