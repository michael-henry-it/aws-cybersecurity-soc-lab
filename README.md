# AWS Cybersecurity SOC Lab (Attack & Detection Environment)

---

## Architecture Diagram

![Architecture Diagram](architecture-diagram.png)

---

## Overview

This project demonstrates a cloud-based Security Operations Center (SOC) lab environment built in AWS using Wazuh SIEM for centralized monitoring, log collection, and security event detection across Windows and Linux systems.

The lab simulates real-world attack scenarios including SSH and RDP brute-force attempts and validates detection through centralized SIEM alerting and log correlation workflows.
---

## Environment Architecture

## Attacker System

- Kali Linux
- Hydra
- Nmap

## Target Systems

- Ubuntu Server (SSH + Apache)
- Windows Server 2022 (RDP Enabled)

## SIEM Platform

- Wazuh Manager
- Wazuh Dashboard
- Wazuh Agents

---

## Technologies Used

- AWS EC2
- AWS VPC
- Wazuh SIEM
- Ubuntu Linux
- Windows Server 2022
- Hydra
- Nmap
- SSH
- RDP
- Windows Event Viewer
---

## Lab Workflow (Actual Execution Order)

1. Build AWS infrastructure (EC2 instances + networking)
2. Configure target systems (Ubuntu + Windows Server)
3. Deploy Wazuh SIEM (server + dashboard)
4. Install and configure Wazuh agents
5. Simulate attacks using Kali (Hydra + Nmap)
6. Validate logs on each target system
7. Confirm detection inside Wazuh dashboard

# Attack Simulation & Detection (STEP-BY-STEP)

---

## 1. Network Reconnaissance

Nmap scanning identified exposed services and attack surfaces including:

SSH (22) on Ubuntu
RDP (3389) on Windows Server

![Nmap Scan Ubuntu](screenshots/01-attacker-kali/nmap-scan-ubuntu.png)
![Nmap Scan Windows](screenshots/01-attacker-kali/nmap-scan-windows.png)

---

## 2. SSH Brute Force Simulation

Hydra was used to simulate brute-force authentication attempts against the Ubuntu SSH service.

## Log Validation

Linux authentication failures were confirmed through:

/var/log/auth.log

![Hydra SSH Attack](screenshots/01-attacker-kali/hydra-ssh-attack.png)

---

## 3. Linux Log Validation

- Checked `/var/log/auth.log`
- Observed multiple failed login attempts

![Ubuntu Auth Logs](screenshots/02-target-ubuntu/ubuntu-auth-log-failures.png)

---

## 4. RDP Brute Force Simulation

Hydra was used to simulate brute-force attempts against Windows RDP services.

## Log Validation

Windows authentication failures were analyzed using:

Windows Event Viewer
Event ID 4625

![Hydra RDP Attack](screenshots/01-attacker-kali/hydra-rdp-attack.png)

---

## 5. Windows Log Validation

- Opened Event Viewer → Security Logs
- Filtered for:

![Windows 4625 Logs](screenshots/03-target-windows/windows-4625-failures.png)

---

## 6. SIEM Monitoring and Detection

Wazuh successfully ingested, correlated, and alerted on:

- SSH brute-force activity
- RDP brute-force attempts
- Source IP identification
- Authentication failures across Linux and Windows systems

![Wazuh Dashboard](screenshots/04-wazuh-siem/wazuh-dashboard-login.png)
![Agents Active](screenshots/04-wazuh-siem/wazuh-agents-active.png)
![SSH Detection](screenshots/04-wazuh-siem/wazuh-ssh-detection.png)
![RDP Detection](screenshots/04-wazuh-siem/wazuh-rdp-detection.png)

---

# Detection Details
# Ubuntu Linux
- Log Source: /var/log/auth.log
- Detection: Failed SSH authentication attempts
- Result: Wazuh alert generation and event correlation

# Windows Server 2022
- Log Source: Windows Security Logs
- Event ID: 4625
- Detection: Failed RDP authentication attempts
- Result: Wazuh alert generation and centralized visibility
---

# SIEM Capabilities Demonstrated

- Centralized log collection
- Endpoint visibility and monitoring
- Real-time brute-force detection
- Cross-platform log correlation
- Security alert analysis
- Source IP tracking
- Dashboard-based monitoring workflows

---

# Troubleshooting and Operational Challenges

During deployment and testing, several infrastructure and configuration issues were identified and resolved, including:

- Wazuh agent misconfiguration (0.0.0.0)
- Agent version compatibility issues
- SSH authentication configuration
- AWS Security Group configuration
- Service availability and connectivity troubleshooting
---

# Incident Response Considerations

In a production SOC environment, additional response actions would include:

Investigating attacker IP reputation
Correlating activity across systems
Reviewing successful authentication attempts following failures
Applying account lockout policies
Escalating potential lateral movement activity

---

# Detection Enhancement Opportunities

Potential future improvements include:

- Alert thresholds for repeated failed logins
- Cross-system event correlation
- False-positive reduction tuning
- Automated response workflows
---

# Skills Demonstrated
- Security Information and Event Management (SIEM)
- AWS Infrastructure Deployment
- Linux Administration
- Windows Event Analysis
- Network Traffic Analysis
- Endpoint Monitoring
- Security Alert Correlation
- Incident Detection and Investigation
- Log Analysis
- Infrastructure Troubleshooting

# Screenshot Structure

/screenshots
├── 01-attacker-kali
├── 02-target-ubuntu
├── 03-target-windows
├── 04-wazuh-siem

---

# Summary

This project demonstrates a complete SOC monitoring workflow:

Attack Simulation → Log Generation → Log Collection → SIEM Detection → Alert Investigation

---

## 👤 Author

Michael Henry
