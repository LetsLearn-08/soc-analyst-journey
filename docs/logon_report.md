
# Logon Correlation – Incident Report

**Incident Title:** Failed and Successful Logon Attempts Detected  

**Date/Time:** 2026‑02‑07  

**Systems Involved:** Windows Forwarder VM (106), Splunk SIEM VM (102), Kali Attacker VM (104)


### 🔎 Incident Description

Multiple failed logon attempts (Event ID 4625) followed by a successful logon (Event ID 4624).  

### 📊 Detection Method
- Windows Security logs showed Event IDs 4625 + 4624.  
- Splunk query:
  ```
  index=win_logs EventCode=4625 OR EventCode=4624
  ```
- Stats query correlated attacker IP (192.168.56.104).

### ⚠️ Impact

Brute force attempt detected, successful logon could lead to compromise.

### ✅ Response

Security logging enabled, Splunk ingestion validated, screenshots saved in proof2
