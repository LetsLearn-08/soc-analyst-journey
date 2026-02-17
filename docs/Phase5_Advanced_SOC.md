# 📅 Phase 5 – IOC Enrichment + Advanced SOC & Pentesting Prep

## 🎯 Objective
Strengthen SOC detection and expand into pentesting awareness by:
- Integrating **threat intelligence feeds** (AlienVault OTX, AbuseIPDB).  
- Automating **SIEM alerts** for suspicious activity.  
- Validating detections through **pentesting basics** (Nmap, Nessus, exploitation labs).  
- Documenting workflows and proof screenshots for recruiter‑ready visibility.

---

## 🛠️ Tools Used
- **Sysmon** → Hash logging for process creation and image loads.  
- **Splunk** → Ingestion, correlation searches, dashboards, and alert automation.  
- **AlienVault OTX & AbuseIPDB** → IOC feeds for malicious IPs/domains and file hashes.  
- **Nmap & Nessus** → Vulnerability scanning and pentesting validation.  

---

## 📅 Timeline

### Day 61–64: SIEM Automation
- Configured **automated alerts** for failed logins, suspicious PowerShell activity, and malware detections.  
- Built **correlation rules** combining multiple weak signals into strong detections.  
- Validated automation workflows in Splunk dashboards.  

### Day 65–68: Threat Intelligence Integration
- Integrated **AlienVault OTX** (hashes) and **AbuseIPDB** (IPs/domains) into Splunk.  
- Configured alerts for known malicious indicators.  
- Documented feed ingestion and correlation queries.  

### Day 69–72: Pentesting Basics
- Conducted **Nmap scans** and **Nessus vulnerability assessments**.  
- Linked findings back to SOC detections.  
- Explored exploitation labs to validate SOC monitoring workflows.  

### Day 73–75: Reports & Documentation
- Compiled **alert rules** and **vulnerability assessment reports**.  
- Stored documentation in `/docs/Phase5_Advanced_SOC.md`.  
- Linked proof screenshots for automation, threat intel, and pentesting.  

---

## 🖼️ Screenshots Checklist

### ⚙️ SIEM Automation
- [ ] Correlation rule screenshot  
- [ ] Splunk dashboard showing automated alerts  

### 🌐 Threat Intelligence
- [ ] IOC feed integration screenshot  
- [ ] Alert triggered by malicious IP/domain/hash  

### 🛠️ Pentesting
- [ ] Nmap scan results screenshot  
- [ ] Nessus vulnerability report screenshot  
- [ ] Exploitation lab proof screenshot  

### 📑 Reports
- [ ] Alert rules report with screenshots  
- [ ] Vulnerability assessment report with screenshots  

---

## 📊 Detection Coverage (MITRE ATT&CK Mapping)
- **Event ID 1 (ProcessCreate)** → T1059 (Command Execution)  
- **Event ID 7 (ImageLoad)** → T1073 (DLL Injection)  
- **Event ID 11 (FileCreate)** → T1070 (Indicator Removal on Host)  
- **Event ID 22 (DNS Query)** → T1071 (Application Layer Protocol)  

---

## 🌟 Reflection
By the end of Phase 5, I connected **SOC detection with pentesting awareness**:  
- **Automation** reduced analyst workload and improved response speed.  
- **Threat intelligence feeds** enriched alerts with context.  
- **Pentesting** validated SOC detections and highlighted real attack paths.  
- **Documentation** ensured reproducibility and recruiter‑ready proof of skills.  

---

## ✅ Outcome
Phase 5 demonstrated a **complete SOC workflow**:  
- Sysmon hash logging → Splunk ingestion → IOC correlation → Automated alerts.  
- Threat intel feeds integrated for malicious IPs/domains.  
- Pentesting validated detections.  
- Reports and screenshots documented for recruiter visibility.  

---

## 🔍 What I Learned
- **Correlation rules** combine multiple weak signals into strong detections.  
- **Threat intel feeds** provide context and enrich alerts.  
- **Pentesting** bridges offensive and defensive security, validating SOC workflows.  
- **Documentation** ensures reproducibility and recruiter‑ready proof of skills.  

---

# Defense is strongest when automation, intelligence, and validation work together.
## 📢 Stay Tuned
Follow my journey: **[@Lets Learn-08](https://github.com/LetsLearn-08)**
