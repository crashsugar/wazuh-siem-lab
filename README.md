![Wazuh](https://img.shields.io/badge/SIEM-Wazuh-blue)
![Status](https://img.shields.io/badge/Project-Active-green)

## 📑 Table of Contents

- [Overview](#-wazuh-siem-lab)
- [Objectives](#-objectives)
- [Lab Architecture](#-lab-architecture)
- [Scenarios](#-scenarios)
- [Skills Demonstrated](#-skills-demonstrated)
- [Tools Used](#-tools-used)
- [Key Takeaways](#-key-takeaways)
- [Project Structure](#-project-structure)

---

# 🛡️ Wazuh SIEM Lab - Overview

This project demonstrates real-world security monitoring and threat detection using a Wazuh SIEM environment.

It includes multiple attack simulations and corresponding detection techniques commonly observed in Security Operations Centers (SOC).

---

## 🎯 Objectives

* Simulate real-world attack scenarios
* Detect malicious activity using SIEM (Wazuh)
* Analyze security events from Windows and Linux systems
* Map detections to MITRE ATT&CK framework

---

## 🏗️ Lab Architecture

* **Wazuh Manager** (Ubuntu Server)
* **Agents:**

  * Windows 10 endpoint
  * Ubuntu Linux endpoint
  * **Network:** Isolated virtual lab (VirtualBox)

        [ Attacker Machine ]
                 ↓
        --------------------
        |   Wazuh Manager  |
        --------------------
           ↓           ↓
   [ Windows Agent ]  [ Linux Agent ]
  
---

## 📂 Scenarios

### 🪟 Windows

* **Failed Logon Detection (Event ID 4625)**
  Detection of multiple failed login attempts indicating brute force attack.

👉 [`windows-failed-logon`](./windows-failed-logon)

---

### 🐧 Linux

* **SSH Brute Force Detection**
  Detection of repeated failed SSH authentication attempts.

👉 [`linux-ssh-bruteforce`](./linux-ssh-bruteforce)

* **Privilege Escalation (sudo abuse)**
  Detection of unauthorized or suspicious privileged command execution.

👉 [`linux-privilege-escalation`](./linux-privilege-escalation)

---

## 🧠 Skills Demonstrated

* Log analysis (Windows Event Logs & Linux auth logs)
* SIEM monitoring and alert investigation
* Threat detection and analysis
* MITRE ATT&CK mapping
* Incident analysis and reporting

---

## 🛠️ Tools Used

* Wazuh
* Linux (Ubuntu)
* Windows 10
* VirtualBox

---

## 🚨 Key Takeaways

* Centralized logging enables effective threat detection
* Even simple attacks (e.g., brute force) leave clear indicators
* Monitoring privileged activity is critical for detecting post-compromise behavior

---

## 📁 Project Structure

```text
wazuh-siem-lab/
├── windows-failed-logon/
├── linux-ssh-bruteforce/
├── linux-privilege-escalation/
```

---

## 📌 Future Improvements

* Persistence mechanisms detection
* File Integrity Monitoring (FIM)
* Lateral movement scenarios
* Active Directory integration

---

## 📬 Author


