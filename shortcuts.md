# Wireshark Shortcuts & Pro Tips – SOC Cheatsheet

## 📖 Introduction
Efficiency is critical in a SOC environment.  
Wireshark provides keyboard shortcuts and workflow tricks that allow analysts to move faster, isolate suspicious traffic, and document findings during incident response.  

By mastering shortcuts and pro tips, you demonstrate the **speed and precision recruiters expect** from SOC analysts.

---

## 🎯 Why This Matters
- Saves time during live incident investigations  
- Reduces analyst fatigue by streamlining navigation  
- Ensures reproducible workflows for SOC documentation  
- Builds proof of efficient packet analysis skills  

---

## 🏗️ Shortcuts & Tips, Definitions, and Purpose

| Shortcut / Tip | Definition | Purpose in SOC Lab |
|----------------|------------|--------------------|
| **Ctrl + E** | Start/stop packet capture. | Quickly toggle captures during investigations. |
| **Ctrl + F** | Find packets by string, hex, or field. | Locate suspicious traffic fast. |
| **Ctrl + Shift + F** | Apply display filter. | Narrow down traffic to attacker patterns. |
| **Ctrl + H** | Toggle packet details pane. | Focus on raw packet data when needed. |
| **Ctrl + N** | Open new capture window. | Run multiple captures in parallel. |
| **Ctrl + S** | Save capture file. | Preserve forensic evidence for SOC reports. |
| **Ctrl + Shift + S** | Save with options. | Export filtered traffic for deeper analysis. |
| **Statistics → Conversations** | Summarizes endpoints and flows. | Detects anomalies like port scans or beaconing. |
| **Statistics → Endpoints** | Lists all IPs seen in capture. | Identifies suspicious hosts quickly. |
| **Coloring Rules** | Highlight traffic by filter. | Visually flag attacker traffic (e.g., DNS queries). |
| **Expert Info** | Built‑in diagnostic alerts. | Quickly spot malformed packets or anomalies. |

---

## ⚙️ Step‑by‑Step Usage

### Step 1: Start Capture Efficiently
- Use **Ctrl + E** to start/stop captures.  
- Apply capture filters before starting (e.g., `tcp port 80`).  

---

### Step 2: Navigate & Isolate Traffic
- Use **Ctrl + F** to search for suspicious strings (e.g., domains, IPs).  
- Apply display filters with **Ctrl + Shift + F** to isolate attacker traffic.  

---

### Step 3: Summarize & Detect
- Use **Statistics → Conversations** to detect port scans or abnormal flows.  
- Use **Statistics → Endpoints** to identify suspicious IPs.  

---

### Step 4: Document Findings
- Save captures with **Ctrl + S**.  
- Export filtered traffic with **Ctrl + Shift + S**.  
- Store annotated screenshots in `screenshots/` for recruiter‑ready proof.  

---

## 🚨 Incident Response Playbooks with Shortcuts & Tips

| Incident Type | Shortcut / Tip | SOC Response | Purpose |
|---------------|----------------|--------------|---------|
| **Port Scan Detection** | Statistics → Conversations | Identify source IP, block attacker | Summarizes abnormal SYN flows. |
| **Suspicious DNS Beaconing** | Coloring Rules (`dns`) | Investigate domain, enrich with threat intel | Visually flags repeated DNS queries. |
| **HTTP Data Exfiltration** | Ctrl + Shift + F (`http && ip.src==<internal_IP>`) | Terminate connection, investigate host | Isolates large outbound HTTP traffic. |
| **ICMP Tunneling** | Expert Info + Display Filter (`icmp && data.len>100`) | Block ICMP traffic, alert SOC | Detects abnormal ICMP payloads. |
| **Credential Leak** | Ctrl + F (`POST`) | Alert SOC, enforce HTTPS | Finds sensitive data sent over cleartext HTTP. |

---

## ✅ Validation Checklist
- [ ] Shortcuts tested (Ctrl + E, Ctrl + F, Ctrl + Shift + F, Ctrl + S)  
- [ ] Statistics tools used (Conversations, Endpoints)  
- [ ] Coloring rules applied for suspicious traffic  
- [ ] Expert Info reviewed for anomalies  
- [ ] Screenshots stored in `screenshots/` folder  
- [ ] Playbooks validated with sample traffic  

---

## 📚 Glossary of Keywords
- [Wireshark](https://www.wireshark.org/) → [Wireshark Manual](Wireshark_Manual.md)  
- Capture Filters → Pre‑capture rules to reduce noise  
- Display Filters → Post‑capture rules to isolate traffic  
- Statistics Tools → Summarize flows and endpoints for anomaly detection  
- Coloring Rules → Visual highlighting of attacker traffic  
- Expert Info → Built‑in diagnostic alerts for anomalies  

---

## 🎯 Conclusion
Shortcuts and pro tips make Wireshark the **SOC analyst’s fast‑response toolkit**.  
They enable quick navigation, efficient detection, and reproducible documentation during incidents.  

By combining shortcuts with playbooks, you prove your ability to perform **rapid packet analysis and incident triage** — critical skills for SOC analysts.

---

## 🤝 Connect With Me
- 🌐 GitHub: [LetsLearn-08](https://github.com/LetsLearn-08?tab=repositories)  
- 💼 LinkedIn: [Tanuja Reddy](https://www.linkedin.com/in/tanuja-reddy-03aa7b38a)
