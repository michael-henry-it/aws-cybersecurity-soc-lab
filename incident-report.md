# Incident Report: Brute-Force Attack Detection

## 📌 Summary

A brute-force attack was simulated against both Linux (SSH) and Windows (RDP) systems in an AWS environment. The activity was successfully detected using the Wazuh SIEM.

---

## 🕒 Timeline

- Reconnaissance performed using Nmap
- SSH brute-force attack executed using Hydra
- RDP brute-force attack executed using Hydra
- Logs generated on target systems
- Alerts triggered in Wazuh dashboard

---

## 🎯 Affected Systems

- Ubuntu Server (SSH)
- Windows Server 2022 (RDP)

---

## 🔍 Findings

### Linux (Ubuntu)

- Log Source: `/var/log/auth.log`
- Activity:
  - Multiple failed SSH login attempts
- Detection:
  - Wazuh alert triggered

---

### Windows Server

- Log Source: Windows Security Logs
- Event ID: 4625
- Activity:
  - Multiple failed RDP login attempts
- Detection:
  - Wazuh alert triggered

---

## 🌐 Source of Attack

- Origin: Kali Linux attacker machine
- Method: Hydra brute-force attack

---

## 🚨 Impact

- No successful compromise observed
- Attack successfully detected and logged
- Demonstrates vulnerability to brute-force attempts

---

## 🛠️ Recommendations

- Implement account lockout policies
- Restrict RDP access via firewall
- Use SSH key-based authentication
- Enable multi-factor authentication (MFA)
- Monitor failed login thresholds

---

## 🧠 Analyst Notes

This lab demonstrates the ability to:

- Simulate real-world attacks
- Analyze logs across platforms
- Validate SIEM detections
- Investigate authentication-based threats

---

## ✅ Conclusion

The SIEM successfully detected both SSH and RDP brute-force attacks, validating the effectiveness of centralized log monitoring and alerting.
