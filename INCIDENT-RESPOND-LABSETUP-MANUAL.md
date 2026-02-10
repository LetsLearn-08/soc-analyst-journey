# Incident Response Lab Setup – Beginner’s Manual

## 📖 Introduction
This manual explains how to set up an **Incident Response Lab** — a safe environment to learn how cyberattacks happen and how defenders respond.  
Think of it as your personal **mini SOC (Security Operations Center)**.  

By the end, you will:
- Understand attacker vs. defender workflows
- Learn how logs are collected and analyzed
- Practice responding to simulated incidents

---

## 🏗️ Lab Components, Definitions, and Purpose

| Keyword / Tool | Definition | Purpose in Lab |
|----------------|------------|----------------|
| [VirtualBox](https://en.wikipedia.org/wiki/VirtualBox) | Free virtualization software that lets you run multiple operating systems (VMs) on one computer. | Hosts all your lab machines in one place. |
| [Virtual Machine (VM)](https://en.wikipedia.org/wiki/Virtual_machine) | A simulated computer running inside VirtualBox. | Each VM plays a role: attacker, victim, or defender. |
| [Sysmon (System Monitor)](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon) | A Windows tool from Microsoft Sysinternals that logs detailed system activity (processes, network connections, file changes). | Provides forensic visibility into suspicious activity. |
| [Splunk Enterprise](https://en.wikipedia.org/wiki/Splunk) | A SIEM (Security Information and Event Management) tool that ingests logs, correlates events, and raises alerts. | Acts as the central brain of your SOC. |
| [Splunk Universal Forwarder](https://docs.splunk.com/Documentation/Forwarder) | Lightweight Splunk agent installed on endpoints. | Sends logs from VMs to Splunk for analysis. |
| [Metasploitable](https://information.rapid7.com/metasploitable-download.html) | A deliberately vulnerable Linux VM. | Safe target for exploitation practice. |
| [Kali Linux](https://en.wikipedia.org/wiki/Kali_Linux) | A penetration testing distribution. | Attacker machine with tools like Nmap, Metasploit, Burp Suite. |
| [Static IP](https://en.wikipedia.org/wiki/IP_address#Static_IP_addresses) | A fixed network address assigned to a VM. | Ensures consistent communication between machines. |
| [Incident Response Playbook](https://www.cisa.gov/resources-tools/resources/incident-response-playbook) | A documented step‑by‑step guide for handling specific attack scenarios. | Standardizes detection and response actions. |

---

## ⚙️ Step‑by‑Step Setup

### Step 1: Install VirtualBox
- **What:** Download and install VirtualBox.  
- **How:** Visit [VirtualBox official site](https://www.virtualbox.org/), install for your OS.  
- **Why:** You need a platform to run multiple VMs simultaneously.

---

### Step 2: Create VMs
- **Windows VM (Victim)** → Install Windows, enable Sysmon, forward logs.  
- **Kali Linux VM (Attacker)** → Install Kali, use tools like Nmap to simulate attacks.  
- **Splunk SIEM VM (Defender)** → Install Splunk Enterprise, configure to receive logs.  
- **Metasploitable VM (Target)** → Vulnerable machine for exploitation practice.  

**Why:** Each VM plays a role in the attack‑defense cycle.

---

### Step 3: Configure Networking
- **What:** Assign **static IPs** to each VM.  
- **Definition:** A static IP is a fixed address for a machine on the network.  
- **How:** In VirtualBox → Network settings → Manual IP assignment.  
- **Why:** Ensures consistent communication between attacker, victim, and SIEM.

---

### Step 4: Install Sysmon on Windows VM
- **What:** Sysmon logs detailed system activity.  
- **How:**  
  1. Download Sysmon from [Microsoft Sysinternals](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon).  
  2. Use a config file with rules (e.g., log process creation, network connections).  
  3. Run:  
     ```
     sysmon -accepteula -i sysmonconfig.xml
     ```
- **Why:** Without Sysmon, you’d miss critical forensic details like which process opened a suspicious connection.

---

### Step 5: Install Splunk Enterprise (SIEM VM)
- **What:** Splunk ingests and analyzes logs.  
- **How:**  
  1. Install Splunk Enterprise on your SIEM VM.  
  2. Enable **receiver port** (default: 9997).  
  3. Validate with:  
     ```
     netstat -an | grep 9997
     ```
- **Why:** Splunk is your central dashboard for incident detection.

---

### Step 6: Install Splunk Universal Forwarder (Windows VM)
- **What:** Forwarder sends logs to Splunk.  
- **How:**  
  1. Install Splunk Universal Forwarder.  
  2. Configure `outputs.conf` to point to Splunk SIEM IP and port.  
  3. Validate with:  
     ```
     splunk list forward-server
     ```
- **Why:** Without forwarding, Splunk won’t receive endpoint logs.

---

### Step 7: Configure Kali Linux (Attacker VM)
- **What:** Kali provides attacker tools.  
- **How:**  
  - Install/update tools:  
    ```
    apt install nmap metasploit-framework burpsuite
    ```  
  - Use Nmap for scanning, Metasploit for exploitation, Burp Suite for web attacks.  
- **Why:** Simulating attacks helps defenders practice detection and response.

---

### Step 8: Set Up Metasploitable (Target VM)
- **What:** Vulnerable Linux VM.  
- **How:**  
  - Download Metasploitable image from [Rapid7](https://information.rapid7.com/metasploitable-download.html).  
  - Run in VirtualBox with static IP.  
- **Why:** Provides a safe target for exploitation practice.

---

### Step 9: Documentation
- **What:** Store all screenshots in `proof/` folder.  
- **How:** Label screenshots clearly (e.g., `Windows-Sysmon-Install.png`).  
- **Why:** Documentation proves your work and helps recruiters validate skills.

---

## 🚨 Incident Response Playbooks

| Incident Type | Definition | Detection | Response | Purpose |
|---------------|------------|-----------|----------|---------|
| [Phishing](https://en.wikipedia.org/wiki/Phishing) | Fraudulent emails tricking users into revealing info. | Email logs, Sysmon process | Quarantine, user alert | Train defenders to spot malicious emails. |
| [Brute Force Attack](https://en.wikipedia.org/wiki/Brute-force_attack) | Repeated login attempts to guess passwords. | Authentication logs | Account lockout, SIEM alert | Prevent unauthorized access. |
| [Malware](https://en.wikipedia.org/wiki/Malware) | Malicious software designed to damage systems. | Sysmon + Splunk correlation | Isolate host, IOC hunt | Contain and eradicate infection. |

---


## ✅ Validation Checklist
- [ ] All VMs configured with static IPs  
- [ ] Sysmon installed with correct rules  
- [ ] Splunk ingestion validated for Windows & Linux logs  
- [ ] Incident playbooks drafted and tested  
- [ ] Screenshots stored in `proof/` and linked in README  

---

## 📚 Glossary of Keywords
- [VirtualBox](https://en.wikipedia.org/wiki/VirtualBox)  
- [Virtual Machine](https://en.wikipedia.org/wiki/Virtual_machine)  
- [Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)  
- [Splunk Enterprise](https://en.wikipedia.org/wiki/Splunk)  
- [Splunk Universal Forwarder](https://docs.splunk.com/Documentation/Forwarder)  
- [Metasploitable](https://information.rapid7.com/metasploitable-download.html)  
- [Kali Linux](https://en.wikipedia.org/wiki/Kali_Linux)  
- [Static IP](https://en.wikipedia.org/wiki/IP_address#Static_IP_addresses)  
- [Incident Response Playbook](https://www.cisa.gov/resources-tools/resources/incident-response-playbook)  
- [Phishing](https://en.wikipedia.org/wiki/Phishing)  
- [Brute Force Attack](https://en.wikipedia.org/wiki/Brute-force_attack)  
- [Malware](https://en.wikipedia.org/wiki/Malware)  

---

## 🎯 Conclusion
This lab setup teaches you the **foundations of incident response**:
- **What to do:** Configure attacker, victim, and defender machines.  
- **How to do it:** Step‑by‑step installation and configuration.  
- **Why it matters:** Builds real‑world SOC skills in a safe environment.  

Document everything, test playbooks, and practice repeatedly — that’s how you grow from beginner to professional in cybersecurity.

