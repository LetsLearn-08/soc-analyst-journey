# Firewall Analysis – Incident Report

**Incident Title:** Port Scan Detection via Firewall Logs  

**Date/Time:** 2026‑02‑07  

**Systems Involved:** Windows Forwarder VM (106), Splunk SIEM VM (102), Kali Attacker VM (104)



### 🔎 Incident Description

Nmap scan from Kali triggered multiple firewall DROP events on Windows.  

### 📊 Detection Method

- Raw firewall logs (`pfirewall.log`) showed DROP entries.  
- Splunk query:
  ```
  index=win_logs sourcetype=WinFirewall "DROP"
  ```
- Stats query confirmed attacker IP (192.168.56.104).

### ⚠️ Impact

Unauthorized port scan detected.

### ✅ Response

Firewall logging enabled, Splunk ingestion validated, screenshots saved in proof2
