# AlienVault OTX Lab Setup – Beginner’s Manual

## 📖 Introduction
AlienVault Open Threat Exchange (OTX) is a **community-driven threat intelligence platform**.  
It provides Indicators of Compromise (IOCs) such as malicious IPs, domains, and file hashes, which SOC analysts can use to enrich detections and respond to incidents.  

In this lab, OTX helps you:
- Subscribe to threat feeds and watchlists
- Enrich Splunk alerts with IOC context
- Detect attacker infrastructure (C2 servers, phishing domains, malware hashes)
- Document threat intelligence integration for recruiter‑ready proof

By mastering OTX, you demonstrate the **threat intelligence and IOC enrichment skills recruiters expect** from SOC analysts.

---

## 🎯 Why This Lab Matters
- Shows ability to integrate external threat intelligence into SOC workflows  
- Provides visibility into attacker infrastructure beyond local logs  
- Builds proof of IOC enrichment and correlation with Splunk detections  

---

## 🏗️ OTX Components, Definitions, and Purpose

| Component | Definition | Purpose in Lab |
|-----------|------------|----------------|
| [AlienVault OTX](https://otx.alienvault.com/) | Threat intelligence platform with community‑shared IOCs. | Provides feeds of malicious IPs, domains, and hashes. |
| Pulses | Collections of related IOCs (IPs, domains, hashes). | Used to detect specific campaigns or malware families. |
| API Key | Authentication token for OTX integration. | Allows Splunk or scripts to query OTX feeds. |
| Watchlists | Custom IOC lists created by analysts. | Tailor threat intelligence to SOC needs. |
| Splunk Integration | Using OTX APIs or apps to enrich alerts. | Adds IOC context to Splunk detections for triage. |

---

## ⚙️ Step‑by‑Step Setup

### Step 1: Create OTX Account
- **What:** Access OTX threat feeds.  
- **How:**  
  1. Register at [OTX Portal](https://otx.alienvault.com/).  
  2. Generate your API key under account settings.  
- **Why:** Needed for Splunk or script integration.

---

### Step 2: Subscribe to Pulses
- **What:** Pulses are collections of IOCs.  
- **How:**  
  1. Search for relevant malware or campaign pulses.  
  2. Subscribe to them for automatic updates.  
- **Why:** Keeps your SOC updated with fresh threat intelligence.

---

### Step 3: Integrate OTX with Splunk
- **What:** Enrich Splunk alerts with IOC context.  
- **How:**  
  1. Install OTX Splunk app or use API queries.  
  2. Configure correlation searches to check logs against OTX IOCs.  
- **Why:** Adds external intelligence to local detections.

---

### Step 4: Build Watchlists
- **What:** Create custom IOC lists.  
- **How:** Add IPs, domains, or hashes from investigations.  
- **Why:** Tailors threat intelligence to your SOC environment.

---

## 🚨 Incident Response Playbooks with OTX

| Incident Type | OTX IOC | Detection (Splunk SPL) | Response | Purpose |
|---------------|---------|-------------------------|----------|---------|
| **Malicious IP Connection** | IP from OTX pulse | ```index=network_logs | search dest_ip IN [otx_ip_list]``` | Block IP, alert SOC | Detects outbound connections to known malicious IPs. |
| **Phishing Domain Access** | Domain from OTX pulse | ```index=dns_logs | search query IN [otx_domain_list]``` | Investigate user, block domain | Detects DNS queries to phishing domains. |
| **Malware Hash Execution** | File hash from OTX pulse | ```index=sysmon_logs EventID=1 | search Hash IN [otx_hash_list]``` | Quarantine host, hunt IOCs | Detects execution of known malware binaries. |
| **C2 Beaconing** | IP/domain from OTX | ```index=network_logs | stats count by src_ip dest_ip | where dest_ip IN [otx_c2_list]``` | Block outbound connection, escalate | Detects communication with command‑and‑control servers. |

---

## ✅ Validation Checklist
- [ ] OTX account created and API key generated  
- [ ] Subscribed to relevant pulses (malware, campaigns)  
- [ ] Splunk integration tested with IOC enrichment  
- [ ] Custom watchlists created for SOC environment  
- [ ] Playbooks validated with sample IOCs  
- [ ] Screenshots stored in `proof/` folder  

---

## 📚 Glossary of Keywords
- [AlienVault OTX](https://otx.alienvault.com/) → Threat intelligence platform  
- Pulses → Collections of IOCs for campaigns/malware families  
- API Key → Token for OTX integration with Splunk/scripts  
- Watchlists → Custom IOC lists tailored to SOC needs  
- Splunk Integration → Enrichment of alerts with OTX intelligence  

---

## 🎯 Conclusion
AlienVault OTX is the **SOC’s external intelligence feed**.  
It enriches detections with IOCs from global campaigns, helping analysts spot attacker infrastructure.  

By documenting OTX integration, pulses, and playbooks, you prove your ability to perform **threat intelligence enrichment and incident response** — critical skills for SOC analysts.

---

## 🤝 Connect With Me
- 🌐 GitHub: [LetsLearn-08](https://github.com/LetsLearn-08?tab=repositories)  
- 💼 LinkedIn: [Tanuja Reddy](https://www.linkedin.com/in/tanuja-reddy-03aa7b38a)
