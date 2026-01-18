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




## 📌 Windows VM
- [ ] VirtualBox creation  
- [ ] Network interface setup  
- [ ] Audit policy configuration  
- [ ] Sysmon installation  
- [ ] Splunk Forwarder setup  
- [ ] Event log forwarding  
- [ ] Dashboard: Failed logins (EventCode 4625)  
- [ ] Dashboard: Process creation (EventCode 4688)  



## 🐉 Kali Linux VM
- [ ] VM setup and interface  
- [ ] Tool installation (Nmap, Hydra, Nikto)  
- [ ] SSH brute-force attack  
- [ ] RDP brute-force attack  
- [ ] Nmap scan results  



## 💥 Metasploitable VM
- [ ] OVA import  
- [ ] Vulnerable services confirmation  
- [ ] Nmap scan detection in Splunk  



## 📊 SIEM (Splunk) VM
- [ ] Splunk installation on Ubuntu  
- [ ] Receiving enabled on port 9997  
- [ ] Installed Splunk Add-ons (Windows, Sysmon, Linux)  
- [ ] Log ingestion confirmation  
- [ ] Dashboard: Failed logins  
- [ ] Dashboard: Process creation  
- [ ] Dashboard: Suspicious traffic (port scans, brute force attempts)  



## ✅ Validation
- [ ] Attack simulation logs visible in Splunk  
- [ ] Dashboards updated with detections  
- [ ] End-to-end SOC workflow proof  

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

