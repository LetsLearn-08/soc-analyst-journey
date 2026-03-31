# Windows Defender Manual 

## 📖 Introduction
This manual explains how to configure and use **Microsoft Defender Antivirus (Windows Defender)** in your Incident Response Lab.  
It provides **endpoint protection** against malware, phishing, and suspicious activity.  

By the end, you will:
- Understand how Defender works as a built‑in security tool  
- Learn how to configure logging and alerts  
- Practice detecting and responding to threats using Defender  

---

## 🎯 Why This Manual Matters
- Shows recruiters you can configure **native endpoint security tools**  
- Demonstrates integration of Defender logs into SIEM (Splunk)  
- Provides proof of detection workflows with documentation  

---

## 🏗️ Components, Definitions, and Purpose

| Keyword / Tool | Definition | Purpose in Lab |
|----------------|------------|----------------|
| [Windows Defender Antivirus](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-windows) | Built‑in Windows security tool for malware protection. | Detects and blocks malicious files/processes. |
| [Defender Firewall](https://learn.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security) | Network traffic filtering tool. | Prevents unauthorized inbound/outbound connections. |
| [Defender Security Center](https://learn.microsoft.com/en-us/windows/security/threat-protection/windows-security) | GUI dashboard for Defender. | Central place to manage antivirus, firewall, and protection settings. |
| [Event Viewer](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/event-viewer) | Windows log viewer. | Displays Defender alerts and system events. |
| [Splunk Integration](https://docs.splunk.com/Documentation/Forwarder) | Forwarding Defender logs to Splunk. | Enables centralized detection and correlation. |
| [PowerShell](https://learn.microsoft.com/en-us/powershell/) | Command‑line automation tool. | Used to configure Defender policies and extract logs. |

---

## ⚙️ Step‑by‑Step Setup

### Step 1: Enable Windows Defender
- **What:** Ensure Defender Antivirus is active.  
- **How:**  
  - Go to **Windows Security → Virus & Threat Protection**  
  - Confirm **Real‑time protection** is ON  
- **Why:** Provides baseline endpoint protection.

---

### Step 2: Configure Defender Firewall
- **What:** Enable firewall rules.  
- **How:**  
  - Open **Windows Security → Firewall & Network Protection**  
  - Ensure firewall is ON for Domain, Private, and Public networks  
- **Why:** Blocks unauthorized traffic.

---

### Step 3: Enable Logging
- **What:** Defender logs events in Event Viewer.  
- **How:**  
  - Open **Event Viewer → Applications and Services Logs → Microsoft → Windows → Windows Defender**  
  - Verify logs are being generated (Event IDs like 1116 for malware detection).  
- **Why:** Logs are critical for SIEM ingestion.

---

### Step 4: Forward Logs to Splunk
- **What:** Use Splunk Universal Forwarder.  
- **How:**  
  - Configure `inputs.conf` to monitor Defender log path:  
    ```
    [WinEventLog://Microsoft-Windows-Windows Defender/Operational]
    disabled = 0
    ```
  - Restart Splunk Forwarder.  
- **Why:** Centralizes Defender alerts in Splunk.

---

### Step 5: Use PowerShell for Defender Management
- **What:** PowerShell provides advanced control.  
- **How:**  
  - Check status:  
    ```
    Get-MpComputerStatus
    ```
  - Run quick scan:  
    ```
    Start-MpScan -ScanType QuickScan
    ```
  - Update signatures:  
    ```
    Update-MpSignature
    ```
- **Why:** Automates detection and response tasks.

---

## 🚨 Incident Response Playbooks

| Incident Type | Detection | Response | Purpose |
|---------------|-----------|----------|---------|
| Malware Infection | Defender Event ID 1116 | Quarantine file, run full scan | Contain and remove malware. |
| Suspicious Network Traffic | Firewall logs | Block IP, alert SOC | Prevent lateral movement. |
| Unauthorized App Execution | Defender alert + Sysmon | Kill process, IOC hunt | Stop persistence attempts. |

---

## ✅ Validation Checklist
- [ ] Defender Antivirus enabled  
- [ ] Firewall ON for all profiles  
- [ ] Logs visible in Event Viewer  
- [ ] Splunk ingestion validated  
- [ ] PowerShell commands tested  
- [ ] Screenshots stored in `proof/` folder  

---

## 📚 Glossary of Keywords
- [Windows Defender Antivirus](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-windows)  
- [Defender Firewall](https://learn.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)  
- [Defender Security Center](https://learn.microsoft.com/en-us/windows/security/threat-protection/windows-security)  
- [Event Viewer](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/event-viewer)  
- [Splunk Universal Forwarder](https://docs.splunk.com/Documentation/Forwarder)  
- [PowerShell](https://learn.microsoft.com/en-us/powershell/)  

---

## 🎯 Conclusion
Windows Defender provides **built‑in endpoint protection** that integrates seamlessly with your SOC lab.  
By enabling logging, forwarding events to Splunk, and practicing playbooks, you gain **real‑world detection and response skills** recruiters value.  

---

## 🤝 Connect With Me
- 🌐 GitHub: [LetsLearn-08](https://github.com/LetsLearn-08?tab=repositories)  
- 💼 LinkedIn: [Tanuja Reddy](https://www.linkedin.com/in/tanuja-reddy-03aa7b38a)  
