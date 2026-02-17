# Sysmon Lab Setup – Beginner’s Manual

## 📖 Introduction
Sysmon (System Monitor) is a **Windows system monitoring tool** from Microsoft Sysinternals.  
It provides deep visibility into processes, network connections, and file changes — data that is critical for detecting attacker activity.  

In this lab, Sysmon helps you:
- Capture detailed forensic logs from the Windows VM
- Detect suspicious processes, registry changes, and network activity
- Forward logs into Splunk for centralized analysis
- Practice mapping detections to MITRE ATT&CK techniques

By mastering Sysmon, you demonstrate the **endpoint monitoring and detection engineering skills recruiters expect** from SOC analysts.

---

## 🎯 Why This Lab Matters
- Shows ability to configure endpoint monitoring beyond default Windows logs
- Provides visibility into attacker techniques like persistence, privilege escalation, and lateral movement
- Builds proof of detection rules mapped to MITRE ATT&CK

---

## 🏗️ Sysmon Components, Definitions, and Purpose

| Component | Definition | Purpose in Lab |
|-----------|------------|----------------|
| [Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon) | Windows system service and driver from Microsoft Sysinternals that logs detailed system activity. | Provides forensic visibility into suspicious activity missed by default Windows logs. |
| Sysmon Config File [(SwiftOnSecurity)](https://github.com/SwiftOnSecurity/sysmon-config) | XML ruleset defining what Sysmon logs. | Customizes detection to attacker behaviors and reduces noise. |
| [Event Viewer Integration](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon) | Sysmon logs appear under `Applications and Services Logs → Microsoft → Windows → Sysmon`. | Allows analysts to validate and review captured events. |
| Splunk Forwarder Stanza | Configuration in `inputs.conf` for Sysmon logs. | Ensures Sysmon telemetry is forwarded to Splunk for centralized analysis. |


---

## 🔑 Key Event IDs for SOC Analysts

### 🛠️ Sysmon Event IDs (High-Value)

| Event ID | Description | Why It Matters |
|----------|-------------|----------------|
| **1 – Process Creation** | Logs process creation with command line. | Detects suspicious executables, PowerShell abuse, malware launches. |
| **3 – Network Connection** | Logs TCP/UDP connections with source/destination IPs. | Identifies unusual outbound connections, C2 traffic, lateral movement. |
| **6 – Driver Loaded** | Logs kernel drivers loaded. | Detects rootkits or malicious drivers. |
| **7 – Image Loaded** | Logs DLLs/libraries loaded by processes. | Detects DLL injection or unsigned libraries. |
| **8 – CreateRemoteThread** | Logs threads created in another process. | Detects process injection techniques. |
| **10 – Process Access** | Logs when one process opens another with access rights. | Detects privilege escalation or credential theft. |
| **11 – File Create** | Logs file creation events. | Detects malware dropping payloads or persistence files. |
| **12 – Registry Object Create/Delete** | Logs registry key creation/deletion. | Detects persistence mechanisms or tampering. |
| **13 – Registry Value Set** | Logs registry value modifications. | Detects startup entries or altered security settings. |
| **15 – FileCreateStreamHash** | Logs creation of alternate data streams. | Detects hidden payloads or obfuscation. |
| **17 – Pipe Created** | Logs named pipe creation. | Detects malware IPC channels. |
| **18 – Pipe Connected** | Logs connections to named pipes. | Detects malware using pipes for C2/persistence. |
| **19 – WMI Event Filter** | Logs creation of WMI event filters. | Detects persistence via WMI subscriptions. |
| **20 – WMI Event Consumer** | Logs creation of WMI consumers. | Detects malicious WMI scripts. |
| **21 – WMI Event Binding** | Logs binding of filters to consumers. | Detects full WMI persistence setup. |
| **22 – DNS Query** | Logs DNS queries made by processes. | Detects suspicious domains, malware beaconing. |
| **23 – File Delete** | Logs file deletion events. | Detects attackers cleaning up artifacts. |

---

### 🛠️ Windows Security Event IDs (High-Value)

| Event ID | Description | Why It Matters |
|----------|-------------|----------------|
| **4624** | Successful logon. | Tracks valid user logins, useful for baselining. |
| **4625** | Failed logon. | Detects brute force attacks, password guessing, unauthorized access. |
| **4672** | Special privileges assigned to new logon. | Detects privilege escalation attempts. |
| **4688** | Process creation. | Detects suspicious executables or scripts (similar to Sysmon Event ID 1). |
| **4689** | Process termination. | Tracks process lifecycle, useful in correlation. |
| **4697** | Service installation. | Detects persistence via malicious services. |
| **4720** | User account creation. | Detects unauthorized account creation. |
| **4722** | User account enabled. | Detects re‑enabled disabled accounts. |
| **4723 / 4724** | Password change/reset. | Detects suspicious password changes. |
| **4768 / 4769 / 4776** | Kerberos and NTLM authentication events. | Detects pass‑the‑ticket or pass‑the‑hash attacks. |
| **4771** | Kerberos pre‑authentication failed. | Detects brute force or password spraying. |
| **5140** | A network share was accessed. | Detects lateral movement attempts. |
| **5156** | Windows Filtering Platform permitted a connection. | Detects suspicious outbound connections. |

---

### ✅ Why These Tables Matter
- **Sysmon IDs** → Deep forensic visibility (process, network, registry, WMI, DNS).  
- **Windows Security IDs** → Authentication, account management, and privilege events.  
- Together, they provide **full coverage** across endpoint and authentication telemetry, forming the backbone of SOC detection playbooks.


## ⚙️ Step‑by‑Step Setup

### Step 1: Install Sysmon
- **What:** Sysmon logs detailed system activity.  
- **How:**  
  1. Download Sysmon from [Microsoft Sysinternals](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon).  
  2. Use a config file (e.g., [SwiftOnSecurity Sysmon config](https://github.com/SwiftOnSecurity/sysmon-config)).  
  3. Run:  
     ```
     sysmon -accepteula -i sysmonconfig.xml
     ```
- **Why:** Without Sysmon, you miss critical forensic details like suspicious processes or network connections.

---

### Step 2: Validate Sysmon Events
- **What:** Check logs in Event Viewer under `Applications and Services Logs → Microsoft → Windows → Sysmon`.  
- **How:** Generate test activity (e.g., run PowerShell, open a suspicious file).  
- **Why:** Ensures Sysmon is capturing events correctly.

---

### Step 3: Forward Sysmon Logs to Splunk
- **What:** Splunk needs Sysmon logs for correlation.  
- **How:**  
  1. Configure Splunk Universal Forwarder to ingest Sysmon logs.  
  2. Add stanza in `inputs.conf`:  
     ```
     [WinEventLog://Microsoft-Windows-Sysmon/Operational]
     disabled = 0
     ```
- **Why:** Centralizes Sysmon data for SOC analysis.

---

## 🚨 Enhanced Detection Playbooks

| Incident Type | Sysmon Event | Detection (Splunk SPL) | Response | Purpose |
|---------------|--------------|-------------------------|----------|---------|
| **Suspicious Process Creation** | Event ID 1 | ```index=sysmon_logs EventID=1 | search Image="*powershell.exe*"``` | Investigate process, isolate host | Detects PowerShell abuse for malicious scripts. |
| **Unusual Network Connection** | Event ID 3 | ```index=sysmon_logs EventID=3 | stats count by DestinationIp``` | Block IP, alert SOC | Detects connections to suspicious external IPs. |
| **DLL Injection** | Event ID 7 | ```index=sysmon_logs EventID=7 | search ImageLoaded="*evil.dll*"``` | Terminate process, hunt IOCs | Detects malicious DLLs loaded into processes. |
| **Malware Dropping Files** | Event ID 11 | ```index=sysmon_logs EventID=11 | search TargetFilename="*temp\\malware.exe*"``` | Quarantine host, delete file | Detects malware writing files to disk. |
| **Persistence via Registry** | Event ID 13 | ```index=sysmon_logs EventID=13 | search TargetObject="HKCU\\Software\\Microsoft\\Windows\\CurrentVersion\\Run"``` | Remove registry key, alert SOC | Detects attackers adding persistence mechanisms. |
| **Privilege Escalation** | Event ID 10 | ```index=sysmon_logs EventID=10 | search GrantedAccess="0x1F3FFF"``` | Review account activity, restrict access | Detects suspicious access rights assignments. |

---

## 📚 Glossary of Sysmon Keywords

- **Sysmon** → [Microsoft Sysinternals Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)  
  Windows system service and driver that logs detailed system activity.  

- **Sysmon Config File** → [SwiftOnSecurity Sysmon Config](https://github.com/SwiftOnSecurity/sysmon-config)  
  XML ruleset that defines what Sysmon logs, helping reduce noise and focus on attacker behaviors.  

- **Event Viewer Integration** → [Sysmon Documentation](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)  
  Sysmon logs appear under `Applications and Services Logs → Microsoft → Windows → Sysmon`.  

- **Splunk Forwarder Stanza**  
  Custom configuration in `inputs.conf` that forwards Sysmon telemetry to Splunk for centralized analysis.  


---

## 🎯 Conclusion
Sysmon is the **eyes and ears of your Windows VM**.  
It captures detailed forensic logs that default Windows logging misses, making it essential for detecting attacker techniques.  

By documenting Sysmon events, forwarding them to Splunk, and building detection playbooks, you prove your ability to perform **endpoint monitoring and detection engineering** — critical skills for SOC analysts.

---

## 🤝 Connect With Me
- 🌐 GitHub: [LetsLearn-08](https://github.com/LetsLearn-08?tab=repositories)  
- 💼 LinkedIn: [Tanuja Reddy](https://www.linkedin.com/in/tanuja-reddy-03aa7b38a)
