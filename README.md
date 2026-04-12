# AWS Cybersecurity SOC Lab (Attack & Detection Environment)

![AWS Cyber Lab Architecture](aws-cyber-lab-architecture.png)

---

## 🚨 Overview

This project simulates a real-world Security Operations Center (SOC) environment built in Amazon Web Services (AWS). It demonstrates both offensive security techniques and defensive detection using centralized logging and SIEM tools.

---

## 🔥 What This Demonstrates

* Simulated real-world cyber attacks (Nmap, Hydra)
* Detected threats using SIEM (ELK Stack)
* Correlated attacks across Linux and Windows systems
* Built full cloud infrastructure in AWS (VPC, subnets, routing, security groups)
* Implemented alerting and incident response workflow

---

## 🧠 Architecture

* AWS VPC (10.0.0.0/16)
* Kali Linux (Attacker)
* Ubuntu Server (Linux Target)
* Windows Server 2022 (Target)
* Internet Gateway + Route Tables
* Security Groups (Controlled Access)

---

## ⚔️ Attack Simulation

* Network reconnaissance using **Nmap**
* Brute-force attacks using **Hydra**

  * SSH (Linux)
  * RDP (Windows)

---

## 🔍 Detection & Logging

### Linux

* Log file: `/var/log/auth.log`
* Detected failed SSH login attempts

### Windows

* Event Viewer → Security Logs
* Event ID **4625** (Failed logins)

---

## 📊 SIEM Integration (ELK Stack)

To simulate a real SOC, the lab integrates the ELK Stack:

* **Elasticsearch** – log storage and indexing
* **Logstash** – log ingestion and parsing
* **Kibana** – visualization dashboards

### Log Sources

* Linux: `/var/log/auth.log`
* Windows: Security logs via Winlogbeat

### Detection Logic

* Failed SSH login attempts
* Failed RDP login attempts
* Brute-force thresholds (>5 attempts per minute)

---

## 🚨 Alerts & Detection

Implemented alerting in Kibana:

* Trigger: More than 5 failed login attempts within 1 minute
* Queries:

  * `"Failed password"` (Linux)
  * `event.code:4625` (Windows)

---

## 🧪 Attack Scenario

1. Kali Linux performs reconnaissance using Nmap
2. Hydra executes brute-force attacks against SSH and RDP
3. Logs are generated on Ubuntu and Windows systems
4. ELK Stack ingests and analyzes logs
5. Alerts trigger for suspicious activity
6. Activity is investigated and documented

---

## 📊 Dashboard Example

![Kibana Dashboard](screenshots/kibana-dashboard.png)

---

## 📝 Incident Response Workflow

1. **Detection** – Alert triggered in SIEM
2. **Triage** – Identify source IP and affected systems
3. **Investigation** – Analyze logs in Kibana
4. **Correlation** – Link Linux + Windows attack activity
5. **Response** – Simulated blocking of attacker IP

---

## 🛠 Tools Used

* Nmap
* Hydra
* ELK Stack (Elasticsearch, Logstash, Kibana)
* Winlogbeat
* AWS (EC2, VPC, Security Groups)

---

## 💡 Key Skills Demonstrated

* AWS Networking (VPC, Subnets, Routing, Security Groups)
* Offensive Security (Scanning, Brute Force Attacks)
* Log Analysis & Threat Detection
* SIEM Implementation (ELK Stack)
* Incident Response & Correlation

---

## 🔁 How to Reproduce

1. Launch EC2 instances (Kali, Ubuntu, Windows)
2. Configure Security Groups (SSH, RDP, internal traffic)
3. Run attacks from Kali:

   ```
   nmap <target>
   hydra -l ubuntu -P rockyou.txt ssh://<target>
   ```
4. Monitor logs:

   * `/var/log/auth.log`
   * Windows Event Viewer
5. View logs in Kibana dashboard

---

## 👤 Author

Michael Henry

