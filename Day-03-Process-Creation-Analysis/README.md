# Day 03 - Windows Process Creation Analysis (Event ID 4688)

## Overview

In this lab, I explored Windows Process Creation auditing and investigated Event ID 4688 within the Windows Security Log. The primary objective was to understand how Windows records process execution events and how SOC analysts leverage these logs during security investigations.

Since Process Creation Auditing was disabled by default on my Windows 11 Home system, I first configured the required auditing policy before generating and analyzing process creation events.

---

## Objectives

* Understand Event ID 4688 (Process Creation)
* Enable Process Creation Auditing
* Generate custom telemetry
* Analyze parent-child process relationships
* Investigate legitimate Windows processes
* Develop a SOC analyst mindset for process investigations

---

## Lab Environment

| Component             | Details              |
| --------------------- | -------------------- |
| Operating System      | Windows 11 Home      |
| Tool Used             | Event Viewer         |
| Log Source            | Windows Security Log |
| Event ID Investigated | 4688                 |

---

## Audit Configuration

### Initial Observation

During the initial investigation, no Event ID 4688 logs were present because Process Creation Auditing was not enabled.

### Verifying Audit Status

Command used:

```cmd
auditpol /get /subcategory:"Process Creation"
```

Result:

```text
No Auditing
```

---

### Enabling Process Creation Auditing

Command used:

```cmd
auditpol /set /subcategory:"Process Creation" /success:enable
```

---

### Verification

Command used:

```cmd
auditpol /get /subcategory:"Process Creation"
```

Result:

```text
Success
```

After enabling auditing, Windows successfully began recording Event ID 4688 entries within the Security Log.

---

## Event Investigation

### Event 1

| Field          | Value                       |
| -------------- | --------------------------- |
| Process Name   | C:\Windows\System32\mmc.exe |
| Parent Process | C:\Windows\explorer.exe     |
| Timestamp      | 01/06/2026 08:04:13 PM      |

#### Analysis

The process `mmc.exe` represents Microsoft Management Console, which is used to launch administrative tools such as Event Viewer, Device Manager, and Disk Management.

The parent process `explorer.exe` indicates that the application was launched through normal user interaction.

#### Assessment

✅ Legitimate Windows Activity

---

### Event 2

| Field          | Value                           |
| -------------- | ------------------------------- |
| Process Name   | C:\Windows\System32\consent.exe |
| Parent Process | C:\Windows\System32\svchost.exe |
| Timestamp      | 01/06/2026 08:04:13 PM          |

#### Analysis

The process `consent.exe` is associated with User Account Control (UAC) and is commonly observed when elevated privileges are requested.

The parent process `svchost.exe` is a legitimate Windows service host process.

#### Assessment

✅ Legitimate Windows Activity

---

### Event 3

| Field          | Value                       |
| -------------- | --------------------------- |
| Process Name   | C:\Windows\System32\mmc.exe |
| Parent Process | C:\Windows\explorer.exe     |
| Timestamp      | 01/06/2026 08:04:13 PM      |

#### Analysis

A second instance of Microsoft Management Console was observed.

The process relationship remained consistent with expected user activity involving Windows administrative tools.

#### Assessment

✅ Legitimate Windows Activity

---

## Custom Telemetry Generation

To generate additional Event ID 4688 entries, the following applications were manually executed:

* Notepad
* Calculator
* Command Prompt

Commands executed:

```cmd
whoami
hostname
```

These activities successfully generated additional process creation events and demonstrated how user actions are recorded within Windows Security Logs.

---

## Screenshots

### Event Viewer - Event ID 4688 Filter

<img width="1920" height="1080" alt="Screenshot (274)" src="https://github.com/user-attachments/assets/febbd41a-c6c1-42b1-acd4-d6ef4123670e" />


---

### Audit Policy Verification

<img width="1920" height="1080" alt="Screenshot (273)" src="https://github.com/user-attachments/assets/eda8e7ec-94ea-4c74-b595-2d20fcbbb669" />


---

### Event 1

<img width="1920" height="1080" alt="day3" src="https://github.com/user-attachments/assets/d96cc630-ea1e-4f71-aeda-bfb44c960507" />


---

### Event 2 - Consent Process Creation

<img width="1920" height="1080" alt="Screenshot (271)" src="https://github.com/user-attachments/assets/d0292641-5f41-44dd-a33d-e6a4b253e8a7" />


---

### Event 3

<img width="1920" height="1080" alt="Screenshot (272)" src="https://github.com/user-attachments/assets/a57bee4d-650b-4729-ae36-6fc2d12ced7f" />


---


## SOC Analyst Perspective

Process Creation logs provide valuable visibility into system activity and are frequently used during threat hunting, incident response, and malware investigations.

SOC analysts commonly investigate:

* Unexpected PowerShell execution
* Suspicious command-line activity
* Parent-child process anomalies
* Unauthorized software execution
* Potential malware behavior

Examples of suspicious process relationships may include:

* winword.exe → powershell.exe
* excel.exe → cmd.exe
* browser.exe → unknown executable

No suspicious behavior was identified during this investigation.

---

## Skills Learned

* Windows Audit Policy Configuration
* Event Viewer Navigation
* Event ID 4688 Analysis
* Process Monitoring
* Parent-Child Process Investigation
* Basic Threat Hunting Concepts
* Security Event Documentation

---

## Key Takeaways

* Process Creation Auditing is not always enabled by default.
* Event ID 4688 records program execution activity.
* Parent-child process relationships are critical during investigations.
* Legitimate Windows processes can be verified through contextual analysis.
* Process monitoring is a foundational SOC analyst skill.

---

## Conclusion

This lab provided practical experience enabling Windows auditing, generating process creation telemetry, and investigating Event ID 4688 logs. Through the analysis of legitimate Windows processes and manually generated activity, I gained a deeper understanding of process monitoring and its importance within a Security Operations Center (SOC) environment.

---

## Author

**Vinayak Chauhan**

BCA Cyber Security & Digital Forensics Student

Aspiring SOC Analyst | Blue Teaming Enthusiast
