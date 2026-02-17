# Wireshark Protocols – SOC Cheatsheet

## 📖 Introduction
Protocols are the **language of the network**.  
In a SOC environment, understanding how protocols behave allows analysts to spot anomalies, detect attacker techniques, and respond effectively to incidents.  

Wireshark decodes protocols like TCP, DNS, HTTP, and ICMP, giving SOC analysts visibility into reconnaissance, exploitation, and exfiltration attempts.

---

## 🎯 Why Protocol Analysis Matters
- Reveals attacker techniques hidden in normal traffic  
- Helps distinguish legitimate activity from malicious behavior  
- Provides forensic proof during incident investigations  
- Maps detections to MITRE ATT&CK tactics (Reconnaissance, Command & Control, Exfiltration)  

---

## 🏗️ Common Protocols, Definitions, and Purpose

| Protocol | Definition | Purpose in SOC Lab |
|----------|------------|--------------------|
| **TCP (Transmission Control Protocol)** | Connection‑oriented protocol for reliable communication. | Detects port scans, abnormal flags, and suspicious sessions. |
| **UDP (User Datagram Protocol)** | Connectionless protocol for fast communication. | Detects DNS abuse, tunneling, or exfiltration. |
| **DNS (Domain Name System)** | Resolves domain names to IP addresses. | Detects beaconing, suspicious domains, and malware callbacks. |
| **HTTP (Hypertext Transfer Protocol)** | Protocol for web communication. | Detects exfiltration, unencrypted credentials, or malicious payloads. |
| **HTTPS (HTTP Secure)** | Encrypted web communication using TLS. | Detects encrypted C2 traffic and validates certificate anomalies. |
| **ICMP (Internet Control Message Protocol)** | Used for diagnostics (ping). | Detects tunneling, covert channels, or reconnaissance. |
| **ARP (Address Resolution Protocol)** | Resolves IP addresses to MAC addresses. | Detects spoofing or man‑in‑the‑middle attacks. |

---

## ⚙️ Step‑by‑Step Usage

### Step 1: Capture Traffic
- Start a Wireshark capture on the victim or network VM.  
- Apply capture filters to reduce noise (e.g., `tcp port 80`).  

---

### Step 2: Apply Display Filters
- Use protocol‑specific filters to isolate traffic:  
  - `tcp.flags.syn==1 && tcp.flags.ack==0` → Detect SYN scans  
  - `dns` → Show DNS queries/responses  
  - `http.request` → Show HTTP requests  
  - `icmp` → Show ICMP traffic  

---

### Step 3: Decode Protocol Behavior
- Inspect packet details in the middle pane.  
- Look for anomalies such as repeated DNS queries, large HTTP POST requests, or unusual ICMP payloads.  

---

## 🚨 Incident Response Playbooks with Protocols

| Incident Type | Protocol | Wireshark Filter | SOC Response | Purpose |
|---------------|----------|------------------|--------------|---------|
| **Port Scan / Reconnaissance** | TCP | `tcp.flags.syn==1 && tcp.flags.ack==0` | Identify source IP, block attacker | Detects multiple SYN packets without ACKs. |
| **Suspicious DNS Beaconing** | DNS | `dns && ip.dst==<suspicious_IP>` | Investigate domain, enrich with threat intel | Detects repeated DNS queries to suspicious domains. |
| **HTTP Data Exfiltration** | HTTP | `http && ip.src==<internal_IP>` | Terminate connection, investigate host | Detects large outbound HTTP traffic from internal machines. |
| **ICMP Tunneling** | ICMP | `icmp && data.len>100` | Block ICMP traffic, alert SOC | Detects abnormal ICMP packets used for covert channels. |
| **ARP Spoofing** | ARP | `arp` | Investigate MAC/IP mismatch, isolate host | Detects man‑in‑the‑middle attempts. |



---

## 📚 Glossary of Keywords
- [Wireshark](https://www.wireshark.org/) → [Wireshark Manual](Wireshark_Manual.md)  
- TCP → Reliable communication protocol, detects scans and anomalies  
- DNS → Domain resolution, detects beaconing and callbacks  
- HTTP/HTTPS → Web communication, detects exfiltration and credential leaks  
- ICMP → Diagnostic protocol, detects tunneling and covert channels  
- ARP → Address resolution, detects spoofing attacks  

---

## 🎯 Conclusion
Protocol analysis in Wireshark is the **SOC analyst’s decoder ring**.  
By applying filters, decoding anomalies, and documenting playbooks, you prove your ability to perform **network protocol analysis and incident detection** — essential skills for SOC analysts.

---

## 🤝 Connect With Me
- 🌐 GitHub: [LetsLearn-08](https://github.com/LetsLearn-08?tab=repositories)  
- 💼 LinkedIn: [Tanuja Reddy](https://www.linkedin.com/in/tanuja-reddy-03aa7b38a)
