# 🔐 SOC Preparation for Windows 10 VM

This document explains how to prepare the Windows 10 VM for Security Operations Center (SOC) workflows. The goal is to enable endpoint visibility, log forwarding, and detection engineering.

---

## 📥 Prerequisites
- Completed Windows 10 installation (`windows-install.md`)
- Guest Additions installed (`guest-additions.md`)
- Networking configured with NAT + Host‑only adapters

---

## 🛠️ Tools Installed
1. **Sysmon** (System Monitor)
   - Provides detailed process, network, and file creation logs
   - Installed with a custom XML configuration
   - Config file placed in `C:\SysmonConfig.xml`
   - Command:  
     ```powershell
     sysmon.exe -accepteula -i C:\SysmonConfig.xml
     ```
   ✅ *Verification*: Check Event Viewer → Applications and Services Logs → Microsoft → Sysmon

2. **Winlogbeat / NXLog**
   - Forwards Windows event logs to SIEM‑VM
   - Configured to send logs over Host‑only adapter (`192.168.56.x`)
   - Example Winlogbeat config snippet:
     ```yaml
     output.logstash:
       hosts: ["192.168.56.101:5044"]
     ```
   ✅ *Verification*: Confirm logs received on SIEM‑VM

3. **Visibility Tools**
   - **Wireshark**: Network packet capture
   - **Process Explorer**: Advanced process monitoring
   - **Autoruns**: Startup program visibility

✅ *Verification*: Launch each tool and confirm functionality

---

## 👥 Test Users & Events
- Created local test accounts (`labuser1`, `labuser2`)
- Simulated login success and failure events
- Generated sample process activity (e.g., running `notepad.exe`)

✅ *Verification*: Check Security Event Logs for login attempts  


---

## 📸 Proof Screenshot Checklist
- Sysmon installation command
- Event Viewer showing Sysmon logs
- Winlogbeat/NXLog config file
- SIEM‑VM receiving logs
- Wireshark capture window
- Process Explorer running
- Autoruns startup list

---

## 🎯 Goals
- Establish endpoint visibility for SOC workflows
- Forward logs to SIEM for centralized analysis
- Provide reproducible setup for detection engineering

---

## 🔗 Next Steps
- Integrate with SIEM‑VM (`siem-setup.md`)
- Document detection scenarios (failed logins, suspicious processes)
- Expand lab with attack simulation (`metasploitable2-lab.md`)
