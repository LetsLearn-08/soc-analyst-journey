# 📅 Phase 2 Timeline – SOC Lab Journey

## 📅 Timeline

### Day 16–18: Windows Log Analysis
- Collected **Windows Event Logs** (Security, Sysmon).  
- Focused on **failed logins** (EventCode 4625), **privilege escalation attempts** (EventCode 4672), and **PowerShell abuse** (EventCode 4104).  
- Verified ingestion into Splunk dashboards.  

---

### Day 19–21: Linux Log Analysis
- Configured **syslog forwarding** from Ubuntu/Kali.  
- Detected **SSH brute force attempts** (auth.log failures).  
- Identified **sudo misuse** and **cron job anomalies**.  
- Built Splunk queries for Linux authentication events.  

---

### Day 22–24: Firewall Log Analysis
- Forwarded firewall logs into Splunk.  
- Detected **Nmap scans** and suspicious inbound traffic.  
- Created dashboards for **port scan detection** and **brute force traffic patterns**.  

---

### Day 25–27: Incident Report Writing
- Drafted **incident reports** for Windows, Linux, and Firewall detections.  
- Standardized format: Summary → Logs → Detection → Response → Lessons Learned.  
- Stored reports in `/docs/Phase2_Log_Analysis.md`.  

---

### Day 28–30: Validation & Review
- Simulated brute force attacks from Kali against Windows/Linux.  
- Observed detections in Splunk dashboards.  
- Finalized **3–5 incident reports** with screenshots.  

---

# 🖼️ Screenshots Checklist – SOC Lab Phase 2

All Phase 2 screenshots are stored in the -------- folder.

## 📌 Windows Logs
- [ ] Failed login detection (EventCode 4625)  
- [ ] Privilege escalation detection (EventCode 4672)  
- [ ] PowerShell abuse detection (EventCode 4104)  
- [ ] Splunk dashboard screenshot  

## 🐧 Linux Logs
- [ ] SSH brute force detection (auth.log)  
- [ ] Sudo misuse detection  
- [ ] Cron job anomaly detection  
- [ ] Splunk dashboard screenshot  

## 🔥 Firewall Logs
- [ ] Nmap scan detection  
- [ ] Suspicious traffic dashboard  
- [ ] Brute force traffic detection  

## 📑 Incident Reports
- [ ] Windows incident report with screenshots  
- [ ] Linux incident report with screenshots  
- [ ] Firewall incident report with screenshots  

---

# 🌟 Reflection

By the end of Phase 2, I learned that **logs are the lifeblood of detection**.  
- Windows logs revealed privilege misuse and PowerShell abuse.  
- Linux logs showed brute force attempts and misconfigurations.  
- Firewall logs highlighted external threats like scans and brute force traffic.  

This phase taught me how to **connect raw logs to meaningful incidents** and document them clearly for escalation.  

---

# 🔍 What I Learned
- **Windows Event Logs** are critical for detecting privilege escalation and PowerShell misuse.  
- **Linux syslogs** provide visibility into brute force and misuse of sudo/cron.  
- **Firewall logs** help spot external reconnaissance and brute force traffic.  
- **Incident reporting** is about clarity: what happened, how it was detected, and what was done.  
- **Patterns matter**: isolated events may be noise, but repeated anomalies signal attacks.  
- **Documentation builds credibility**: screenshots + reports = proof of detection skills.  

---

# 🚀 Next Steps
- Phase 3 → Build **incident response playbooks** for phishing, brute force, and malware.  
- Phase 4 → Map detections to **MITRE ATT&CK techniques**.  
- Long-term → Automate detection workflows with correlation rules and threat intel feeds.  

---

# Detection is not guessing — it’s pattern recognition, discipline, and persistence.

## 📢 Stay Tuned
Follow my journey: **[@Lets Learn-08](https://github.com/LetsLearn-08)**
