# Incident-Response-Detection

# Incident Response: Detection with Wazuh

> **CompTIA Security+ (SY0-701) Assisted Lab**
>
> Learn how to use **Wazuh** to detect Indicators of Compromise (IoCs), analyze suspicious authentication events, monitor security alerts, and identify anti-forensics activities in a Windows environment. :contentReference[oaicite:0]{index=0}

---

## Lab Overview

In this lab, you will:

- Deploy and use the **Wazuh** security platform
- Detect suspicious login activity
- Analyze security alerts
- Review MITRE ATT&CK mappings
- Understand Wazuh Rule IDs
- Detect anti-forensics activity (log deletion)
- Practice incident detection and investigation

---

# Objectives

This lab covers the following Security+ objectives:

- **2.4** – Analyze indicators of malicious activity
- **3.2** – Apply security principles to enterprise infrastructure
- **4.4** – Security alerting and monitoring
- **4.5** – Modify enterprise security capabilities
- **4.8** – Incident response activities
- **4.9** – Use data sources during investigations :contentReference[oaicite:1]{index=1}

---

# Lab Environment

| Machine | Operating System | Purpose |
|----------|-----------------|----------|
| **KALI** | Kali Linux | Security workstation |
| **WAZUH** | Ubuntu Server | Security monitoring platform |
| **DC10** | Windows Server 2019 | Target system for attacks |

---

# Technologies Used

- Wazuh
- Kali Linux
- Windows Server 2019
- Hydra
- MITRE ATT&CK
- Windows Event Logs
- SIEM
- IDS
- SOAR

---

# What is Wazuh?

Wazuh is an **open-source security platform** built on OSSEC that combines multiple security capabilities into one solution.

Features include:

- Log Analysis
- Intrusion Detection (IDS)
- File Integrity Monitoring
- Vulnerability Detection
- Configuration Assessment
- Incident Response
- Compliance Monitoring

Wazuh can also integrate with:

- Elastic Stack
- Cloud environments
- Hybrid infrastructures

In many environments, Wazuh functions as a:

- SIEM
- IDS
- SOAR platform :contentReference[oaicite:2]{index=2}

---

# Indicators of Compromise (IoCs)

An **Indicator of Compromise (IoC)** is evidence that suggests malicious activity has occurred.

Examples include:

- Failed login attempts
- Successful logins after repeated failures
- Deleted audit logs
- Suspicious authentication
- Malware artifacts
- Unauthorized system changes

Wazuh continuously monitors systems for these indicators to support rapid incident detection. :contentReference[oaicite:3]{index=3}

---

# Exercise 1 – Detecting Logon Events

## Step 1

Create a custom password list by inserting the lab password into a wordlist.

Purpose:

- Prepare for a password guessing attack

---

## Step 2

Open the Wazuh Dashboard.

Login using:

- Username: **admin**
- Password: **Pa??w0rd**

---

## Step 3

View **Security Events**.

Filter events for:

- **DC10**

This allows you to monitor only the target machine.

---

## Step 4

Observe current security events.

Notice:

- Authentication events
- System events
- Log activity
- Event counters

---

# Simulating a Password Guessing Attack

Using **Hydra**, perform an RDP password guessing attack against:

- Target: **10.1.16.1**
- Username: **administrator**

Hydra attempts passwords until the correct password is discovered. :contentReference[oaicite:4]{index=4}

---

# Reviewing Wazuh Alerts

Refresh the dashboard after the attack.

You should observe:

- Authentication failures
- Authentication success
- Increased event count

---

## Important Rule IDs

| Rule ID | Meaning |
|----------|----------|
| **92652** | Successful password discovery |
| **60122** | Logon failure |
| **60106** | Successful logon |
| **63103** | Windows log file cleared |

:contentReference[oaicite:5]{index=5} :contentReference[oaicite:6]{index=6} :contentReference[oaicite:7]{index=7}

---

# Understanding Wazuh Alert Information

Each alert includes:

- Technique
- Tactic
- Description
- Severity Level

These fields help analysts quickly understand the detected activity.

---

# MITRE ATT&CK Integration

Wazuh maps alerts to the **MITRE ATT&CK** framework.

Benefits include:

- Standardized attack classifications
- Better threat understanding
- Faster investigations
- Improved incident response

However, mappings may not always perfectly represent the actual attack, so analysts should verify events using raw log data. :contentReference[oaicite:8]{index=8}

---

# Wazuh Alert Severity Levels

| Level | Severity |
|--------|----------|
| 0–3 | Informational |
| 4–7 | Low |
| 8–11 | Medium |
| 12–15 | High |
| 16 | Emergency |

These levels help prioritize incident response efforts. :contentReference[oaicite:9]{index=9}

---

# Understanding Wazuh Rules

Each Wazuh rule contains:

- Rule ID
- Description
- Severity Level
- Groups
- Frequency
- Timeframe
- Match Pattern
- Decoder
- Options
- MITRE ATT&CK ID

Organizations can also create **custom rules** tailored to their environment. :contentReference[oaicite:10]{index=10}

---

# Exercise 2 – Detecting Anti-Forensics

Attackers often attempt to hide evidence by deleting logs.

This is known as **anti-forensics**.

---

## Activity

Using Event Viewer on DC10:

- Open Windows Security Logs
- Clear the Security log

Return to Wazuh and search for:

**Rule ID: 63103**

Wazuh detects this activity and generates an alert indicating that a Windows log file was cleared. :contentReference[oaicite:11]{index=11}

---

# Skills Learned

By completing this lab, you practiced:

- Security monitoring
- SIEM analysis
- Authentication event analysis
- IoC detection
- MITRE ATT&CK analysis
- Password attack detection
- Windows log investigation
- Wazuh alert analysis
- Incident detection
- Anti-forensics detection

---

# Key Takeaways

- Wazuh automates security monitoring and incident detection.
- Authentication events are valuable Indicators of Compromise.
- MITRE ATT&CK provides useful context for detected threats.
- Alert severity helps prioritize incident response.
- Custom Wazuh rules improve detection accuracy.
- Deleting Windows logs is a strong indicator of suspicious activity.
- Effective detection is essential for successful incident response. :contentReference[oaicite:12]{index=12}

---

# Tools & Technologies

- Wazuh
- Kali Linux
- Windows Server 2019
- Hydra
- Windows Event Viewer
- MITRE ATT&CK
- SIEM
- IDS
- SOAR
- Windows Security Logs

---

## Repository Topics

`cybersecurity` `securityplus` `wazuh` `siem` `incident-response` `threat-detection` `mitre-attck` `hydra` `windows-security` `log-analysis` `soc` `soc-analyst` `blue-team` `kali-linux`
