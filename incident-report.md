# Incident Report: Brute Force Attack

## Summary
Detected brute-force login attempts targeting Linux and Windows systems.

## Source
IP: <attacker-ip>

## Timeline
- Initial detection: Kibana alert triggered
- Multiple failed SSH attempts observed
- Multiple failed RDP attempts observed

## Affected Systems
- Ubuntu Server
- Windows Server 2022

## Evidence
- /var/log/auth.log
- Event ID 4625

## Response
- Identified attacker IP
- Simulated blocking via Security Group

## Conclusion
Demonstrates detection and response to multi-system brute-force attack.
