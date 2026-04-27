# 🔐 Wazuh SIEM Lab – Detection of Privilege Escalation (Linux)

## 📌 Overview

This project demonstrates detection and analysis of privilege escalation activity on a Linux system using Wazuh SIEM.

The objective was to simulate post-compromise behavior where a user attempts to execute commands with elevated privileges and verify detection through log monitoring and rule matching.

---

## 🏗️ Lab Environment

* SIEM: Wazuh Manager (Ubuntu Server)
* Target: Ubuntu Linux (Wazuh Agent)
* Scenario Type: Post-exploitation activity
* Network: Isolated lab (VirtualBox)

---

## 🎯 Attack Scenario

Privilege escalation was simulated using `sudo` to execute commands with root privileges.

### Commands executed:

```bash
sudo su
sudo cat /etc/shadow
sudo ls /root
```

These commands represent typical attacker behavior after gaining initial access.

---

## 🔍 Log Evidence (Linux)

System logs confirmed execution of privileged commands:

```text
sudo: user : TTY=pts/0 ; COMMAND=/bin/su
sudo: user : COMMAND=/usr/bin/cat /etc/shadow
```

Log location:

```bash
/var/log/auth.log
```

---

## 🚨 Detection in Wazuh

Wazuh successfully detected privilege escalation activity.

### Alert Details

* Rule Description: Sudo command executed
* Log Source: `sudo`
* Agent: Linux endpoint
* User: Local user account
* Event Type: Privileged command execution

---

## 🧠 Analysis

The activity indicates use of elevated privileges via `sudo`.

Key observations:

* Execution of sensitive commands
* Access to restricted files (`/etc/shadow`)
* Transition to root shell (`sudo su`)

This behavior is consistent with post-exploitation techniques used after initial system access.

---

## 🧠 Analyst Notes

This activity suggests that a user with valid credentials attempted to escalate privileges.

While `sudo` usage can be legitimate, execution of commands such as accessing `/etc/shadow` is highly suspicious and should be investigated.

No additional lateral movement or persistence mechanisms were observed in this scenario.

---

## 🧬 MITRE ATT&CK

| Tactic                        | Technique                             | ID    |
| ----------------------------- | ------------------------------------- | ----- |
| Privilege Escalation          | Exploitation for Privilege Escalation | T1068 |
| Defense Evasion / Persistence | Valid Accounts                        | T1078 |

---

## 🛠️ Detection Logic

The detection is based on:

* Monitoring `sudo` command execution
* Identifying access to sensitive system resources
* Correlating privileged actions with user activity

---

## 🚨 Severity Assessment

Medium → High

Escalates if:

* unauthorized user performs escalation
* escalation leads to further actions (persistence, lateral movement)

---

## 🛡️ Recommendations

* Restrict `sudo` access to required users only
* Monitor privileged command usage
* Implement least privilege principle
* Log and audit all administrative actions
* Use multi-factor authentication where possible

---

## 📸 Screenshots

Include:

* Terminal showing sudo commands
* `/var/log/auth.log`
* Wazuh alert detection

---

## ✅ Outcome

This lab confirms that:

* Privileged activity is correctly logged on Linux systems
* Wazuh detects and categorizes escalation attempts
* Security monitoring provides visibility into post-compromise behavior

---

## 📁 Next Steps

* Persistence mechanisms (cron jobs, services)
* Lateral movement simulation
* Correlation of multi-stage attacks
