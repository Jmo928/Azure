# 🛡️ Securing an Environment with Azure Security Center & Azure Sentinel

## 📄 Overview
This project demonstrates securing a cloud environment using **Azure Security Center** and **Azure Sentinel**. It simulates protecting customer data (e.g., Salesforce accounts) and detecting security incidents in Azure.

---

## 🧑‍💻 Key Highlights:
- **Azure Security Center** for cloud security posture management and recommendations.
- **Azure Sentinel** as a SIEM/SOAR platform for threat detection and response.
- **Data Protection**: Safeguarding customer account data (e.g., Salesforce).

---

## 🗄️ Sample Sensitive Data:
The included `Salesforce_Accounts_Import.csv` represents sample customer data that must be **protected**. This emphasizes the need for:
- **Access control** using Azure Security Center policies.
- **Threat detection** in case of unauthorized access via Azure Sentinel.

---

## 🛠️ Project Implementation Steps

### 1️⃣ **Azure Security Center Setup**
- Enable **Azure Security Center Standard Tier**.
- Enable **Azure Defender for Servers, Storage, and SQL**.
- Review **Secure Score** and apply recommendations:
  - Enable **Data Encryption at Rest**.
  - Configure **Role-Based Access Control (RBAC)** for Salesforce data.
  - Enable **MFA** for access to cloud resources.

Guide: [Setup Security Center](setup_security_center.md)

---

### 2️⃣ **Azure Sentinel Setup**
- Activate **Azure Sentinel** with a **Log Analytics Workspace**.
- Connect **Azure Activity**, **Azure AD**, and **Security Center** as data sources.
- Enable **Data Exfiltration Detection** and **Suspicious User Activity** analytics rules.
- Investigate and respond to alerts (e.g., unauthorized access to Salesforce data).

Guide: [Setup Azure Sentinel](setup_azure_sentinel.md)

---

### 3️⃣ **Data Protection Policy**
- Establish a **Data Protection Policy** for customer data (e.g., Salesforce):
  - Data classification (sensitive, confidential).
  - Access control & least privilege.
  - Logging and auditing access to customer data.

Policy: [Data Protection Policy](data_protection_policy.md)

---

## ⚙️ Sample Incident Analysis Script – `security_incident_analysis.py`
```python
import pandas as pd

# Simulated security alerts dataset
alerts_data = {
    'IncidentName': ['Unauthorized Access', 'Data Exfiltration', 'Malware on VM'],
    'Severity': ['High', 'High', 'Medium'],
    'Status': ['Active', 'Resolved', 'Active'],
    'Description': [
        'Suspicious access to Salesforce data',
        'Possible data exfiltration detected',
        'Malware detected on Azure VM'
    ]
}

alerts_df = pd.DataFrame(alerts_data)

# Display high-severity incidents
high_severity = alerts_df[alerts_df['Severity'] == 'High']

print("High-Severity Security Incidents:")
print(high_severity)
