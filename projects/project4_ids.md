# 🛡️ Project 4 – IDS Deployment & Rule Writing

## 🌟 Intro 

Every attacker leaves a trail — the question is, can you see it? In this project, I stepped into the defender’s shoes. I deployed **Suricata IDS** on Ubuntu, wrote my own 
detection rules, and then used Kali to simulate attacks. The story is simple: Kali tried to sneak in with pings, port scans, and suspicious HTTP requests… but Suricata caught every move.

---


## 📖 Scenario Overview – The Three Characters

This project simulates how a defender sets up an **Intrusion Detection System (IDS)** to catch attacker activity in real time.  
The story unfolds as a cat‑and‑mouse chase between attacker and defender:

- 🎭 **Attacker (Kali VM)**  
  Launches reconnaissance and probing attacks: ICMP pings, Nmap port scans, suspicious HTTP requests, and Netcat connections.

- 🛡️ **Defender (Ubuntu IDS VM)**  
  Runs Suricata IDS with custom rules to monitor traffic and detect malicious activity.

- 👩‍💻 **SOC Analyst (You)**  
  Observes Suricata alerts, maps detections to MITRE ATT&CK techniques, and documents proof for recruiter‑ready evidence.

---

## 🛠️ Tools & Environment Setup

- **Suricata IDS (Ubuntu VM)**  
  - Version: 7.0.3  
  - Custom rules for ICMP, port scans, and HTTP suspicious requests  
  - Logs stored in `/var/log/suricata/fast.log`

- **Kali Attacker VM**  
  - Tools: `nmap`, `curl`, `netcat`  
  - Used to simulate attacker traffic

- **Apache2 Web Server (Ubuntu VM)**  
  - Installed to open port 80 for HTTP detection

---


## 🛡️ Custom Suricata Rules

```
alert icmp any any -> $HOME_NET any (msg:"ICMP Ping Detected"; sid:1000001; rev:1;)
alert tcp any any -> $HOME_NET 80 (msg:"HTTP Suspicious Request"; content:"cmd.exe"; sid:1000002; rev:1;)
alert tcp any any -> $HOME_NET any (msg:"Port Scan Detected"; flags:S; threshold:type both, track by_src, count 5, seconds 60; sid:1000003; rev:1;)
```
---

## 🚀 Attack Simulation

From Kali VM:
```
ping -c 4 192.168.56.102
nmap -sS 192.168.56.102
curl http://192.168.56.102/cmd.exe
nc -v 192.168.56.102 80
```

---


## 🔍 Detection Workflow

1. **Connectivity Check**  
   - Verified VM communication between Kali and Ubuntu IDS.  
   - Evidence: `connection.png`, `ping-google.png`.

2. **Tool Installation & Verification**  
   - Installed Nmap, Curl, and Netcat on Kali.  
   - Confirmed versions and readiness for attack simulation.  
   - Evidence: `nmap-curl-nc-version.png`, `linux-netcat-install.png`.

3. **IDS Setup**  
   - Installed Suricata on Ubuntu (`ubuntu-suricata-install.png`).  
   - Wrote custom detection rules (`suricata-rules.png`).  
   - Started Suricata engine (`suricata-engine.png`).

4. **Attack Simulation (Kali VM)**  
   - ICMP ping to IDS (`ping -c 4`).  
   - Nmap SYN scan (`nmap -sS`).  
   - HTTP suspicious request (`curl http://192.168.56.102/cmd.exe`).  
   - Netcat connection to port 80 (`nc -v`).  
   - Evidence: `nmap-curl-nc-attacks.png`.

5. **Detection & Logging (Ubuntu IDS)**  
   - Suricata captured alerts in `fast.log`.  
   - ICMP ping, port scan, and HTTP suspicious request all detected.  
   - Evidence: `fast-log.png`, `fast-log-traffic.png`.

6. **Analyst Review**  
   - Tier‑1 triaged Suricata alerts.  
   - Tier‑2 correlated multiple detections to attacker IP `192.168.56.104`.  
   - Tier‑3 validated rules and mapped activity to MITRE ATT&CK.  
   - Evidence: `suricata-engine.png`, `fast-log.png`, `suricata-rules.png`.


---

## 🧑‍💻 Analyst Workflow

### Tier‑1 Analyst – Triage
![Suricata Engine Started](project4/suricata-engine.png)  
*Tier‑1 analyst sees Suricata engine running and begins monitoring `fast.log` for alerts. Initial detections of ICMP traffic confirm that the IDS is active and logging.*

