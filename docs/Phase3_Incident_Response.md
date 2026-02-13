# 📅 SOC Journey – Phase 3: Incident Response Playbooks

## 📅 Timeline

### Day 31–33: Phishing Simulation
- Simulated **phishing emails** using Thunderbird with malicious attachments/links.  
- Forwarded logs into Splunk for detection.  
- Built queries to identify suspicious email activity.  
- Documented **Tier‑1 SOC analyst steps**: identify, isolate, escalate.  

---

### Day 34–36: Brute Force Attack Simulation
- Simulated **SSH and RDP brute force attempts** from Kali Linux.  
- Detected repeated failed login attempts in Windows logs.  
- Configured **correlation rules** in Splunk for brute force detection.  
- Documented **Tier‑1 → Tier‑2 escalation workflow**.  

---

### Day 37–39: Malware (EICAR) Simulation
- Deployed **EICAR test malware** on Windows VM.  
- Observed **AV alerts** and log ingestion into Splunk.  
- Built dashboards for **malware detection and response**.  
- Documented **containment and eradication steps**.  

---

### Day 40–42: Playbook Development
- Wrote **step‑by‑step playbooks** for phishing, brute force, and malware.  
- Standardized format: Summary → Logs → Detection → Response → Lessons Learned.  
- Stored playbooks in `/docs/Phase3_Incident_Response.md`.  

---

### Day 43–45: Incident Response Reports
- Drafted **incident reports** for each simulated attack.  
- Linked screenshots from proof folder.  
- Validated **escalation paths** with workflow diagrams.  

---

