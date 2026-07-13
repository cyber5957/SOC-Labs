# ⚡ Elastic Stack: The Basics – SIEM Fundamentals & Log Investigation

<p align="center">

![Elastic](https://img.shields.io/badge/SIEM-Elastic%20Stack-005571?style=for-the-badge&logo=elastic)
![TryHackMe](https://img.shields.io/badge/TryHackMe-SOC%20Level%201-red?style=for-the-badge&logo=tryhackme)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-orange?style=for-the-badge)

</p>

---

# 📖 Overview

This lab was completed as part of the **TryHackMe SOC Level 1** learning path.

The objective of this room was to understand the fundamentals of the **Elastic Stack (ELK)** and how Security Operations Center (SOC) analysts use it to collect, search, visualize, and investigate security logs.

During this lab, I explored the **Discover** tab, learned the basics of **Kibana Query Language (KQL)**, and created visualizations and dashboards to improve log analysis and monitoring.

---

# 📑 Table of Contents

- 🎯 Objective
- 🛠️ Lab Environment
- 🧩 Understanding the Elastic Stack
- 🔍 Discover Tab
- 💻 KQL Overview
- 📊 Creating Visualizations
- 📈 Creating Dashboards
- 📸 Screenshots
- 🛡️ SOC Analyst Perspective
- 🧠 Key Learnings
- 🚀 Skills Demonstrated
- 📚 References

---

# 🎯 Objective

The goal of this lab was to understand the core components of the Elastic Stack and learn how analysts use Kibana to investigate logs and visualize security data.

After completing this room, I was able to:

- ✅ Understand the Elastic Stack architecture
- ✅ Navigate Kibana
- ✅ Explore log data using the Discover tab
- ✅ Write basic KQL queries
- ✅ Create visualizations
- ✅ Build dashboards
- ✅ Understand how Elastic supports SOC investigations

---

# 🛠️ Lab Environment

| Item | Value |
|------|-------|
| Platform | TryHackMe |
| Learning Path | SOC Level 1 |
| SIEM | Elastic Stack (ELK) |
| Interface | Kibana |
| Query Language | KQL (Kibana Query Language) |
| Difficulty | Intermediate |

---

# 🧩 Understanding the Elastic Stack

The Elastic Stack, commonly known as **ELK**, is a collection of open-source tools used for centralized log collection, search, analysis, and visualization.

### Core Components

### 📥 Elasticsearch

Stores, indexes, and searches large volumes of machine-generated data efficiently.

### 📦 Logstash

Processes and transforms incoming log data before forwarding it to Elasticsearch.

### 📊 Kibana

Provides an interactive web interface for searching logs, creating visualizations, and building dashboards.

### 🚢 Beats

Lightweight data shippers that collect logs and system metrics from endpoints and forward them to Logstash or Elasticsearch.

---

## 📸 Screenshot
>
> <img width="1920" height="1080" alt="Screenshot (369)" src="https://github.com/user-attachments/assets/7c3966a6-f7a3-44ee-9b75-e8b2affd92bd" />


---

# 🔍 Discover Tab

## 🎯 Goal

Learn how to explore and investigate indexed log data using Kibana's Discover interface.

### What I Learned

- Search indexed events
- Filter logs using fields
- Modify time ranges
- Inspect individual events
- Explore event details
- Analyze log data efficiently

The Discover tab is one of the most frequently used interfaces by SOC analysts during investigations because it provides quick access to raw security events.

---

## 📸 Screenshot
>
> <img width="1920" height="1080" alt="Screenshot (370)" src="https://github.com/user-attachments/assets/21ca5b03-38ff-4770-8547-02ed59c8bdbc" />


---

# 💻 KQL (Kibana Query Language)

## 🎯 Goal

Learn how to filter and search log data using Kibana Query Language (KQL).

### Example Queries

```kql
event.category : authentication
```

```kql
host.name : "DC01"
```

```kql
source.ip : "192.168.1.10"
```

```kql
event.outcome : success
```

### 📖 Why KQL?

KQL allows analysts to quickly search structured log data without writing complex queries. It is commonly used for filtering events, locating suspicious activity, and supporting incident investigations.

---

## 📸 Screenshot
>
> <img width="1920" height="1080" alt="Screenshot (371)" src="https://github.com/user-attachments/assets/4c25bf87-b805-4de0-a919-bd395522d7b5" />
>
><img width="1920" height="1080" alt="Screenshot (372)" src="https://github.com/user-attachments/assets/a7c65f95-9282-4d80-afbe-2283725d36de" />



---

# 📊 Creating Visualizations

## 🎯 Goal

Understand how visualizations help analysts identify trends and patterns within security data.

### Types of Visualizations

- 📊 Bar Charts
- 🥧 Pie Charts
- 📈 Line Charts
- 📉 Area Charts
- 📋 Data Tables
- 🌍 Maps

Visualizations transform raw log data into meaningful insights, making it easier to detect anomalies and monitor security events.

---

## 📸 Screenshot
>
> <img width="1920" height="1080" alt="Screenshot (373)" src="https://github.com/user-attachments/assets/9114fcc9-8835-40ad-91e0-46155c03bea4" />
>
><img width="1920" height="1080" alt="Screenshot (374)" src="https://github.com/user-attachments/assets/28b05d20-a221-40b6-936a-2e86902298e6" />



---

# 📈 Creating Dashboards

## 🎯 Goal

Combine multiple visualizations into a centralized dashboard for monitoring security events.

### Dashboard Benefits

- Centralized monitoring
- Faster investigations
- Better visibility
- Executive reporting
- Security monitoring at a glance

Dashboards enable analysts to monitor key security metrics and quickly identify abnormal activity across an environment.

---

## 📸 Screenshot
>
> <img width="1920" height="1080" alt="Screenshot (375)" src="https://github.com/user-attachments/assets/dec565a0-50ee-411b-a628-73350b748329" />
>
> <img width="1920" height="1080" alt="Screenshot (376)" src="https://github.com/user-attachments/assets/e0d8ec7c-bff9-4628-9a10-8178f24d0641" />


---

# 🛡️ SOC Analyst Perspective

> 💡 **Why This Lab Matters**

Elastic Stack is widely used in enterprise environments to centralize log collection, monitor security events, and support threat detection.

As a SOC analyst, understanding Elastic enables you to:

- 🔍 Investigate security events
- 📊 Monitor dashboards
- 🚨 Detect suspicious activity
- 📝 Perform log analysis
- ⚡ Support incident response
- 📈 Identify trends using visualizations

The concepts learned in this lab are directly applicable to real-world SOC operations.

---

# 🧠 Key Learnings

- ✅ Understood Elastic Stack architecture
- ✅ Learned the role of Elasticsearch, Logstash, Kibana, and Beats
- ✅ Explored the Discover interface
- ✅ Performed searches using KQL
- ✅ Built visualizations
- ✅ Created dashboards
- ✅ Improved SIEM investigation skills

---

# 🚀 Skills Demonstrated

- Elastic Stack (ELK)
- Kibana
- Kibana Query Language (KQL)
- SIEM Operations
- Security Monitoring
- Log Investigation
- Data Visualization
- Dashboard Creation
- Blue Team Fundamentals

---

# 📚 References

- 📖 TryHackMe — Elastic Stack: The Basics
- 📖 Elastic Documentation
- 📖 Kibana Documentation

---

# 👨‍💻 Author

**Vinayak Chauhan**

🎓 BCA Cyber Security & Forensics

🛡️ Aspiring SOC Analyst

💙 Blue Team | SIEM | Threat Detection | Incident Response

---

⭐ **Thank you for visiting this repository! If you found it helpful, consider giving it a star.**
