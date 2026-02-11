# 📨 Phishing Simulation – SOC Lab Phase 3

## 📖 Summary
This simulation demonstrates how a **[phishing attack](https://en.wikipedia.org/wiki/Phishing)** can be detected and responded to in a SOC environment.  
Phishing is one of the most common attack vectors, often delivered via email with malicious attachments or links.

---

## ⚙️ Setup
- Used **Thunderbird** email client to craft and send a phishing email.  
- Email contained a malicious link designed to trigger **[Microsoft Edge](https://en.wikipedia.org/wiki/Microsoft_Edge)** (`msedge.exe`) when clicked.  
- Logs were forwarded into **[Splunk](https://en.wikipedia.org/wiki/Splunk)** for analysis.

---

## 🔍 Detection Workflow
1. **Sysmon Event ID 1** captured the process chain: `Thunderbird → Edge`.  
2. Splunk ingested logs and correlation rules flagged suspicious activity.  
3. Queries were built to identify abnormal email behavior.  

---

## 🛡️ Incident Response Steps
- **Tier‑1 Analyst:** Identify suspicious email activity.  
- **Tier‑1 Escalation:** Isolate affected endpoint.  
- **Tier‑2 Analyst:** Investigate attachments/links, escalate if confirmed malicious.  

---

## 📎 Proof
Screenshots stored in `proof3/phishing_*`:
- Email creation and delivery.  
- Sysmon Event Viewer logs.  
- Splunk query results.  

---

## 📑 Lessons Learned
- Phishing detection requires **quick isolation** to prevent lateral movement.  
- SOC analysts must be trained to recognize suspicious email patterns.  
- Playbooks standardize response and reduce confusion during incidents.
