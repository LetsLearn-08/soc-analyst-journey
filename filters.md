# Wireshark Filters – SOC Cheatsheet

## 📖 Introduction
Wireshark filters are the **core detection mechanism** for packet analysis.  
In a SOC environment, filters allow analysts to isolate suspicious traffic patterns, detect attacker techniques, and triage incidents quickly.  

By mastering capture and display filters, you demonstrate the **network detection and incident response skills recruiters expect** from SOC analysts.

---

## 🎯 Why Filters Matter
- Reduce noise and focus on relevant traffic during investigations  
- Enable quick detection of attacker behaviors (port scans, beaconing, exfiltration)  
- Provide reproducible proof of analysis for SOC documentation  

---

## 🏗️ Filter Types, Definitions, and Purpose

| Filter Type | Definition | Purpose in SOC Lab |
|-------------|------------|--------------------|
| **Capture Filters** | Applied before packet capture begins. | Limit traffic collection to relevant flows (e.g., only HTTP or DNS). |
| **Display Filters** | Applied after capture. | Highlight suspicious traffic patterns for SOC analysis. |
| **Protocol Filters** | Built-in keywords for TCP, DNS, HTTP, ICMP, etc. | Decode attacker techniques at the packet level. |

---

## ⚙️ Step‑by‑Step Usage

### Step 1: Apply Capture Filters
- **What:** Limit traffic before capture.  
- **How:** Example:  
```
tcp port 80
```
- **Why:** Focuses on HTTP traffic only, reducing noise.

---

### Step 2: Apply Display Filters
- **What:** Narrow down captured traffic for analysis.  
- **How:** Example:
```
http.request
```
- **Why:** Isolates HTTP requests, useful for spotting suspicious activity.

---

### Step 3: Use Protocol Filters
- **What:** Decode attacker techniques.  
- **How:** Examples:  
- `dns` → Show DNS queries/responses  
- `icmp` → Show ICMP traffic (ping/tunneling)  
- `tcp.flags.syn==1 && tcp.flags.ack==0` → Detect SYN scans  
- **Why:** Helps identify reconnaissance, beaconing, or tunneling.

---

## 🚨 Incident Response Playbooks with Filters

| Incident Type | Wireshark Filter | SOC Response | Purpose |
|---------------|------------------|--------------|---------|
| **Port Scan / Reconnaissance** | `tcp.flags.syn==1 && tcp.flags.ack==0` | Identify source IP, block attacker | Detects multiple SYN packets without ACKs (scan behavior). |
| **Suspicious DNS Beaconing** | `dns && ip.dst==<suspicious_IP>` | Investigate domain, enrich with threat intel | Detects repeated DNS queries to suspicious domains. |
| **HTTP Data Exfiltration** | `http && ip.src==<internal_IP>` | Terminate connection, investigate host | Detects large outbound HTTP traffic from internal machines. |
| **ICMP Tunneling** | `icmp && data.len>100` | Block ICMP traffic, alert SOC | Detects abnormal ICMP packets used for covert channels. |
| **Unencrypted Credentials** | `http.request.method==POST && tcp.port==80` | Alert SOC, enforce HTTPS | Detects sensitive data sent over cleartext HTTP. |

---

## 📚 Glossary of Keywords
- [Wireshark](https://www.wireshark.org/) → [Wireshark Manual](Wireshark_Manual.md)  
- Capture Filters → Pre‑capture rules (see examples above)  
- Display Filters → Post‑capture rules (see examples above)  
- Protocol Filters → Built‑in keywords for TCP, DNS, HTTP, ICMP  

---

## 🎯 Conclusion
Wireshark filters are the **SOC analyst’s detection lens**.  
They reduce noise, isolate attacker traffic, and provide actionable insights for incident response.  

By documenting filters, screenshots, and playbooks, you prove your ability to perform **network detection and triage** — critical skills for SOC analysts.
