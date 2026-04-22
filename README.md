# wazuh-siem-lab
SOC lab with Wazuh - attack simulations and detections

# 🛡️ Wazuh SIEM Lab – Detection of Failed Logon Attempts (Windows)

## 📌 Overview

This project demonstrates detection of failed logon attempts using a Wazuh SIEM lab environment.

The goal was to simulate a brute-force style attack and verify detection through log collection, rule matching, and alert generation.

---

## 🏗️ Lab Environment

* **SIEM**: Wazuh Manager (Ubuntu Server VM)
* **Agent 1**: Windows 10 VM
* **Agent 2**: Ubuntu VM
* **Network**: Internal LAN (VirtualBox)

---

## 🎯 Scenario: Failed Logon Simulation

A simulated attack was performed by generating multiple failed login attempts on a Windows endpoint.

### Steps:

1. Logged out from Windows session
2. Entered incorrect password multiple times (5–10 attempts)
3. Triggered Windows Security Event Log entries

---

## 🔍 Detection

Wazuh successfully detected the activity using built-in rules.

### Key Event:

* **Event ID**: 4625
* **Description**: An account failed to log on

### Wazuh Alert:

* **Rule Description**: Login failure
* **Agent Name**: Windows endpoint
* **Log Source**: Windows Security Log

---

## 🧠 Analysis

Multiple failed login attempts may indicate:

* Brute force attack
* Password spraying
* Unauthorized access attempts

---

## 🧬 MITRE ATT&CK Mapping

* **Technique**: T1110 – Brute Force
* **Tactic**: Credential Access

---

## 🚨 Severity

Medium (can escalate if repeated frequently)

---

## 🛠️ Recommendations

* Monitor repeated failed logins
* Implement account lockout policies
* Enable multi-factor authentication (MFA)
* Review logs for suspicious patterns

---

## 📸 Screenshots

(Add here:)

* Wazuh alert view
* Event details (4625)
* Dashboard overview

---

## ✅ Outcome

This lab confirms that:

* Wazuh correctly ingests Windows logs
* Detection rules are functioning
* SIEM pipeline works end-to-end

---

## 📁 Next Steps

* Simulate SSH brute force (Linux)
* Detect privilege escalation
* Build correlation rules
