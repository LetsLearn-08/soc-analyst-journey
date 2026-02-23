# 📅 Phase 6 – Endpoint Detection & Response (EDR) Tools (Days 76–80)

## 📖 Introduction
This phase focuses on **Endpoint Detection & Response (EDR)** solutions.  
EDR tools provide visibility into endpoint activity (processes, files, registry, network connections) and help detect, investigate, and respond to threats.  

By the end of this phase, you will:
- Understand how open-source EDR tools work
- Configure agents to collect endpoint telemetry
- Detect suspicious activity such as malware execution, privilege escalation, and persistence
- Document findings with screenshots stored in `proof6/`

---

## 🎯 Why This Phase Matters
- Recruiters value hands‑on EDR experience since it’s core to SOC workflows.  
- Demonstrates ability to configure endpoint agents and analyze telemetry.  
- Builds detection skills beyond SIEM, focusing on host-level visibility.  

---

## 🏗️ Tools, Definitions, and Purpose

| Tool | Definition | Purpose in Lab |
|------|------------|----------------|
| [Wazuh](https://wazuh.com/) | Open-source security platform with EDR, SIEM, and XDR capabilities. | Collects endpoint telemetry, detects anomalies, integrates with Elastic. |
| [OSSEC](https://www.ossec.net/) | Host-based intrusion detection system (HIDS). | Monitors logs, file integrity, rootkits, and policy violations. |
| [Windows Defender](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/) | Built-in Windows AV/EDR solution. | Provides baseline detection, logs suspicious activity. |
| *(Placeholder: [Cortex XDR](https://www.paloaltonetworks.com/cortex/xdr) / [CrowdStrike Falcon](https://www.crowdstrike.com/))* | Commercial EDR platforms. | Advanced detection and response, to be explored later. |

---

## ⚙️ Step‑by‑Step Setup

### Step 1: Wazuh Deployment
- Install Wazuh Manager on a dedicated VM.  
- Install Wazuh Agent on Windows/Linux endpoints.  
- Configure agent to connect to manager via static IP.  
- Validate connectivity:  
````
  systemctl status wazuh-agent
  tail -f /var/ossec/logs/ossec.log
````
### Step 2: OSSEC Setup
- Install OSSEC on Linux endpoint.
- Configure agent to monitor /var/log/auth.log, /etc/passwd, and file integrity for /etc/.
- Validate alerts:
```
tail -f /var/ossec/logs/alerts/alerts.log
```
### Step 3: Windows Defender Logs
- Enable Windows Defender on victim VM.
- Configure Event Forwarding for key Event IDs:
   - 1116 → Malware detected
   - 5007 → Configuration change
   - 1121 → Suspicious behavior blocked
- Forward logs to Splunk/Elastic for correlation.

---

## 🚨 Detection Use Cases

- Malware Execution → Wazuh detects suspicious process creation (4688), OSSEC alerts on modified files, Defender logs malware detection (1116).
- Privilege Escalation → Wazuh detects 4672, OSSEC alerts on unauthorized root login, Defender flags suspicious privilege use.
- Persistence Techniques → Wazuh detects registry modifications, OSSEC alerts on startup script changes, Defender logs scheduled task creation.

---

🚨 MITRE ATT&CK Mapping

- T1059 – Command and Scripting Interpreter
- T1068 – Exploitation for Privilege Escalation
- T1547 – Boot or Logon Autostart Execution
- T1078 – Valid Accounts

---

✅ Validation Checklist

- [ ] Wazuh Manager + Agent installed and connected
- [ ] OSSEC configured for log and file integrity monitoring
- [ ] Windows Defender logs forwarded to SIEM
- [ ] Detection queries tested for malware, privilege escalation, persistence
- [ ] Screenshots stored in proof6/
- [ ] Documentation updated in docs/Phase6_EDR.md

## 🎯 Conclusion

Phase 6 builds endpoint visibility and detection skills.
By deploying Wazuh, OSSEC, and leveraging Windows Defender logs, you gain practical experience in detecting malware, privilege escalation, and persistence techniques.
All screenshots and evidence are stored in proof6/ for validation.
This phase demonstrates host‑level visibility and detection skills, proving readiness for SOC workflows where endpoint telemetry is critical.

## 🤝 Connect With Me
- 🌐 GitHub: [LetsLearn-08](https://github.com/LetsLearn-08?tab=repositories)  
- 💼 LinkedIn: [Tanuja Reddy](https://www.linkedin.com/in/tanuja-reddy-03aa7b38a)
