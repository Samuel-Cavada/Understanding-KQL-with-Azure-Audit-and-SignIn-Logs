<p align="center">
  <a href="https://github.com/Samuel-Cavada" target="_blank">
    <img src="https://img.shields.io/badge/Back_to_Main_Page-000000?style=for-the-badge&logo=github&logoColor=white" alt="Back to Main Page"/>
  </a>
</p>

<h1 align="center">Understanding KQL with Azure Audit and SignIn Logs</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white" alt="Cloud Platform" />
  <img src="https://img.shields.io/badge/OS-N/A-0078D6?style=for-the-badge&logo=windows&logoColor=white" alt="OS" />
  <img src="https://img.shields.io/badge/Tool-Azure%20Monitor-00B388?style=for-the-badge&logo=microsoftazure&logoColor=white" alt="Tool" />
  <img src="https://img.shields.io/badge/Tool-PowerShell-2C5EA8?style=for-the-badge&logo=powershell&logoColor=white" alt="Tool" />
  <img src="https://img.shields.io/badge/Focus-KQL%20and%20Log%20Analytics-orange?style=for-the-badge" alt="Focus Area" />
</p>

---

## 📌 Project Objective
> Develop familiarity with Kusto Query Language (KQL) by querying and interpreting Azure Entra ID (formerly Azure Active Directory) Sign-in and Audit logs. This project prepares for future labs involving Microsoft Defender for Endpoint (MDE) integration.

---

## 🧰 Tools & Technologies
- **Platform:** Azure
- **OS:** N/A
- **Tools:** Azure Monitor, Log Analytics, Entra ID Logs, PowerShell
- **Languages/Scripts:** KQL

---

## 🧠 Skills Gained / Focus Areas
- Queried Azure Entra ID Sign-in and Audit logs using KQL
- Interpreted filtered results by user and time window
- Summarized geolocation data from sign-in attempts
- Prepared for log-based threat hunting and VM onboarding to MDE

---

## 🧪 Environment Setup
> Accessed Azure Entra ID portal and connected to Log Analytics Workspace. Viewed live SignInLogs and AuditLogs for specific users and actions. Azure Monitor and KQL were used to search and summarize activity.

![Environment Setup](assets/images/setup.jpg)

---

## 🛠️ Walkthrough
1. [Step 1: View Logs](#step-1-view-logs)
2. [Step 2: Analyze Query](#step-2-analyze-query)
3. [Step 3: Modify for Future Use](#step-3-modify-for-future-use)

---

### ✅ Step 1: View Logs
> - Navigated to **Microsoft Entra ID** → **Monitoring** → **Sign-in logs** and **Audit logs**  
> - Reviewed recent activity by user and service  
> - Enabled diagnostic settings if needed to route logs to Log Analytics

![Step 1](assets/images/step1.jpg)

---

### ✅ Step 2: Analyze Query
> Examined the following KQL query:
```kql
let target_upn = "josh.cyber.test_gmail@lognpacific.com";
SigninLogs
| where UserPrincipalName == target_upn and TimeGenerated > ago(30m)
| summarize loginCount = count() by UserPrincipalName, Country = tostring(LocationDetails['countryOrRegion'])
```

> **Purpose:**
> - Filters sign-in logs for a specific user within the last 30 minutes
> - Counts total login attempts
> - Summarizes results by country

---

### ✅ Step 3: Modify for Future Use
> - Practiced modifying UPN, time window, and summary fields  
> - Explored use cases for failed sign-ins, MFA status, app access  
> - Prepared to onboard virtual machines to Microsoft Defender for Endpoint (MDE) in follow-up labs

![Step 3](assets/images/step3.jpg)

---

## 📝 Outcomes and Lessons Learned
- **Technical Insight:** KQL enables efficient log filtering and analysis within Azure environments.
- **Configuration Skills:** Navigated Entra ID logs and customized queries in Log Analytics.
- **Troubleshooting:** Understood how to filter logs by time and user context to validate activity.
- **Takeaway:** Mastery of log queries is essential for incident response and proactive threat hunting.

---

## 📎 References
- [Kusto Query Language Reference](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/)
- [Azure Sign-in Logs Overview](https://learn.microsoft.com/en-us/entra/idp/monitor-view-sign-ins)
- [Audit Logs in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/idp/monitor-view-audit-logs)
