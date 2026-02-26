# 📅 Phase 6 – Endpoint Detection & Response (EDR) Tools (Days 76–80)

## 📖 Introduction
This phase focuses on **Endpoint Detection & Response (EDR)** solutions.  
EDR tools provide visibility into endpoint activity (processes, files, registry, network connections) and help detect, investigate, and respond to threats.  

By the end of this phase, you will:
- Understand how Windows Defender logs can be leveraged for detection
- Forward endpoint telemetry to a SIEM for analysis
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
| [Windows Defender](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/) | Built-in Windows AV/EDR solution. | Provides baseline detection, logs suspicious activity. |
| *(Placeholder: [Cortex XDR](https://www.paloaltonetworks.com/cortex/xdr) / [CrowdStrike Falcon](https://www.crowdstrike.com/))* | Commercial EDR platforms. | Advanced detection and response, to be explored later. |

---

## ⚙️ Step‑by‑Step Setup

### Step 1: Windows Defender Logs
- Ensure Windows Defender is enabled on the victim VM.  
- Configure Event Forwarding for key Event IDs:  
   - **1116** → Malware detected  
   - **5007** → Configuration change  
   - **1121** → Suspicious behavior blocked  
- Forward logs to Splunk/Elastic for correlation and visualization.

---

## 🚨 Detection Use Cases

- **Malware Execution** → Defender logs Event ID 1116 when malware is detected.  
- **Privilege Escalation** → Defender flags suspicious privilege use (correlated with 4672 in Windows Security logs).  
- **Persistence Techniques** → Defender logs scheduled task creation or registry modifications.  

---

## 🚨 MITRE ATT&CK Mapping

- T1059 – Command and Scripting Interpreter  
- T1068 – Exploitation for Privilege Escalation  
- T1547 – Boot or Logon Autostart Execution  
- T1078 – Valid Accounts  

---

## 📊 Detection Summary Table

| Event ID | Tool | MITRE Technique | Example Detection |
|----------|------|-----------------|------------------|
| 1116 – Malware Detected | Defender | T1078 | Malware execution blocked |
| 5007 – Config Change | Defender | T1547 | Persistence via startup modification |
| 1121 – Suspicious Behavior | Defender | T1068 | Privilege escalation attempt |

---

## ✅ Validation Checklist

- [ ] Windows Defender enabled and logging  
- [ ] Event Forwarding configured for key IDs  
- [ ] Logs forwarded to SIEM (Splunk/Elastic)  
- [ ] Detection queries tested for malware, privilege escalation, persistence  
- [ ] Screenshots stored in `proof6/`  
- [ ] Documentation updated in `docs/Phase6_EDR.md`  

---

## 🔍 Preview Subsection

**Phase 6 – Endpoint Detection & Response (EDR)**  
Windows Defender telemetry was forwarded to Splunk, enabling detection of malware execution, privilege escalation, and persistence attempts.  
Proof artifacts are stored in `proof6/` and linked in `docs/Phase6_EDR.md`.

---

## 🎯 Conclusion

Phase 6 builds endpoint visibility and detection skills.  
By leveraging Windows Defender logs and forwarding them to a SIEM, you gain practical experience in detecting malware, privilege escalation, and persistence techniques.  
All screenshots and evidence are stored in `proof6/` for validation.  
This phase demonstrates host‑level visibility and detection skills, proving readiness for SOC workflows where endpoint telemetry is critical.

---


## 🤝 Connect With Me
- 🌐 GitHub: [LetsLearn-08](https://github.com/LetsLearn-08?tab=repositories)  
- 💼 LinkedIn: [Tanuja Reddy](https://www.linkedin.com/in/tanuja-reddy-03aa7b38a)
