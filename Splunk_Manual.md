# Splunk Lab Setup – Beginner’s Manual


## 📖 Introduction 
Splunk Enterprise is one of the most widely used **SIEM (Security Information and Event Management)** platforms in the industry.
It acts as the **central nervous system of a SOC**, collecting logs from endpoints, servers, and network devices, then correlating them to detect suspicious activity.
In this lab, Splunk helps you:
- Ingest logs from Windows, Linux, and network sources
- Build dashboards that visualize attacker vs. defender activity
- Create correlation searches that automatically detect incidents
- Practice responding to real-world attack scenarios in a safe environment By mastering Splunk, you demonstrate the
  **core SOC analyst skillset recruiters look for**: log analysis, detection engineering, and incident response.

---

## 🎯 Why This Lab Matters
- Demonstrates ability to configure and operate a SIEM recruiters expect SOC analysts to know
- Shows practical skills in log ingestion, correlation, and alerting
- Provides proof of Splunk dashboards and detection rules

---

## 🏗️ Splunk Components, Definitions, and Purpose

| Keyword / Tool | Definition | Purpose in Lab |
|----------------|------------|----------------|
| [Splunk Enterprise](https://www.splunk.com/) | SIEM platform for log ingestion, correlation, and incident detection. | Acts as the SOC’s central dashboard. |
| [Splunk Universal Forwarder](https://docs.splunk.com/Documentation/Forwarder) | Lightweight agent installed on endpoints. | Sends logs from VMs to Splunk Enterprise. |
| [Index](https://docs.splunk.com/Documentation/Splunk/latest/Indexer/Aboutindexes) | Logical data store in Splunk. | Organizes ingested logs for searching. |
| [Search Head](https://docs.splunk.com/Documentation/Splunk/latest/Search/Aboutsearchheads) | Splunk component for running queries and dashboards. | Allows analysts to query logs and visualize data. |
| [Correlation Search](https://docs.splunk.com/Documentation/ES/latest/Admin/CorrelationSearches) | Saved search that detects suspicious patterns. | Automates detection of incidents. |

---

## ⚙️ Step‑by‑Step Setup

### Step 1: Install Splunk Enterprise
- **What:** Splunk ingests and analyzes logs.  
- **How:**  
  1. Download Splunk Enterprise from [Splunk official site](https://www.splunk.com/).  
  2. Install on your SIEM VM.  
  3. Enable **receiver port** (default: 9997).  
  4. Validate with:  
     ```
     netstat -an | grep 9997
     ```
- **Why:** Splunk is your central dashboard for incident detection.

---

### Step 2: Configure Indexes
- **What:** Indexes store logs.  
- **How:** Create indexes for Windows, Linux, and network logs.  
- **Why:** Organizes data for efficient searching.

---

### Step 3: Install Splunk Universal Forwarder
- **What:** Forwarder sends logs to Splunk.  
- **How:**  
  1. Install on Windows/Linux VMs.  
  2. Configure `outputs.conf` to point to Splunk SIEM IP and port.  
  3. Validate with:  
     ```
     splunk list forward-server
     ```
- **Why:** Without forwarding, Splunk won’t receive endpoint logs.

---

### Step 4: Build Dashboards
- **What:** Dashboards visualize logs.  
- **How:** Use Splunk’s Search Head to create panels for login attempts, process creation, and network traffic.  
- **Why:** Dashboards help analysts quickly spot anomalies.

---

### Step 5: Create Correlation Searches
- **What:** Saved searches detect suspicious activity.  
- **How:**  
  - Example: Detect multiple failed logins in 1 minute.  
  - SPL query:  
    ```
    index=windows_logs sourcetype=WinEventLog:Security EventCode=4625
    | stats count by Account_Name
    | where count > 5
    ```
- **Why:** Automates detection of brute force attacks.

---

## 🚨 Enhanced Detection Playbooks

| Incident Type | Detection (Splunk SPL) | Response | Purpose |
|---------------|-------------------------|----------|---------|
| **Brute Force Login** | ```index=windows_logs EventCode=4625 | stats count by Account_Name | where count>5``` | Lock account, alert SOC team | Detects repeated failed login attempts that indicate password guessing. |
| **Suspicious PowerShell Usage** | ```index=sysmon_logs EventID=1 | search Image="*powershell.exe*"``` | Investigate process, isolate host | Identifies potential abuse of PowerShell for malicious scripts. |
| **Port Scan / Reconnaissance** | ```index=network_logs sourcetype=nmap | stats count by src_ip dest_port``` | Block IP, raise alert | Detects attacker reconnaissance before exploitation. |
| **Malware Execution** | ```index=sysmon_logs EventID=1 | search Image="*malware.exe*"``` | Quarantine host, hunt IOCs | Detects suspicious executables launched on endpoints. |
| **Privilege Escalation** | ```index=windows_logs EventCode=4672 | stats count by Account_Name``` | Review account activity, restrict access | Detects assignment of special privileges to accounts. |
| **Data Exfiltration** | ```index=network_logs | stats sum(bytes) by src_ip dest_ip | where sum(bytes)>10000000``` | Block outbound connection, investigate | Detects unusually large outbound data transfers. |

---

## 📚 Glossary of Keywords
- [Splunk Enterprise](https://www.splunk.com/) → [Splunk Manual](Splunk_Manual.md)  
- [Splunk Universal Forwarder](https://docs.splunk.com/Documentation/Forwarder)  
- [Index](https://docs.splunk.com/Documentation/Splunk/latest/Indexer/Aboutindexes)  
- [Search Head](https://docs.splunk.com/Documentation/Splunk/latest/Search/Aboutsearchheads)  
- [Correlation Search](https://docs.splunk.com/Documentation/ES/latest/Admin/CorrelationSearches)  

---

## 🎯 Conclusion
Splunk is the **heart of your SOC lab**.  
It ingests logs, correlates events, and raises alerts — giving defenders visibility into attacks.  

By documenting dashboards, correlation searches, and playbooks, you prove your ability to operate a SIEM recruiters expect SOC analysts to master.

---

## 🤝 Connect With Me
- 🌐 GitHub: [LetsLearn-08](https://github.com/LetsLearn-08?tab=repositories)  
- 💼 LinkedIn: [Tanuja Reddy](https://www.linkedin.com/in/tanuja-reddy-03aa7b38a)
