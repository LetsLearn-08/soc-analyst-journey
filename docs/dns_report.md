
# DNS Query Monitoring – Incident Report

**Incident Title:** Suspicious Domain Access Detected  

**Date/Time:** 2026‑02‑07  

**Systems Involved:** Windows Forwarder VM (106), Splunk SIEM VM (102), Kali Attacker VM (104)



### 🔎 Incident Description

Suspicious DNS query observed (`badsite.com`) triggered by attacker activity.  

### 📊 Detection Method
- Windows DNS Client logs showed Event ID 3008.  
- Splunk query:
  ```
  index=win_logs sourcetype=WinDNS "badsite.com"
  ```
- Stats query confirmed attacker IP (192.168.56.104).

### ⚠️ Impact

Potential malware beaconing or phishing attempt.

### ✅ Response

DNS client logging enabled, Splunk ingestion validated, screenshots saved in proof2.
