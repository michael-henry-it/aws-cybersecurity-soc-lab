# Wazuh Dashboard Overview

## 📊 Dashboard Purpose

The Wazuh dashboard provides centralized visibility into security events across Linux and Windows systems.

---

## 🧠 Key Views Used

### 1. Agents Status
- Displays connected endpoints
- Verified:
  - Ubuntu agent → Active
  - Windows agent → Active

---

### 2. Security Events

Used to detect brute-force attacks:

- SSH failures (Linux)
- RDP failures (Windows)

---

### 🔍 Filters Used

- Linux:
  - Authentication failures

- Windows:
  - Event ID: 4625

---

## 🚨 Detection Observed

### SSH Attack
- Multiple failed login attempts detected
- Source IP traced to attacker machine

---

### RDP Attack
- Event ID 4625 generated
- Multiple failed login attempts recorded
- Source IP visible in logs

---

## 📈 Outcome

- Successfully validated:
  - Log ingestion
  - Detection rules
  - Alert visibility

---

## 🧠 Key Takeaway
The dashboard confirms end-to-end detection from attack execution to SIEM alerting.
The dashboard confirms end-to-end detection from attack execution to SIEM alerting.
