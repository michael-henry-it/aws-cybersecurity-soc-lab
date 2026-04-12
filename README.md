# AWS-Lab
AWS Lab for cybersecurity
# AWS Cybersecurity Lab (Attack & Detection Environment)

## Overview
This project demonstrates a hands-on cybersecurity lab built in Amazon Web Services (AWS). The lab simulates real-world attack scenarios and detection techniques using cloud infrastructure.

## Architecture
- AWS VPC (10.0.0.0/16)
- Kali Linux (Attacker)
- Ubuntu Server (Linux Target)
- Windows Server 2022 (Target)
- Internet Gateway + Route Tables
- Security Groups (Controlled Access)

## Attack Simulation
- Network scanning using Nmap
- Brute-force attacks using Hydra (SSH & RDP)

## Detection & Logging
### Linux
- Log file: `/var/log/auth.log`
- Detected failed SSH login attempts

### Windows
- Event Viewer → Security Logs
- Event ID 4625 (Failed logins)

## SIEM & Monitoring (Extended)
- AWS CloudWatch (log monitoring)
- ELK Stack (optional enhancement)
  - Elasticsearch
  - Logstash
  - Kibana

## Key Skills Demonstrated
- Cloud Networking (VPC, Subnets, Routing)
- Offensive Security (Nmap, Hydra)
- Log Analysis & Threat Detection
- Windows & Linux Security Monitoring

## Lab Diagram
![Architecture](diagram.png)

## How to Reproduce
1. Launch EC2 instances (Kali, Ubuntu, Windows)
2. Configure Security Groups (SSH, RDP, internal traffic)
3. Run attacks from Kali:
   - `nmap <target>`
   - `hydra -l ubuntu -P rockyou.txt ssh://<target>`
4. Monitor logs on Ubuntu and Windows

## Author
Michael Henry
