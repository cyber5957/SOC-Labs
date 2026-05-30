Windows Event Viewer Fundamentals
Objective
The objective of this lab was to understand how Windows records system and security events and how a Security Operations Centre (SOC) analyst can use these logs during investigations.
________________________________________
Lab Environment
•	Operating System: Windows 10/11
•	Tool Used: Event Viewer
•	Date Performed: [05/30/2026]
________________________________________
Topics Covered
•	Introduction to Event Viewer
•	Windows Log Categories
•	Security Log Analysis
•	Event ID 4624 (Successful Logon)
•	Event ID 4625 (Failed Logon)
•	Event ID 4688 (Process Creation)
________________________________________
Procedure
Step 1: Open Event Viewer
1.	Press Win + R
2.	Type:
“eventvwr.msc”
3.	Press Enter
Step 2: Navigate to Windows Security Logs
Windows Logs → Security
Step 3: Filter Events
Used the "Filter Current Log" option to search for specific Event IDs.
Investigated:
•	4624 (successful login)
•	4625 (failed login)
•	4688 (process creation )
________________________________________
Findings
Event ID 4624 – Successful Logon
Description:
A successful authentication attempt was recorded.
Observations:
•	Username: [SENTINAL$]
•	Date & Time: [05/30/2026, 07:29:26 pm]
•	Logon Type: [Audit Success]
Analysis:
This event indicates a successful login to the system.
________________________________________
Event ID 4625 – Failed Logon
Description:
A failed authentication attempt was recorded.
Observations:
•	Username: [NIL]
•	Date & Time: [NIL]
•	Failure Reason: [NIL]
Analysis:
Failed logon events can be indicators of password guessing or brute-force activity when occurring in large numbers.
________________________________________
Event ID 4688 – Process Creation
Description:
A process was created on the system.
Observations:
•	Process Name: [NIL]
•	Parent Process: [NIL]
Analysis:
Process creation events help analysts track program execution and identify suspicious activities.
________________________________________
SOC Analyst Perspective
These events are important because:
•	4624 helps identify successful authentications.
•	4625 helps detect unauthorized access attempts.
•	4688 helps monitor process execution.
Together, these logs provide valuable visibility into system activity.
________________________________________
Key Takeaways
•	Learned how to use Event Viewer.
•	Understood the importance of Security Logs.
•	Investigated Event IDs 4624, 4625, and 4688.
•	Learned how Windows records authentication activity.
•	Gained foundational knowledge useful for SOC investigations.
________________________________________
Conclusion
This lab introduced Windows Event Viewer and the role of security logs in SOC operations. Understanding these events is a fundamental skill for log analysis, incident investigation, and threat detection.

