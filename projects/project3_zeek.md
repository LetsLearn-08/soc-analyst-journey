# 🛡️ Project 3 – Zeek Threat Hunting (Delivery & Exploitation)

## 📖 Scenario Overview – The Four Characters

This project simulates detection of malicious activity during the **delivery and exploitation phases** of the attack lifecycle.  
Zeek was deployed on a monitoring interface to capture traffic between attacker and victim VMs, providing visibility into HTTP, DNS, SSL, and connection metadata.

- 👤 **Commoner (Employee / End User)**  
  Downloads files and browses websites, unknowingly exposing the network to malicious payloads.

- 🎭 **Attacker (Threat Actor)**  
  Hosts malicious files on a web server and attempts delivery via HTTP download.

- 👩‍💻 **Tier‑1 Analyst (First Responder)**  
  Detects unusual connections and suspicious downloads in Zeek logs.

- 👨‍💻 **Tier‑2 Analyst (Investigator)**  
  Confirms detections, maps them to **MITRE ATT&CK techniques**, and escalates for containment.

---

## 📖 Scenario Explained for Non‑Users (Manual Style)

This section explains the lab in simple terms, so even someone without cybersecurity experience can follow the story:

1. **The Setup**  
   - Imagine three computers:  
     - One attacker machine (Kali Linux) pretending to be a hacker.  
     - One victim machine (Windows) representing an employee’s computer.  
     - One monitoring machine (Ubuntu with Zeek) acting as the SOC sensor.  
   - The attacker sets up a fake website using Apache (a web server).  
   - The victim visits the site and downloads a file (`malicious.exe`).  
   - The monitoring machine (Zeek) watches all the network traffic between them.

2. **The Attack**  
   - The attacker places a malicious file on their web server.  
   - The victim unknowingly downloads it.  
   - This simulates how malware often enters a company network.

3. **The Detection**  
   - Zeek records every connection, DNS query, and SSL handshake.  
   - Analysts look at Zeek’s logs (`conn.log`, `dns.log`, `ssl.log`, `http.log`, `files.log`) to spot suspicious activity.  
   - For example:  
     - A strange domain in `dns.log`.  
     - A suspicious file download in `http.log`.  
     - A weak certificate in `ssl.log`.

4. **The Response**  
   - Analysts map detections to MITRE ATT&CK techniques.  
   - They recommend blocking malicious domains, investigating endpoints, and tuning detection rules.

---

## 🛠️ Tools & Environment Setup

- **Zeek**
  - Logs generated:
    - **conn.log** – TCP/UDP connection metadata
    - **dns.log** – DNS queries
    - **ssl.log** – TLS handshake details
    - **weird.log** – Protocol anomalies
    - **http.log / files.log** – Expected when HTTP/file traffic is captured

- **Traffic Simulation**
  - Kali VM hosts malicious payload via Apache (`malicious.exe`)
  - Windows VM downloads payload using PowerShell
  - Zeek sensor captures traffic on `enp0s8`

- **MITRE ATT&CK Mapping**
  - **T1071.001** – Application Layer Protocol: Web Traffic  
  - **T1071.004** – Application Layer Protocol: DNS  
  - **T1041** – Exfiltration Over C2 Channel  
  - **T1105** – Ingress Tool Transfer  
  - **T1587.003** – Develop Capabilities: Digital Certificates  

---

## 🔍 Detection Workflow

1. **Connection Monitoring**  
   Zeek logs TCP connections in `conn.log`.  
   Analysts detect unusual ports or repeated failed connections.

2. **DNS Visibility**  
   Zeek logs DNS queries in `dns.log`.  
   Analysts identify suspicious domains or algorithmically generated names.

3. **File Delivery**  
   Attacker hosts `malicious.exe` on Kali.  
   Zeek captures HTTP GET request in `http.log` and file metadata in `files.log`.

4. **SSL/TLS Inspection**  
   Zeek logs certificate details in `ssl.log`.  
   Analysts detect self‑signed or expired certificates.

---

## 📎 Evidence & Artifacts

All screenshots for this lab are stored in the [project3 folder](project3/).  

