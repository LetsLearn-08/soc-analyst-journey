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

# 🖼️  Checklist – SOC Lab Phase 2

## 📑 Phase 2 Incident Reports
- [Firewall Analysis – Port Scan Detection](firewall_report.md)
- [Logon Correlation – Failed + Successful Attempts](logon_report.md)
- [DNS Query Monitoring – Suspicious Domain Access](dns_report.md)

---

## 📸 Screenshots Proofs
All Phase 2 screenshots are stored in the proof2 folder:  
[View on GitHub](https://github.com/LetsLearn-08/soc-analyst-journey/tree/73e6d44fbefb5db38ad618bad571b7079001b7f3/proof2)


---

## 📊 Phase 2 Learnings & Troubleshooting Issues

| **Category**         | **Key Learnings**                                                                 | **Common Troubleshooting Issues**                                                                 |
|-----------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| **Windows Logs**      | Event IDs (4625, 4672, 4104) reveal failed logins, privilege misuse, and PowerShell abuse. | Misconfigured audit policies, missing Sysmon rules, Splunk not parsing PowerShell logs correctly. |
| **Linux Logs**        | Syslogs highlight SSH brute force, sudo misuse, and cron anomalies.               | Forwarder misconfigurations, missing auth.log ingestion, incorrect Splunk query syntax.           |
| **Firewall Logs**     | Firewall telemetry detects Nmap scans and brute force traffic patterns.           | Logs not forwarded properly, dashboards failing due to missing fields, noisy traffic overwhelming queries. |
| **Splunk Dashboards** | Dashboards transform raw logs into clear detection patterns.                      | Incorrect field extractions, dashboards not updating, queries too broad or too narrow.            |
| **Incident Reports**  | Standardized format (Summary → Logs → Detection → Response → Lessons Learned) builds credibility. | Forgetting screenshots, inconsistent formatting, missing correlation between log sources.         |
| **Validation**        | Simulated attacks confirm detections across Windows, Linux, and Firewall.         | Attack simulations not triggering logs, timing mismatches between attack and ingestion.            |
| **Documentation**     | Reports + screenshots = proof of detection skills and professional workflow.      | Broken README links, inconsistent file naming in `proof2` folder.                                 |
---

# 🌟 Reflection


Phase 2 reinforced that **logs are the lifeblood of detection**. By analyzing Windows, Linux, and Firewall telemetry, I learned how to transform raw events into meaningful incidents and document them for escalation.

### Key Insights
- **Windows Logs** → revealed privilege misuse and PowerShell abuse.  
- **Linux Logs** → exposed brute force attempts and misconfigurations.  
- **Firewall Logs** → highlighted external threats like scans and brute force traffic.  

### Achievements
- ✅ Built Splunk queries and dashboards for multi‑platform log sources.  
- ✅ Standardized incident report format (Summary → Logs → Detection → Response → Lessons Learned).  
- ✅ Captured screenshots and reports as proof of detection skills.  

### Growth Mindset
- **Patterns matter** → isolated events may be noise, but repeated anomalies signal attacks.  
- **Incident reporting builds credibility** → clear documentation shows professional workflow.  
- **Validation is critical** → simulated attacks confirmed detections across all systems.  

This phase taught me how to **connect raw logs to actionable incidents** and communicate findings clearly — a skill every SOC analyst must master.

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
- **Phase 3 → Incident Response Playbooks & Automation**
   - Develop structured playbooks for common attack scenarios (phishing, brute force, malware).
   -  Focus: Automate attack simulations and detection workflows to ensure reproducibility.
   -   Goal: Demonstrate how automation and playbooks reduce manual effort and strengthen SOC operations. 
- **Phase 4 → MITRE ATT&CK Mapping & Advanced Detection**
   -  Map detections to ATT&CK techniques and expand Splunk queries for persistence and privilege escalation.
   - Focus: Build recruiter‑ready proof with screenshots and ATT&CK‑aligned documentation.
   - Goal: Showcase advanced detection engineering and correlation capabilities.
 - **Long-term → Community Cybersecurity Platform**
   - Consolidate all phases into a reproducible lab environment.
   - Goal: Enable learners and recruiters to explore cybersecurity labs paired with creative storytelling. 

---

# Detection is not guessing — it’s pattern recognition, discipline, and persistence.

## 📢 Stay Tuned
Follow my journey: **[@Lets Learn-08](https://github.com/LetsLearn-08)**