## 🔗 Phase 3 Manual
You can view the Incident Response Lab manual here:  
[Incident Response Lab Manual](https://github.com/LetsLearn-08/soc-analyst-journey/blob/65a5a7e6162972ff88a3df76c9a9741cea20b884/INCIDENT-RESPOND-LABSETUP-MANUAL.md)


---


## 📂 Attack Simulations

### 🔹 Phishing Simulation
**Description:**  
A simulated [phishing attack](https://en.wikipedia.org/wiki/Phishing) was conducted using Thunderbird to send malicious emails with attachments and links. Clicking the malicious link triggered [Microsoft Edge](https://en.wikipedia.org/wiki/Microsoft_Edge) (`msedge.exe`) as a child process.

📎 [Read Full Documentation → phishing_simulation.md](proof/phishing_simulation.md)

---

### 🔹 Brute Force Attack
**Description:**  
Simulated [brute-force attack](https://en.wikipedia.org/wiki/Brute-force_attack) attempts were performed against [SSH](https://en.wikipedia.org/wiki/Secure_Shell) and [RDP](https://en.wikipedia.org/wiki/Remote_Desktop_Protocol) services from Kali Linux.

📎 [Read Full Documentation → bruteforce_attack.md](proof/bruteforce_attack.md)

---

### 🔹 Malware Execution (EICAR Test File)
**Description:**  
The [EICAR test file](https://en.wikipedia.org/wiki/EICAR_test_file) was deployed using `curl.exe` to simulate malware activity.

📎 [Read Full Documentation → malware_execution.md](proof/malware_execution.md)

---

## 📑 Incident Response Playbooks
Each attack scenario was documented in a standardized format:

**Format:**  
- **Summary** → Attack description  
- **Logs** → Sysmon + Splunk evidence  
- **Detection** → Queries and dashboards  
- **Response** → Containment, eradication, escalation  
- **Lessons Learned** → Improvements for SOC workflow  

Stored in: `/docs/Phase3_Incident_Response.md`


---
## 📊 Phase 3 Learnings & Troubleshooting Issues

| **Category**            | **Key Learnings**                                                                 | **Common Troubleshooting Issues**                                                                 |
|--------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| **Phishing Simulation**  | Quick isolation and escalation are critical when malicious emails are detected.   | Email logs not forwarding correctly, Splunk queries missing child process correlation (e.g., msedge.exe). |
| **Brute Force Detection**| Correlation rules reduce noise and highlight true brute force attempts.           | Splunk correlation searches misconfigured, thresholds too low/high, failed login events not ingested. |
| **Malware Simulation**   | Containment and eradication steps must be documented clearly.                     | EICAR file not triggering AV alerts, Splunk dashboards missing malware fields, ingestion delays.   |
| **Playbook Development** | Standardized playbooks ensure reproducibility and clarity across SOC tiers.       | Inconsistent formatting, missing escalation steps, unclear response actions in early drafts.       |
| **Incident Reporting**   | Reports strengthen communication between Tier‑1 and Tier‑2 analysts.              | Screenshots not linked properly, broken file paths in proof folder, inconsistent report structure. |
| **Validation**           | Simulated attacks confirm both detection and response workflows.                  | Attack simulations not generating logs, timing mismatches between attack execution and log ingestion. |
| **Documentation**        | Clear playbooks + incident reports = professional SOC workflow.                   | README links breaking, proof folder not consistently organized, duplicate or mislabeled screenshots. |

---

## 🖼️ Proof – SOC Lab Phase 3
All Phase 3 screenshots are stored in the [proof3 folder](https://github.com/LetsLearn-08/soc-analyst-journey/tree/74554db12e84a85240ed5752d68f0d53d7801ec4/proof3).

---

## 🌟 Reflection

Phase 3 taught me how to **move from detection to structured response**.  
By simulating phishing, brute force, and malware incidents, I learned that detection alone isn’t enough — analysts must have clear playbooks and escalation paths.

### Key Insights
- **Phishing simulations** → reinforced the importance of quick isolation and escalation.  
- **Brute force attempts** → showed the value of correlation rules to reduce noise and highlight true attacks.  
- **Malware detection (EICAR)** → emphasized containment, eradication, and communication across SOC tiers.  

### Achievements
- ✅ Developed incident response playbooks for phishing, brute force, and malware.  
- ✅ Standardized reporting format (Summary → Logs → Detection → Response → Lessons Learned).  
- ✅ Validated escalation workflows with diagrams and screenshots.  

### Growth Mindset
- **Response is structured** → playbooks ensure clarity and reproducibility.  
- **Communication matters** → incident reports strengthen Tier‑1 to Tier‑2 handoffs.  
- **Persistence pays off** → repeated simulations confirmed detection and response workflows.  

This phase elevated my SOC journey from **log analysis → incident response**, proving that analysts must combine technical detection with disciplined response strategies.

---

# 🔍 What I Learned
- **Phishing detection** requires quick identification and isolation.  
- **Brute force detection** benefits from correlation rules to reduce noise.  
- **Malware detection** emphasizes containment and eradication steps.  
- **Playbooks** provide clarity and reproducibility for SOC workflows.  
- **Incident reports** strengthen communication between Tier‑1 and Tier‑2 analysts.  

---

## 🚀 Next Steps

- **[Phase 4](https://github.com/LetsLearn-08/soc-analyst-journey/blob/74554db12e84a85240ed5752d68f0d53d7801ec4/docs/Phase4_Threat_Hunting.md) → MITRE ATT&CK Mapping & Advanced Detection**  
  Map detections from Windows, Linux, and Firewall logs to MITRE ATT&CK techniques.  
  Focus: Align Sysmon and Splunk queries with ATT&CK tactics (Persistence, Privilege Escalation, Defense Evasion).  
  Goal: Build recruiter‑ready proof with ATT&CK‑aligned documentation and screenshots.  

- **[Phase 5](https://github.com/LetsLearn-08/soc-analyst-journey/blob/74554db12e84a85240ed5752d68f0d53d7801ec4/docs/Phase5_Advanced_SOC.md) → SIEM Automation & Threat Intelligence Feeds**  
  Implement automated correlation rules and integrate external threat intelligence feeds.  
  Focus: Reduce manual effort by automating detection workflows and enriching alerts with IP/domain reputation data.  
  Goal: Showcase advanced SOC engineering and proactive defense capabilities.  

- **Post‑Phase 5 → Unique SOC Analyst Projects**  
  Redo all projects with advanced angles:  
  - Custom dashboards & attack storytelling  
  - Automation scripts for reproducible detections  
  - Threat intel enrichment  
  - SOC playbooks with workflow diagrams  
  - Beginner’s guide for community sharing  
  Goal: Transform the SOC lab into a professional portfolio that stands out from standard projects.  

- **Long‑term Vision → Complete Defense Strategy**  
  Blend SOC playbooks with pentesting awareness to build a holistic defense platform.  
  Goal: Enable learners and recruiters to explore cybersecurity labs paired with creative storytelling.


---

# Detection is not guessing — it’s structured response, clarity, and persistence.
## 📢 Stay Tuned
Follow my journey: **[@Lets Learn-08](https://github.com/LetsLearn-08)**