---

### Tier‑2 Analyst – Investigation
![Suricata Fast Log Output](project4/fast-log.png)  
*Tier‑2 analyst correlates alerts: ICMP ping, port scan attempts, and suspicious HTTP requests. Evidence shows attacker IP `192.168.56.104` probing the IDS with multiple techniques.*

---

### Tier‑3 Analyst – Validation & Response
![Suricata Rules File](project4/suricata-rules.png)  
*Tier‑3 analyst validates that custom rules triggered correctly. Activity is mapped to MITRE ATT&CK techniques (T1016, T1046, T1190). Recommended response: block attacker IP, tune detection rules, and document findings.*


---

## 📎 Evidence & Artifacts

👉 All screenshots for this lab are stored in the [project4 folder](https://github.com/LetsLearn-08/soc-analyst-journey/tree/main/project4).  
Browse the folder directly to review the full set of evidence images.

- `connection.png` → VM connectivity check  
- `ping-google.png` → Internet connectivity test  
- `nmap-curl-nc-version.png` → Tool installation verification  
- `nmap-curl-nc-attacks.png` → Attack simulation from Kali  
- `suricata-engine.png` → Suricata engine started  
- `suricata-rules.png` → Custom rules file  
- `fast-log.png` → Suricata log output  
- `fast-log-traffic.png` → Detailed traffic alerts  
- `ubuntu-suricata-install.png` → IDS installation proof  
- `ubuntu-apache2-install.png` → Apache setup for HTTP detection  
- `linux-netcat-install.png` → Netcat installation proof  
- `linux-upgrade.png`, `ubuntu-upgrade-1.png`, `ubuntu-upgrade-2.png` → System updates  

---

## 🗂️ MITRE ATT&CK Mapping
- **T1016 – System Network Configuration Discovery** → ICMP Ping Detected  
- **T1046 – Network Service Scanning** → Port Scan Detected  
- **T1190 – Exploit Public‑Facing Application** → HTTP Suspicious Request  

---

## ✅ Validation Checklist
- [ ] Suricata installed and running on Ubuntu IDS  
- [ ] Custom rules written and loaded  
- [ ] Apache2 installed to open port 80  
- [ ] Kali attacker traffic simulated (ping, nmap, curl, nc)  
- [ ] Suricata alerts captured in `fast.log`  
- [ ] Screenshots stored in `project4/` folder  
- [ ] MITRE ATT&CK mapping documented  



## 📊 Detection Summary

| Stage                  | Tool/Command | Suricata Rule | MITRE ATT&CK Mapping          | Evidence Screenshot            |
|-------------------------|--------------|---------------|--------------------------------|--------------------------------|
| ICMP Ping               | `ping`       | ICMP rule     | T1016 – Network Discovery      | project4/connection.png         |
| Port Scan               | `nmap -sS`   | Port scan rule| T1046 – Service Scanning       | project4/nmap-curl-nc-attacks.png |
| HTTP Suspicious Request | `curl`       | HTTP rule     | T1190 – Exploit Public App     | project4/fast-log.png           |
| Netcat Connection       | `nc -v`      | TCP rule      | T1046 – Service Scanning       | project4/linux-netcat-install.png |



### 🔑 Key Takeaways

| Lesson | Why It Matters | Example in This Project |
|--------|----------------|-------------------------|
| IDS visibility is critical | Detects attacker traffic in real time | Suricata alerts for ping, scan, HTTP |
| Custom rules enhance detection | Tailored to lab scenarios | ICMP, port scan, HTTP suspicious request |
| Attack simulation validates setup | Proof of detection workflow | Kali VM attacks logged in fast.log |
| MITRE mapping adds context | Standardized language for recruiters | T1016, T1046, T1190 |
| Documentation builds credibility | Recruiter‑ready evidence | Screenshots + README.md |



## 🎯 Conclusion
This lab demonstrates how an IDS can be deployed, tuned with custom rules, and validated against attacker traffic.  
By simulating attacks from Kali and capturing Suricata alerts, you prove your ability to perform **SOC detection, rule writing, and incident analysis**.  
The defender’s eye is open — Suricata caught every move.

---

## 🤝 Connect With Me
- 🌐 GitHub: [LetsLearn-08](https://github.com/LetsLearn-08?tab=repositories)  
- 💼 LinkedIn: [Tanuja Reddy](https://www.linkedin.com/in/tanuja-reddy-03aa7b38a)  

