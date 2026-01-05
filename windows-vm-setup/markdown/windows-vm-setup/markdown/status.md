# 📊 Lab Status & Next Steps

This document tracks the current progress of the Windows 10 SOC lab setup and outlines upcoming tasks.

---

## ✅ Completed
- Windows 10 VM created and installed (`windows-install.md`)
- VirtualBox Guest Additions installed (`guest-additions.md`)
- Networking configured (NAT + Host‑only, `192.168.56.0/24`)
- Snapshot created: `Win10_BaseInstall_ReadyForTools`
- Sysmon installed with custom configuration
- Winlogbeat/NXLog configured to forward logs to SIEM‑VM
- Visibility tools installed: Wireshark, Process Explorer, Autoruns
- Test users created and login events simulated

---

## 🔄 In Progress
- Collecting proof screenshots for all major steps
- Validating log forwarding to SIEM‑VM
- Documenting detection scenarios (failed logins, suspicious processes)

---

## 📅 Next Steps
- Integrate with SIEM‑VM (`siem-setup.md`)
- Add detection engineering examples (e.g., brute force login alerts)
- Expand lab with attack simulation (`metasploitable2-lab.md`)
- Polish README with badges, navigation links, and screenshot references

---

## 🎯 Goal
Maintain a reproducible, proof‑driven SOC lab environment that demonstrates endpoint visibility and detection workflows for recruiters and peers.
