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

# 📂 Phase 3 – Attack Simulations Proof

This section documents three key attack scenarios captured in the SOC lab. Each link points to supporting screenshots and documentation (to be attached later).

---

## 1. Phishing Simulation
**Description:** A phishing email was drafted in Thunderbird. Clicking the malicious link triggered Edge (`msedge.exe`) as a child process. Sysmon Event ID 1 captured this chain, and Splunk confirmed ingestion.  

[📎 View Phishing Simulation Proof](proof/phishing_simulation.md)

---

## 2. Brute Force Attack
**Description:** Multiple failed login attempts were simulated against the Windows VM. Sysmon and Security logs captured Event IDs for authentication failures, and Splunk searches validated detection of brute force behavior.  

[📎 View Brute Force Proof](proof/bruteforce_attack.md)

---

## 3. Malware Execution (EICAR Test File)
**Description:** The EICAR test file was executed to simulate malware activity. Sysmon logged file creation and process execution events, while Splunk queries confirmed detection and correlation.  

[📎 View Malware Simulation Proof](proof/malware_execution.md)

---

## ✅ Narrative
These three scenarios demonstrate end‑to‑end detection capabilities in the SOC lab:
- **Phishing:** Thunderbird → Edge process chain.  
- **Brute Force:** Authentication failures logged and correlated.  
- **Malware:** EICAR execution detected and ingested.  

Together, they showcase how Sysmon and Splunk provide visibility into diverse attack techniques.

---

# 🖼️ Screenshots Checklist – SOC Lab Phase 3

## 📌 Phishing
- [ ] Detection logs  
- [ ] Splunk dashboard screenshot  

## 🔐 Brute Force
- [ ] Detection logs  
- [ ] Correlation rule screenshot  

## 🦠 Malware (EICAR)
- [ ] Detection logs  
- [ ] AV alert screenshot  
- [ ] Splunk dashboard screenshot  

## 📑 Incident Reports
- [ ] Phishing incident report with screenshots  
- [ ] Brute force incident report with screenshots  
- [ ] Malware incident report with screenshots  

---

# 🌟 Reflection

By the end of Phase 3, I learned how to **translate detections into actionable playbooks**.  
- Phishing simulations showed the importance of quick isolation.  
- Brute force attempts highlighted the need for correlation rules.  
- Malware detection reinforced containment and eradication workflows.  

This phase taught me how to **document escalation paths clearly** and standardize incident response.  

---

# 🔍 What I Learned
- **Phishing detection** requires quick identification and isolation.  
- **Brute force detection** benefits from correlation rules to reduce noise.  
- **Malware detection** emphasizes containment and eradication steps.  
- **Playbooks** provide clarity and reproducibility for SOC workflows.  
- **Incident reports** strengthen communication between Tier‑1 and Tier‑2 analysts.  

---

# 🚀 Next Steps
- Phase 4 → Map detections to **MITRE ATT&CK techniques**.  
- Phase 5 → Implement **SIEM automation and threat intelligence feeds**.  
- Long‑term → Blend SOC playbooks with **pentesting awareness** for a complete defense strategy.  

---

# Detection is not guessing — it’s structured response, clarity, and persistence.
## 📢 Stay Tuned
Follow my journey: **[@Lets Learn-08](https://github.com/LetsLearn-08)**
