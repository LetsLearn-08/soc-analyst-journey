# 🛠️ Cloud Security Monitoring – Lab Work (Phase 8)

## 📖 Overview
This lab demonstrates how to monitor cloud login events from **AWS** and **Azure** using **Splunk**.  
The objective is to ingest simulated failed login events, build dashboards, and configure alerts to detect suspicious activity.

---

## ⚙️ Setup Steps
1. Install Splunk on the SIEM VM.  
2. Enable **HTTP Event Collector (HEC)** for log ingestion.  
3. Generate test events using `curl` commands with AWS and Azure JSON logs.  
4. Create dashboards to visualize login activity.  
5. Configure alerts to trigger when >5 failed logins occur.  
6. Save screenshots as proof artifacts in the `proof8` folder.

---

## 🔍 Splunk Queries

### AWS Failed Logins
```spl
index=main source=aws_console
```
### Azure Failed Logins
```spl
index=main source=azure_signin
```
### Combined View
```spl
index=main (source=aws_console OR source=azure_signin)
```
Lateral Movement Detection
```spl
index=main (source=aws_console OR source=azure_signin)
| eval ip=coalesce(sourceIPAddress, ipAddress)
| iplocation ip
| stats dc(Country) as country_count values(Country) as countries by userIdentity.userName, userPrincipalName
| where country_count > 1
```

## 📊 Proof of Work – Screenshots (Phase 8)

All screenshots for this lab are stored in the [`proof8`](./proof8) folder.  
This folder contains complete visual evidence of Splunk setup, event generation, log ingestion, dashboard creation, and alert configuration.

👉 [View All Proof Screenshots](./proof8)

---

### 1. Splunk Setup
- **HEC Port Configuration** – `proof8/HEC-port.png`  
- **Token Creation** – `proof8/Token-creation.png`

---

### 2. Event Generation
- **AWS Batch JSON** – `proof8/aws-batch-json.png`  
- **Azure Batch JSON** – `proof8/azure-batch-json.png`  
- **Test Commands** – `proof8/test-commands.png`

---

### 3. Log Ingestion
- **AWS Events JSON** – `proof8/aws-events-json.png`  
- **Azure Events JSON** – `proof8/azure-events-json.png`  
- **Splunk Logs** – `proof8/splunk-logs.png`

---

### 4. Dashboard Creation
- **Dashboard Creation** – `proof8/dashboard-creation.png`  
- **AWS Failed Logins Dashboard** – `proof8/AWS-Failed-Logins-dashboard.png`  
- **Azure Failed Logins Dashboard** – `proof8/Azure-Failed-Login-dashboard.png`  
- **Combined Dashboard (AWS + Azure)** – `proof8/aws-console-or-azure-signin-splunk.png`  
- **Failed Logins Over Time** – `proof8/Failed-Logins-Over-Time.png`

---

### 5. Alert Configuration
- **Cloud Failed Login Alert Dashboard** – `proof8/cloud-failed-login-alert-dashboard.png`  
- **Splunk Alert** – `proof8/splunk-alert.png`  
- **Alert Generation** – `proof8/aplunk-alert-generation.png`

---

### 6. Validation
- **Console Login Test** – `proof8/console-login-test.png`  
- **Splunk Running** – `proof8/splunk-running.png`  
- **Splunk Console Login Events** – `proof8/splunk=console-login-events.png`  
- **Splunk Signin Logs** – `proof8/splunk-signin-logs.png`

---

## 🏁 Summary
These screenshots serve as **proof artifacts** for Phase 8. They demonstrate:
- Splunk setup and HEC configuration  
- Event generation and ingestion from AWS and Azure  
- Dashboard creation for failed logins  
- Alert configuration and validation  

Together, they show a complete workflow:  
**Cloud Events → Splunk Ingestion → Dashboard → Alert → Proof**


## 📚 Key Learnings
During this lab, the following skills and insights were gained:

- **Cloud IAM Fundamentals** – Understanding how AWS, Azure, and GCP manage identities, roles, and access policies.  
- **Event Simulation** – Generating failed login events in JSON format to replicate real‑world authentication scenarios.  
- **Log Ingestion with Splunk HEC** – Configuring Splunk’s HTTP Event Collector to receive cloud events securely.  
- **Dashboard Creation** – Building visual panels to monitor failed logins and authentication activity over time.  
- **Alerting Mechanisms** – Setting up automated alerts to detect brute force attempts or suspicious login behavior.  
- **Documentation Discipline** – Capturing and organizing proof artifacts (`proof8` folder) for validation and recruiter visibility.  

---

## 🏁 Conclusion
Phase 8 provided a **hands‑on introduction to cloud security monitoring**.  
By simulating login events from AWS and Azure, ingesting them into Splunk, and configuring dashboards and alerts, learners gained practical experience in detecting suspicious authentication activity.  

The structured documentation and proof artifacts demonstrate not only technical execution but also professional readiness for SOC analyst roles.  
This lab bridges theory with practice, reinforcing the importance of IAM, monitoring, and alerting in modern cloud environments.


## 🤝 Connect With Me
- 🌐 GitHub: [LetsLearn-08](https://github.com/LetsLearn-08?tab=repositories)  
- 💼 LinkedIn: [Tanuja Reddy](https://www.linkedin.com/in/tanuja-reddy-03aa7b38a)
