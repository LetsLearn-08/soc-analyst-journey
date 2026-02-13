# 📅 Phase 4 Timeline – Threat Hunting & MITRE ATT&CK

## 📅 Timeline

### Day 46–48: MITRE ATT&CK Study
- Reviewed **ATT&CK framework categories**: Initial Access, Execution, Persistence.  
- Selected techniques relevant to lab simulations (e.g., **T1110 – Brute Force**, **T1059 – Command Execution**).  
- Documented how each technique maps to SOC detections.  

---

### Day 49–52: Mapping Attacks
- Mapped **brute force, phishing, and malware simulations** to ATT&CK techniques.  
- Created documentation tables linking **attack → technique → detection query**.  
- Stored mappings in `/docs/Phase4_Threat_Hunting.md`.  

---

### Day 53–56: SIEM Query Development
- Wrote **Splunk queries** for proactive detection of brute force, phishing, and malware.  
- Tested queries against lab logs.  
- Documented query results with screenshots.  

---

### Day 57–60: Threat Hunting Reports
- Compiled **threat hunting documentation** in `/docs/Phase4_Threat_Hunting.md`.  
- Linked ATT&CK mappings and SIEM queries.  
- Added screenshots of query results and detections.  


---
# 📊 Phase 4 Detection Summary – SOC Lab

## 🔎 Validated Detections (Sysmon + Splunk)

| Technique (MITRE ATT&CK) | Sysmon Event ID | Example Process | Splunk Query | Screenshot Name |
|---------------------------|-----------------|-----------------|--------------|-----------------|
| Registry Persistence (T1547.001) | 13 | `lsass.exe` modifying Run keys | `index=win_logs EventCode=13 TargetObject="*\\Run*" OR TargetObject="*\\RunOnce*"` | `phase4_registry_splunk.png` |
| Scheduled Task Creation (T1053.005) | 1 | `schtasks.exe`, `taskeng.exe` | `index=win_logs EventCode=1 Image="*schtasks.exe" OR Image="*taskeng.exe"` | `phase4_schtasks_splunk.png` |
| Privilege Escalation Attempts (T1078) | 1 | `runas.exe`, `psexec.exe` | `index=win_logs EventCode=1 Image="*runas.exe" OR Image="*psexec.exe"` | `phase4_runas_splunk.png` |
| Suspicious Command Execution (T1059) | 1 | `powershell.exe`, `cmd.exe`, `wmic.exe` | `index=win_logs EventCode=1 Image="*powershell.exe" OR Image="*cmd.exe" OR Image="*wmic.exe"` | `phase4_powershell_splunk.png` |
| Network Connections (T1071) | 3 | `powershell.exe`, `cmd.exe` | `index=win_logs EventCode=3 Image="*powershell.exe" OR Image="*cmd.exe"` | `phase4_network_splunk.png` |
| Bonus: DNS Monitoring | 22 | `svchost.exe` querying domains | `index=win_logs EventCode=22 QueryName=*` | `phase4_dns_splunk.png` |

---

## ⚠️ Warnings & Reminders
- **Scheduled Task detections**: Registry changes may log (Event ID 13) even if process creation (Event ID 1) doesn’t appear. Validate both sides.  
- **Privilege escalation attempts**: `runas.exe` / `psexec.exe` may fail silently — always confirm in Event Viewer before assuming Splunk missed it.  
- **Network connections**: Event ID 3 requires explicit outbound activity (ping, Invoke‑WebRequest). Background DNS queries (Event ID 22) are not enough.  
- **Cross‑validation**: Always compare Splunk queries with Sysmon logs to avoid false assumptions.  

---


# 📸 Proof Screenshots – Phase 4

All detection proof screenshots for Phase 4 are stored in the dedicated folder:

👉 [Proof4 Screenshots](https://github.com/LetsLearn-08/soc-analyst-journey/tree/a3a74b75bff3d39ec6dbf5a31d52fb9c774c9164/proof4)

## 📌 Checklist
- [x] Registry Persistence
- [x] Scheduled Task Creation 
- [x] Suspicious Command Execution 
- [x] Privilege Escalation Attempts  
- [x] Network Connections 
- [x] Bonus DNS Monitoring 

---

📂 All screenshots are organized in the `proof/phase4` folder for easy navigation and recruiter‑ready documentation.

---

# 🌟 Reflection

By the end of Phase 4, I learned how **structured frameworks like MITRE ATT&CK enhance threat hunting**.  
- Mapping attacks to techniques provided clarity and standardization.  
- Queries allowed proactive detection of anomalies across logs.  
- Documentation strengthened detection workflows and made them reproducible.  

---

# 🔍 What I Learned
- **MITRE ATT&CK** provides a universal language for mapping threats.  
- **Threat hunting** is proactive, not reactive—it’s about searching for anomalies before alerts trigger.  
- **Splunk queries** can uncover hidden brute force, phishing, and malware attempts.  
- **Documentation** ensures repeatability and recruiter‑ready proof of skills.  

---

# 🚀 Next Steps
- Phase 5 → Implement **SIEM automation and threat intelligence feeds**.  
- Phase 6 → Build **SOC dashboards for executive reporting**.  
- Long‑term → Blend **threat hunting with pentesting awareness** for a complete defense strategy.  

---

# Hunting is not guessing — it’s proactive detection, structured mapping, and persistence.
## 📢 Stay Tuned
Follow my journey: **[@Lets Learn-08](https://github.com/LetsLearn-08)**
