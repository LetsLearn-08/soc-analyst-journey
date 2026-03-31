# Nmap Manual – Beginner’s Guide

## 📖 Introduction
This manual explains how to use **Nmap (Network Mapper)** in your Incident Response Lab.  
Nmap is one of the most widely used tools for **network discovery, vulnerability scanning, and penetration testing**.  

By the end, you will:
- Understand how Nmap works and its role in attacker/defender workflows  
- Learn essential scanning techniques  
- Practice documenting scan results for SOC and incident response  

---

## 🎯 Why This Manual Matters
- Nmap is a **core skill recruiters expect** in cybersecurity roles  
- Demonstrates ability to perform reconnaissance and detect open ports/services  
- Provides proof of **network visibility and vulnerability assessment** in your lab  

---

## 🏗️ Components, Definitions, and Purpose

| Keyword / Tool | Definition | Purpose in Lab |
|----------------|------------|----------------|
| [Nmap](https://nmap.org/) | Open‑source network scanner used for host discovery and port scanning. | Identifies live systems, open ports, and services. |
| [Port Scanning](https://en.wikipedia.org/wiki/Port_scanner) | Technique to probe network ports for availability. | Detects services attackers may exploit. |
| [Service Detection](https://nmap.org/book/man-version-detection.html) | Nmap feature to identify applications running on ports. | Helps defenders know what software is exposed. |
| [OS Fingerprinting](https://nmap.org/book/man-os-detection.html) | Technique to guess the operating system of a host. | Provides attacker/defender context about target systems. |
| [Vulnerability Scanning](https://nmap.org/book/nse.html) | Using Nmap Scripting Engine (NSE) to detect known issues. | Identifies misconfigurations and CVEs. |
| [NSE (Nmap Scripting Engine)](https://nmap.org/book/nse.html) | Lua‑based scripting framework within Nmap. | Automates advanced scans like brute force or malware detection. |
| [Kali Linux](https://www.kali.org/) | Penetration testing distribution that includes Nmap. | Attacker VM for reconnaissance and exploitation. |
| [Metasploitable](https://information.rapid7.com/metasploitable-download.html) | Vulnerable Linux VM. | Safe target for Nmap scanning practice. |

---

## ⚙️ Step‑by‑Step Setup

### Step 1: Install Nmap
- **What:** Ensure Nmap is installed on Kali Linux.  
- **How:**
 ``` 
sudo apt update
sudo apt install nmap
```
- **Why:** Provides attacker/defender scanning capability.



### Step 2: Basic Host Discovery
- **What:** Identify live systems.  
- **How:**
``` 
nmap -sn 192.168.56.0/24
```
- **Why:** Detects which VMs are online in your lab network.



### Step 3: Port Scanning
- **What:** Scan for open ports.  
- **How:**
``` 
nmap -p 1-65535 192.168.56.106
```
- **Why:** Reveals services attackers may exploit; defenders can harden them.



### Step 4: Service & Version Detection
- **What:** Identify applications running on ports.  
- **How:**
``` 
nmap -sV 192.168.56.106
```
- **Why:** Helps defenders know what software is exposed and patch vulnerabilities.



### Step 5: OS Fingerprinting
- **What:** Guess operating system of target.  
- **How:**
``` 
nmap -O 192.168.56.106
```
- **Why:** Provides attacker context; defenders can confirm system inventory.



### Step 6: Vulnerability Scanning with NSE
- **What:** Use Nmap Scripting Engine.  
- **How:**
 ```  
nmap --script vuln 192.168.56.107
```
- **Why:** Detects known CVEs and misconfigurations on Metasploitable.



### Step 7: Documentation
- **What:** Save scan results.  
- **How:**
```  
nmap -sV -oN proof/nmap-scan.txt 192.168.56.107
```
- **Why:** Provides proof artifacts for recruiters and SOC workflows.

---

## 🚨 Incident Response Playbooks

| Incident Type | Detection | Response | Purpose |
|---------------|-----------|----------|---------|
| Unauthorized Port Exposure | Nmap scan shows open ports | Close ports, update firewall rules | Prevent exploitation. |
| Vulnerable Service | NSE script detects CVE | Patch/update service, IOC hunt | Reduce attack surface. |
| Rogue Host Discovery | Host appears unexpectedly in scan | Investigate, isolate, alert SOC | Detect lateral movement or unauthorized devices. |

- For more information can refer the :
  - [Nmap Scans](https://github.com/LetsLearn-08/Roadmap---Penetration-Testing/blob/48bc7e76f3d1229bb39f1bad65cac94b6984cbb9/nmap-scans/README.md)
  - [Incident Response Manual](https://github.com/LetsLearn-08/soc-analyst-journey/blob/7a5f3476c9062a26124e8b210961f6f639f345aa/INCIDENT-RESPOND-LABSETUP-MANUAL.md)
---

## ✅ Validation Checklist
- [ ] Nmap installed on Kali Linux  
- [ ] Host discovery tested (`-sn`)  
- [ ] Port scanning validated (`-p`)  
- [ ] Service detection performed (`-sV`)  
- [ ] OS fingerprinting tested (`-O`)  
- [ ] Vulnerability scan run with NSE  
- [ ] Results documented in `proof/` folder  

---

## 📚 Glossary of Keywords
- [Nmap](https://nmap.org/)  
- [Port Scanning](https://en.wikipedia.org/wiki/Port_scanner)  
- [Service Detection](https://nmap.org/book/man-version-detection.html)  
- [OS Fingerprinting](https://nmap.org/book/man-os-detection.html)  
- [Vulnerability Scanning](https://nmap.org/book/nse.html)  
- [NSE (Nmap Scripting Engine)](https://nmap.org/book/nse.html)  
- [Kali Linux](https://www.kali.org/)  
- [Metasploitable](https://information.rapid7.com/metasploitable-download.html)  

---

## 🎯 Conclusion
Nmap is a **foundational tool** for both attackers and defenders.  
By practicing host discovery, port scanning, service detection, OS fingerprinting, and vulnerability scanning, you gain **real‑world reconnaissance and incident response skills**.  

Document everything, store proof artifacts, and integrate results into your SOC workflows — this demonstrates professional readiness.

---

## 🤝 Connect With Me
- 🌐 GitHub: [LetsLearn-08](https://github.com/LetsLearn-08?tab=repositories)  
- 💼 LinkedIn: [Tanuja Reddy](https://www.linkedin.com/in/tanuja-reddy-03aa7b38a)  
