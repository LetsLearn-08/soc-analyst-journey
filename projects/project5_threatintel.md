# Project 5: Threat Intelligence Integration with MISP

## 🎯 Purpose
The purpose of this project is to demonstrate how a SOC team can **collect, structure, enrich, and operationalize threat intelligence** using MISP (Malware Information Sharing Platform & Threat Sharing).  
By simulating a real attack scenario, the project shows how indicators of compromise (IOCs) are documented, correlated, and shared to strengthen defensive capabilities.

---

## 📖 Story: The SOC Team vs. The Phantom Payload
It was a quiet afternoon in the SOC when the monitoring dashboard lit up with unusual outbound traffic.  
Analyst **Tanuja** noticed repeated connections to a suspicious domain: `evil-example.com`. At the same time, **Raghu**, the malware specialist, captured a file hash (`44d88612fea8a8f36de82e1278abb02f`) that matched known ransomware samples.  

The team quickly realized they were facing a **coordinated phishing campaign** delivering a malicious payload via a download link:  
`http://malicious-download.com/payload.exe`.  

To ensure the organisation could defend against this threat in the future, **Sivangi**, the threat intelligence lead, documented all findings in **MISP**.  
She created **Event #1**, populated it with the domain, URL, IP address (`203.0.113.45`), and file hashes, and shared it across the SOC.  

This way, the team transformed raw detection into **structured intelligence** — ready to be correlated, automated, and acted upon.
---

## 🛠️ Environment Setup
- **Platform**: Ubuntu Server (SIEM VM)  
- **Tools Installed**: MISP, MariaDB, Apache  
- **User**: `admin@admin.test`  
- **Organisation**: `SOC_Project_Demo`  

### Screenshots
![MISP Interface](Project5/misp-interface.png)  
*First login to the MISP web interface*

![Ownership Fix](Project5/misp-ownership.png)  
*Adjusted file ownership for MISP directories*

---

## 📂 Event Creation
Created **Event #1** with the following metadata:
- **Date**: 2026‑03‑20  
- **Distribution**: Your Organisation Only  
- **Threat Level**: Medium  
- **Analysis**: Initial  
- **Event Info**: SOC Demo Event  

### Screenshots
![Threat Intel Demo Event](Project5/threat-intel-demo-event.png)  
*Demo event created with attributes*

![MISP Attributes](Project5/misp-attributes.png)  
*Indicators of compromise (IOCs) added to the event*

![MISP Tables](Project5/misp-tables.png)  
*Database tables populated after event creation*


---

## 🔎 Attribute Population
Indicators added to Event #1:

| Type   | Value                                      | Context                          |
|--------|---------------------------------------------|----------------------------------|
| SHA256 | `275a021bbfb6480f1a51f9e6d5857f5d76b9f7a2c3d5f9d3c7f6a6` | Malware payload hash |
| MD5    | `44d88612fea8a8f36de82e1278abb02f`          | Known ransomware sample          |
| Domain | `evil-example.com`                          | Phishing infrastructure          |
| URL    | `http://malicious-download.com/payload.exe` | Malware delivery link            |
| IP     | `203.0.113.45`                              | Command & Control server         |


## 📑 Attribute Documentation
### Screenshots
![MISP Attributes](Project5/misp-attributes.png)  
*IOC entry form showing domains, IPs, and hashes*

![Threat Intel Demo Event](Project5/threat-intel-demo-event.png)  
*Event view showing all IOCs added to the demo event*

---
# 📑 Proof of Artifacts

## ⚙️ MISP Installation & Configuration
### Screenshots
![Clone GitHub MISP](Project5/clone-github-misp.png)  
*MISP cloned from GitHub repository*

![MISP Core Dependencies](Project5/misp-core-dependencies.png)  
*Installed core dependencies for MISP*

![MISP Configuration](Project5/misp-conf.png)  
*Configuration file updated for MISP*

![MISP Interface](Project5/misp-interface.png)  
*First login to the MISP web interface*


---

## 🔗 Worker & API Integration
### Screenshots
![Worker Starting](Project5/worker-starting.png)  
*Background worker initiated for scheduled tasks*

![Redis Server Installation](Project5/redis-server-installation.png)  
*Redis server installed to support background jobs*

![MISP Logs](Project5/misp-logs.png)  
*Log output confirming successful worker execution*

### 🧩 Supporting Configuration & Troubleshooting
Additional screenshots (terminal commands, configuration edits, service checks, CakePHP setup, worker status, dependency fixes) are included to demonstrate the **struggle and persistence** behind the clean final output.


---

## 🔗 API Integration
To validate that indicators are accessible programmatically, the SOC team used the **MISP REST API**.  
By authenticating with the admin user’s API key, they retrieved Event #1 and its attributes in JSON format.

Example command:
```bash
curl -H "Authorization: <API_KEY>" \
     -H "Accept: application/json" \
     -H "Content-Type: application/json" \
     http://192.168.56.102/events/view/8649c645-ef20-428f-bd18-73507be00b29
```

## 📚 Key Learnings

- Threat intelligence must be structured: Raw IOCs are only useful when documented in a platform like MISP.
- Collaboration is critical: Multiple SOC roles (analyst, malware specialist, threat intel lead) worked together to capture and contextualize the threat.
- Automation enhances scalability: API integration ensures indicators can be shared with SIEMs, SOAR platforms, and other tools without manual effort.
- Proof artifacts matter: Screenshots and documentation provide examiner‑ready evidence of the workflow.
- Operationalization is the end goal: Intelligence is most valuable when it feeds into detection and response systems.

---

## 🤝 Connect with Me

I’m always excited to share knowledge, collaborate on cybersecurity projects, and explore new opportunities in SOC analysis, threat intelligence, and security automation.  
If you’d like to connect, discuss my work, or explore potential collaborations, here are my profiles:

- 🌐 **GitHub**: [LetsLearn-08](https://github.com/LetsLearn-08?tab=repositories)  
- 💼 **LinkedIn**: [Tanuja Reddy](https://www.linkedin.com/in/tanuja-reddy-03aa7b38a)  

Feel free to reach out — let’s learn, build, and secure together!

