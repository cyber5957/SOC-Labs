# 🔍 Splunk: The Basics – Data Ingestion & Basic Log Analysis

<p align="center">

![Splunk](https://img.shields.io/badge/SIEM-Splunk-orange?style=for-the-badge&logo=splunk)
![TryHackMe](https://img.shields.io/badge/TryHackMe-SOC%20Level%201-red?style=for-the-badge&logo=tryhackme)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)
![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-blue?style=for-the-badge)

</p>

---

## 📖 Overview

This lab was completed as part of the **TryHackMe SOC Level 1** learning path.

The objective was to learn how Security Information and Event Management (SIEM) platforms ingest machine data, create searchable indexes, and analyze VPN authentication logs using **Splunk Search Processing Language (SPL)**.

Throughout the lab, I uploaded JSON-based VPN logs, created a custom index, parsed structured log data, and performed multiple investigations to identify users, source IP addresses, and authentication events.

---

# 📑 Table of Contents

- 🎯 Objective
- 🛠 Lab Environment
- 📂 Dataset Overview
- 📥 Data Ingestion
- 🔍 Investigations
- 💻 SPL Queries
- 📸 Screenshots
- 🛡 SOC Analyst Perspective
- 🧠 Key Learnings
- 📚 References

---

# 🎯 Objective

The primary objective of this lab was to understand how Splunk collects, indexes, and searches machine-generated data.

After completing this exercise, I was able to:

✅ Upload external log files

✅ Create custom indexes

✅ Parse JSON logs

✅ Search events using SPL

✅ Investigate VPN authentication activity

---

# 🛠 Lab Environment

| Item | Value |
|------|-------|
| Platform | TryHackMe |
| Learning Path | SOC Level 1 |
| SIEM | Splunk Enterprise |
| Dataset | VPN Authentication Logs |
| Format | NDJSON |
| Index | VPN_Logs |

---

# 📂 Dataset Overview

The uploaded dataset contains VPN authentication events stored in newline-delimited JSON format.

Each event includes useful security fields such as:

- 👤 Username
- 🌍 Source Country
- 🌐 Source IP
- 🕒 Timestamp
- 🔐 Authentication Event

These logs can help identify unauthorized remote access and investigate suspicious login activity.

---

# 📥 Data Ingestion Workflow

The VPN logs were successfully uploaded into Splunk using the Upload wizard.

### Steps Performed

1. Opened **Add Data**
2. Selected **Upload**
3. Chose VPN log dataset
4. Verified JSON source type
5. Created **VPN_Logs** index
6. Completed upload
7. Opened Search & Reporting
8. Selected **All Time**
9. Verified imported events

---

## 📸 Screenshot
>
> <img width="1920" height="1040" alt="Screenshot (359)" src="https://github.com/user-attachments/assets/816e28a9-33a0-4354-b356-18a8b0dbc982" />


---

## 📸 Screenshot
>
> <img width="1920" height="1040" alt="Screenshot (360)" src="https://github.com/user-attachments/assets/51c82aaa-bcd9-42a4-b42a-b57c18361563" />


---

## 📸 Screenshot
>
> <img width="1920" height="1035" alt="Screenshot (361)" src="https://github.com/user-attachments/assets/b2fcf258-ee7a-4fa4-9296-5645b9e52b83" />


---

# 🔍 Investigation 01 — Verify Successful Import

### 🎯 Goal

Verify that every VPN authentication event was successfully imported.

## 💻 SPL Query

```spl
index=VPN_Logs
| stats count
```

### 📖 Explanation

This query searches every event stored inside the **VPN_Logs** index and returns the total event count.

### ✅ Result

> **2862 Events**

---

## 📸 Screenshot
>
> <img width="1920" height="1040" alt="Screenshot (362)" src="https://github.com/user-attachments/assets/8354a374-d88a-4d1b-bb57-8e516bee18c9" />


---

# 🔍 Investigation 02 — Search Events for User "Maleena"

### 🎯 Goal

Determine how many authentication events belong to the user **Maleena**.

## 💻 SPL Query

```spl
index=VPN_Logs
| spath
| search UserName="Maleena"
| stats count
```

### 📖 Explanation

The **spath** command parses JSON fields.

The **search** command filters events belonging to the specified user.

Finally, **stats count** returns the total matching events.

### ✅ Result

> **60 Events**

---

## 📸 Screenshot
>
> <img width="1920" height="1043" alt="Screenshot (363)" src="https://github.com/user-attachments/assets/0b33e604-771c-41f6-875f-f3c4dbc8cc54" />


---

# 🔍 Investigation 03 — Identify Username by Source IP

### 🎯 Goal

Determine which user authenticated from:

**107.14.182.38**

## 💻 SPL Query

```spl
index=VPN_Logs
| spath
| search Source_ip="107.14.182.38"
| stats values(UserName) as UserName count
```

### 📖 Explanation

This query searches all VPN events generated from the specified IP address and extracts the associated username.

### ✅ Result

> **Username:** Smith

---

## 📸 Screenshot
>
> <img width="1920" height="1038" alt="Screenshot (364)" src="https://github.com/user-attachments/assets/57235241-6af7-456c-85e3-242d323f31c0" />


---

# 🔍 Investigation 04 — Events Outside France

### 🎯 Goal

Count every VPN event originating outside France.

## 💻 SPL Query

```spl
index=VPN_Logs
| spath
| search Source_Country!="France"
| stats count
```

### 📖 Explanation

Filters all authentication events where the source country is **not France**.

### ✅ Result

> **2814 Events**

---

## 📸 Screenshot
>
> <img width="1920" height="1038" alt="Screenshot (365)" src="https://github.com/user-attachments/assets/bda665d1-b9dc-4649-a17f-ff0fabefb2ae" />


---

# 🔍 Investigation 05 — Count Events from a Specific IP

### 🎯 Goal

Count authentication events generated by:

**107.3.206.58**

## 💻 SPL Query

```spl
index=VPN_Logs
| spath
| search Source_ip="107.3.206.58"
| stats count
```

### 📖 Explanation

Returns the total authentication events generated by the specified source IP.

### ✅ Result

> 14 EVENTS

---

## 📸 Screenshot
>
> <img width="1920" height="1040" alt="Screenshot (366)" src="https://github.com/user-attachments/assets/080bfd3c-5d49-4a3d-81f2-2e570d34b20d" />


---

# 💻 SPL Commands Used

| Command | Purpose |
|-----------|----------|
| index | Search a specific index |
| search | Filter matching events |
| spath | Parse JSON fields |
| stats | Generate statistics |
| values() | Display unique values |

---

# 🛡 SOC Analyst Perspective

> 💡 **Why This Lab Matters**

VPN authentication logs are a valuable source of evidence during security investigations.

Using Splunk, analysts can:

- 🔐 Detect unauthorized VPN access
- 🌍 Identify suspicious login locations
- 🚨 Investigate compromised accounts
- 🌐 Track malicious IP addresses
- 📊 Correlate authentication events with other security logs
- 🛡 Support incident response investigations

These skills are fundamental for day-to-day work in a Security Operations Center (SOC).

---

# 🧠 Key Learnings

- ✅ Learned Splunk data ingestion workflow
- ✅ Created custom indexes
- ✅ Parsed structured JSON logs
- ✅ Performed log analysis using SPL
- ✅ Investigated authentication events
- ✅ Filtered logs using usernames and IP addresses
- ✅ Generated statistical summaries
- ✅ Strengthened SIEM investigation skills

---

# 🚀 Skills Demonstrated

- SIEM Operations
- Splunk Enterprise
- Search Processing Language (SPL)
- JSON Parsing
- VPN Log Analysis
- Threat Investigation
- Event Correlation
- Security Monitoring
- Blue Team Fundamentals

---

# 📚 References

- 📖 TryHackMe – Splunk: The Basics
- 📖 Splunk Enterprise Documentation
- 📖 SPL Search Reference

---

# 👨‍💻 Author

**Vinayak Chauhan**

🎓 BCA Cyber Security & Forensics

🛡 Aspiring SOC Analyst

💙 Blue Team | SIEM | Incident Response | Threat Detection

⭐ *Thank you for visiting this repository! If you found it useful, consider giving it a star.*