- `zeek-conn.png` → Connection metadata (conn.log)  
- `zeek-dns.png` → Suspicious DNS queries (dns.log)  
- `zeek-http.png` → Malicious file download (http.log)  
- `zeek-files.png` → File transfer metadata (files.log)  
- `zeek-ssl.png` → Certificate anomalies (ssl.log)  

---

## 🧑‍💻 Analyst Workflow

### Tier‑1 Analyst – Triage
![Zeek Connection Detection](project3/zeek-conn.png)  
*Tier‑1 analyst detects unusual outbound connections in Zeek conn.log.*

---

### Tier‑2 Analyst – Investigation
![Zeek DNS Detection](project3/zeek-dns.png)  
*Tier‑2 analyst confirms suspicious DNS queries mapped to MITRE ATT&CK T1071.004.*

---

### Tier‑3 Analyst – Validation & Response
![Zeek File Download Detection](project3/zeek-http.png)  
*Tier‑3 analyst validates malicious file download attempt mapped to MITRE ATT&CK T1105. Recommended response: block malicious domains, investigate endpoints, and tune detection rules.*

---

## 🗂️ MITRE ATT&CK Mapping
- **T1071.001 – Application Layer Protocol: Web Traffic**  
- **T1071.004 – Application Layer Protocol: DNS**  
- **T1041 – Exfiltration Over C2 Channel**  
- **T1105 – Ingress Tool Transfer**  
- **T1587.003 – Develop Capabilities: Digital Certificates**  

---

## ✅ Validation Checklist
- [x] Zeek deployed on correct interface (`enp0s8`)  
- [x] Connection logs captured (`conn.log`)  
- [x] DNS queries captured (`dns.log`)  
- [x] Malicious file hosted and downloaded (HTTP/file logs expected)  
- [x] SSL anomalies observed (`ssl.log`)  
- [x] Screenshots stored in `project3/` folder  
- [x] Analyst workflow mapped to MITRE ATT&CK  

---

## 📊 Detection Summary

| Stage              | Zeek Log   | Example Detection                                    | MITRE ATT&CK Mapping          | Evidence Screenshot       |
|--------------------|------------|------------------------------------------------------|--------------------------------|---------------------------|
| Connection Monitor | conn.log   | Unusual ports, repeated failed connections           | T1041 – Exfiltration           | proof/zeek-conn.png       |
| DNS Visibility     | dns.log    | Suspicious domains, algorithmic queries              | T1071.004 – DNS Protocol       | proof/zeek-dns.png        |
| File Delivery      | http.log   | GET request for malicious.exe                        | T1105 – Ingress Tool Transfer  | proof/zeek-http.png       |
| File Metadata      | files.log  | Malicious file transfer details                      | T1105 – Ingress Tool Transfer  | proof/zeek-files.png      |
| SSL Inspection     | ssl.log    | Self‑signed/expired certificates                     | T1587.003 – Certificates       | proof/zeek-ssl.png        |

---

### 🔑 Key Takeaways

| Lesson | Why It Matters | Example in This Project |
|--------|----------------|-------------------------|
| Interface selection | Visibility depends on correct NIC | `enp0s8` monitoring |
| Connection analysis | Reveals attacker behavior | conn.log anomalies |
| DNS monitoring | Detects suspicious domains | dns.log queries |
| File transfer detection | Identifies malicious payloads | http.log/files.log |
| SSL inspection | Exposes weak certificates | ssl.log anomalies |
| MITRE mapping | Standardized detection language | ATT&CK T1071, T1105 |

---

## 🎯 Conclusion
This lab demonstrates detection of **delivery and exploitation techniques** using Zeek.  
By correlating Zeek logs with simulated attacker traffic and mapping to MITRE ATT&CK, you prove your ability to perform **network‑based SOC detection and threat hunting** during the early attack lifecycle.

---

## 🤝 Connect With Me
- 🌐 GitHub: [LetsLearn-08](https://github.com/LetsLearn-08?tab=repositories)  
- 💼 LinkedIn: [Tanuja Reddy](https://www.linkedin.com/in/tanuja-reddy-03aa7b38a)  
