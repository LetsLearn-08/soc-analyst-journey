# Wireshark Lab Setup – Beginner’s Manual

## 📖 Introduction
Wireshark is an **open-source network protocol analyzer** widely used in SOCs and incident response.  
It acts as the **SOC’s microscope**, allowing analysts to capture and inspect raw packet traffic to detect attacker techniques such as reconnaissance, tunneling, and data exfiltration.  

In this lab, Wireshark helps you:
- Capture and analyze live network traffic
- Apply filters to isolate suspicious activity
- Decode protocols like TCP, DNS, HTTP, and ICMP
- Document findings with screenshots for recruiter‑ready proof

By mastering Wireshark, you demonstrate the **network analysis and incident detection skills recruiters expect** from SOC analysts.

---

## 🎯 Why This Lab Matters
- Shows ability to analyze raw network traffic — a core SOC skill  
- Provides visibility into attacker techniques like port scans, beaconing, and exfiltration  
- Builds proof of detection workflows with filters, screenshots, and documented playbooks  

---

## 🏗️ Wireshark Components, Definitions, and Purpose

| Component | Definition | Purpose in Lab |
|-----------|------------|----------------|
| [Wireshark](https://www.wireshark.org/) | Open-source network protocol analyzer. | Captures and inspects packet traffic for anomalies. |
| Capture Filters | Rules applied before capture begins. | Reduce noise, focus only on relevant traffic. |
| Display Filters | Syntax applied after capture. | Highlight suspicious traffic patterns for SOC analysis. |
| Protocol Decoders | Built-in parsers for TCP, DNS, HTTP, ICMP, etc. | Help analysts understand attacker techniques. |
| Statistics Tools | Features like “Conversations” and “Endpoints.” | Summarize flows, detect anomalies, and support incident triage. |

---

## ⚙️ Step‑by‑Step Setup

### Step 1: Install Wireshark
- **What:** Wireshark captures and analyzes packets.  
- **How:**  
  1. Download Wireshark from [official site](https://www.wireshark.org/).  
  2. Install on your attacker/victim VM or host machine.  
  3. Ensure you have permissions to capture network traffic.  
- **Why:** Without Wireshark, you cannot inspect raw traffic for attacker techniques.

---

### Step 2: Configure Capture Filters
- **What:** Capture filters limit traffic before recording.  
- **How:** Example:  
   ```
   tcp port 80
   ```
- **Why:** Reduces noise and focuses on relevant traffic.

---

### Step 3: Apply Display Filters
- **What:** Display filters refine captured traffic.  
- **How:** Example:
  ```
  http.request
  ```
- **Why:** Helps isolate suspicious traffic patterns for SOC analysis.

---

### Step 4: Use Protocol Decoders
- **What:** Wireshark decodes protocols like TCP, DNS, HTTP, ICMP.  
- **How:** Inspect packet details in the middle pane.  
- **Why:** Understanding protocol behavior is critical for detecting anomalies.

---

### Step 5: Document Findings
- **What:** Save annotated screenshots in `screenshots/`.  
- **How:** Label clearly (e.g., `Wireshark-DNS-Query.png`).  
- **Why:** Documentation proves your SOC analysis skills to recruiters.

---

## 🚨 Incident Response Playbooks

| Incident Type | Detection (Wireshark Filter) | Response | Purpose |
|---------------|-------------------------------|----------|---------|
| **Port Scan / Reconnaissance** | `tcp.flags.syn==1 && tcp.flags.ack==0` | Identify source IP, block attacker | Detects multiple SYN packets without ACKs (scan behavior). |
| **Suspicious DNS Beaconing** | `dns && ip.dst==<suspicious_IP>` | Investigate domain, enrich with threat intel | Detects repeated DNS queries to suspicious domains. |
| **HTTP Data Exfiltration** | `http && ip.src==<internal_IP>` | Terminate connection, investigate host | Detects large outbound HTTP traffic from internal machines. |
| **ICMP Tunneling** | `icmp && data.len>100` | Block ICMP traffic, alert SOC | Detects abnormal ICMP packets used for covert channels. |
| **Unencrypted Credentials** | `http.request.method==POST && tcp.port==80` | Alert SOC, enforce HTTPS | Detects sensitive data sent over cleartext HTTP. |

---

## ✅ Validation Checklist
- [ ] Wireshark installed and running  
- [ ] Capture filters tested (e.g., `tcp port 80`)  
- [ ] Display filters validated (e.g., `http.request`)  
- [ ] Protocols decoded and anomalies identified  
- [ ] Screenshots stored in `screenshots/` folder  
- [ ] Incident playbooks tested with sample traffic  

---

## 📚 Glossary of Keywords
- [Wireshark TOOL](https://www.wireshark.org/) → [Wireshark Manual](Wireshark_Manual.md)  
- Capture Filters → See [`filters.md`](filters.md)  
- Display Filters → See [`filters.md`](filters.md)  
- Protocols → See [`protocols.md`](protocols.md)  
- Shortcuts → See [`shortcuts.md`](shortcuts.md)  
- Tips & Tricks → See [`tips.md`](tips.md)  

---

## 🎯 Conclusion
Wireshark is the **SOC’s microscope**.  
It captures raw traffic, applies filters, and decodes protocols to reveal attacker techniques.  

By documenting filters, screenshots, and playbooks, you prove your ability to perform **network analysis and incident detection** — critical skills for SOC analysts.

---

## 🤝 Connect With Me
- 🌐 GitHub: [LetsLearn-08](https://github.com/LetsLearn-08?tab=repositories)  
- 💼 LinkedIn: [Tanuja Reddy](https://www.linkedin.com/in/tanuja-reddy-03aa7b38a)
 
