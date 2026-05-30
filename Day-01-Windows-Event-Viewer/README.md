# Day 01 - Windows Event Viewer Fundamentals

## Lab Overview

This lab introduces Windows Event Viewer and demonstrates how Security Operations Center (SOC) analysts use Windows logs to investigate system activity, authentication events, and potential security incidents.

---

## Objectives

* Understand the purpose of Windows Event Viewer.
* Explore Windows log categories.
* Analyze Security Logs.
* Investigate Event IDs 4624, 4625, and 4688.
* Develop a basic SOC analyst mindset for log analysis.

---

## Tools Used

| Tool          | Purpose                            |
| ------------- | ---------------------------------- |
| Event Viewer  | Viewing and analyzing Windows logs |
| Windows 10/11 | Lab Environment                    |

---

## Key Event IDs Investigated

| Event ID | Description      | Importance                                                           |
| -------- | ---------------- | -------------------------------------------------------------------- |
| 4624     | Successful Logon | Tracks successful authentication attempts                            |
| 4625     | Failed Logon     | Helps identify unauthorized access attempts and brute-force activity |
| 4688     | Process Creation | Records when a process is executed                                   |

---

## Lab Procedure

### Step 1: Launch Event Viewer

1. Press `Win + R`
2. Enter:

```text
eventvwr.msc
```

3. Press Enter

---

### Step 2: Navigate to Security Logs

```text
Windows Logs
└── Security
```

The Security log contains authentication and security-related events.

---

### Step 3: Filter Specific Event IDs

Using **Filter Current Log**, search for:

```text
4624
4625
4688
```

---

## Findings

### Event ID 4624 - Successful Logon

**Description**

A successful authentication attempt was recorded.

**Observed Details**

| Field       | Value         |
| ----------- | ------------- |
| Username    | [ENTER VALUE] |
| Date & Time | [ENTER VALUE] |
| Logon Type  | [ENTER VALUE] |

**Analysis**

This event confirms that a user successfully authenticated to the system.

---

### Event ID 4625 - Failed Logon

**Description**

A failed authentication attempt was recorded.

**Observed Details**

| Field          | Value         |
| -------------- | ------------- |
| Username       | [ENTER VALUE] |
| Date & Time    | [ENTER VALUE] |
| Failure Reason | [ENTER VALUE] |

**Analysis**

Failed logon events can indicate incorrect credentials, password spraying, or brute-force activity when observed in large numbers.

---

### Event ID 4688 - Process Creation

**Description**

A new process was created on the system.

**Observed Details**

| Field          | Value         |
| -------------- | ------------- |
| Process Name   | [ENTER VALUE] |
| Parent Process | [ENTER VALUE] |

**Analysis**

Process creation events help analysts track application execution and identify suspicious activity.

---

## Screenshots

### Event Viewer Interface

![Event Viewer](screenshots/eventviewer-overview.png)

---

### Security Log

![Security Log](screenshots/security-log.png)

---

### Event ID 4624

![4624 Event](screenshots/eventid-4624.png)

---

### Event ID 4625

![4625 Event](screenshots/eventid-4625.png)

---

### Event ID 4688

![4688 Event](screenshots/eventid-4688.png)

---

## SOC Analyst Perspective

From a defensive security perspective:

* Event ID 4624 helps identify legitimate authentication activity.
* Event ID 4625 assists in detecting unauthorized access attempts.
* Event ID 4688 provides visibility into process execution.

These events are frequently used during incident investigations, threat hunting, and security monitoring.

---

## Key Takeaways

* Learned how to navigate Windows Event Viewer.
* Explored Security Logs.
* Investigated authentication-related events.
* Analyzed process creation events.
* Gained foundational knowledge required for SOC operations.

---

## Conclusion

Windows Event Viewer is a critical source of security telemetry for SOC analysts. Understanding authentication and process-related events is an essential first step toward effective log analysis, incident response, and threat detection.

---

## Author

**Vinayak Chauhan**

BCA Cyber Security & Digital Forensics Student
Aspiring SOC Analyst | Blue Teaming Enthusiast

