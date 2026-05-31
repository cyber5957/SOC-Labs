# Day 02 - Windows Authentication Log Analysis

## Overview

In this lab, I investigated Windows authentication events using Event Viewer to understand how successful and failed logon attempts are recorded within the Windows Security Log.

This exercise focused on Event IDs 4624 and 4625, which are commonly reviewed by SOC analysts during authentication-related investigations.

---

## Skills Practiced

* Windows Event Log Analysis
* Authentication Monitoring
* Event ID Investigation
* Logon Type Analysis
* Basic SOC Investigation Methodology

---

## Environment

| Component        | Details              |
| ---------------- | -------------------- |
| Operating System | Windows              |
| Tool Used        | Event Viewer         |
| Log Source       | Windows Security Log |

---

## Event ID 4624 - Successful Logon

### Findings

| Username  | Logon Type | Timestamp           |
| --------- | ---------- | ------------------- |
| SENTINAL$ | 5          | 31/05/2026 09:31:46 |
| SENTINAL$ | 5          | 31/05/2026 09:31:46 |
| SENTINAL$ | 5          | 31/05/2026 09:29:42 |

### Analysis

The account **SENTINAL$** generated multiple successful authentication events.

The account name ends with a dollar sign (`$`), which is commonly associated with system-managed or service accounts.

All observed events used:

**Logon Type 5 – Service Logon**

This logon type is typically generated when Windows services authenticate and start running.

### Assessment

✅ Expected Activity

No indicators of malicious behavior were identified.

---

## Event ID 4625 - Failed Logon

### Findings

| Account Name | Logon Type | Failure Reason                   | Timestamp           |
| ------------ | ---------- | -------------------------------- | ------------------- |
| SENTINAL$    | 2          | Unknown username or bad password | 31/05/2026 12:22:43 |
| SENTINAL$    | 2          | Unknown username or bad password | 31/05/2026 12:22:43 |

### Analysis

The failed authentication events were intentionally generated during testing.

Observed logon type:

**Logon Type 2 – Interactive Logon**

This indicates a local authentication attempt from a user interacting directly with the system.

Failure reason:

> Unknown username or bad password

This behavior is expected when incorrect credentials are entered.

### Assessment

✅ Benign Activity

The events were generated in a controlled testing environment and do not indicate malicious activity.

---

## Logon Types Observed

| Logon Type | Description       |
| ---------- | ----------------- |
| 2          | Interactive Logon |
| 5          | Service Logon     |

---

## Screenshots

### Event Viewer Overview

<img width="1920" height="1080" alt="Screenshot (262)" src="https://github.com/user-attachments/assets/478e5cf0-50f6-43e0-9e90-6cb38090e172" />


### Event ID 4624

<img width="1920" height="1080" alt="Screenshot (266)" src="https://github.com/user-attachments/assets/ec62642e-843d-4f54-bd86-a64a5218d54b" />

<img width="1920" height="1080" alt="Screenshot (267)" src="https://github.com/user-attachments/assets/1d515590-5438-4675-98f4-213b8d5390dd" />

<img width="1920" height="1080" alt="Screenshot (268)" src="https://github.com/user-attachments/assets/78ee23c1-7a06-4815-8a08-20109186f071" />


### Event ID 4625

<img width="1920" height="1080" alt="Screenshot (269)" src="https://github.com/user-attachments/assets/db931b98-f8c9-4a41-b44e-e3e798ff4d36" />


---

## Key Takeaways

* Investigated Windows authentication events.
* Analyzed successful and failed logon activity.
* Learned the difference between Interactive and Service Logons.
* Practiced identifying expected versus suspicious authentication behavior.
* Developed foundational SOC investigation skills.

---

## Conclusion

This lab provided hands-on experience analyzing Windows authentication events. Understanding Event IDs 4624 and 4625 is essential for monitoring login activity, investigating security incidents, and detecting potential unauthorized access attempts.

---

**Author:** Vinayak Chauhan

**Role:** Aspiring SOC Analyst | BCA Cyber Security & Digital Forensics Student
