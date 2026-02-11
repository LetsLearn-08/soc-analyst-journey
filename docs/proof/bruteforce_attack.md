# 🔐 Brute Force Attack Simulation – SOC Lab Phase 3

## 📖 Summary
This simulation demonstrates detection of a **[brute-force attack](https://en.wikipedia.org/wiki/Brute-force_attack)** against authentication services.  
Brute force attacks attempt repeated logins until credentials are guessed.

---

## ⚙️ Setup
- Attack launched from **Kali Linux** using tools like Hydra.  
- Targeted **[SSH](https://en.wikipedia.org/wiki/Secure_Shell)** and **[RDP](https://en.wikipedia.org/wiki/Remote_Desktop_Protocol)** services on the Windows VM.  
- Logs ingested into Splunk for correlation.

---

## 🔍 Detection Workflow
1. Windows Security logs captured repeated failed login attempts.  
2. Sysmon recorded authentication activity.  
3. Splunk correlation rules flagged multiple failed logins followed by a successful compromise.  

---

## 🛡️ Incident Response Steps
- **Tier‑1 Analyst:** Detect abnormal login attempts.  
- **Tier‑1 Escalation:** Escalate to Tier‑2 SOC analyst.  
- **Tier‑2 Analyst:** Block attacker IP, reset compromised credentials, investigate persistence.  

---

## 📎 Proof
Screenshots stored in `proof3/bruteforce_*`:
- Hydra brute force attempts.  
- Windows Event Viewer logs.  
- Splunk correlation rule detection.  

---

## 📑 Lessons Learned
- Brute force detection benefits from **correlation rules** to reduce noise.  
- Failed login thresholds must be tuned to avoid false positives.  
- Escalation workflows ensure compromised accounts are contained quickly.
