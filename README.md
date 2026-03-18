# ☁️ CloudGuard – Azure Secure Cloud Infrastructure

> **Enterprise-style Azure security project built from scratch — covering networking, monitoring, alerting, governance, and security posture management.**

📖 [Full Case Study](https://prasanth-portfolio-blond.vercel.app/blog/azure-secure-storage-architecture) &nbsp;|&nbsp; 🔗 [LinkedIn (https://www.linkedin.com/in/prasanthpanneer/) 💼 Open to Azure Administrator & Cloud Engineer roles

![Azure](https://img.shields.io/badge/Cloud-Microsoft%20Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Security](https://img.shields.io/badge/Focus-Cloud%20Security-green?style=for-the-badge)
![Monitoring](https://img.shields.io/badge/Monitoring-Log%20Analytics-orange?style=for-the-badge)
![RBAC](https://img.shields.io/badge/Governance-RBAC%20%7C%20Policy-red?style=for-the-badge)
![Defender](https://img.shields.io/badge/Security-Defender%20for%20Cloud-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge)

---

## 📋 Table of Contents

- [About This Project](#-about-this-project)
- [Why This Project Stands Out](#-why-this-project-stands-out)
- [Architecture Overview](#-architecture-overview)
- [Skills Demonstrated](#-skills-demonstrated)
- [Project Phases](#-project-phases)
  - [Phase 1 – Infrastructure Setup](#phase-1--infrastructure-setup)
  - [Phase 2 – Network Security & Monitoring](#phase-2--network-security--monitoring)
  - [Phase 3 – Cloud Security Monitoring & Log Analytics](#phase-3--cloud-security-monitoring--log-analytics)
  - [Phase 4 – Alerting & Incident Notifications](#phase-4--alerting--incident-notifications)
  - [Phase 5 – Security & Governance](#phase-5--security--governance-custom-rbac--azure-policy)
  - [Phase 6 – Defender for Cloud](#phase-6--microsoft-defender-for-cloud)
- [Tools & Services Used](#-tools--services-used)
- [What I Learned](#-what-i-learned)
- [Interview Summary](#-interview-summary)

---

## 🎯 About This Project

**CloudGuard** is a hands-on Microsoft Azure project that simulates a real-world enterprise cloud security environment — built entirely from scratch using the Azure Portal, with zero coding required.

This project was designed to reflect exactly what **Azure Administrators and Cloud Engineers** do in production:

- 🔒 Secure the network with VNet segmentation and NSG rules
- 📊 Build centralized monitoring and log pipelines
- 🚨 Configure automated alerting for incident detection
- 🛡️ Enforce least-privilege access with custom RBAC roles
- 📋 Automate governance with Azure Policy
- 🔍 Assess and improve security posture with Defender for Cloud

**Built by:** Prasanth | Fresher targeting Azure Administrator & Cloud Engineer roles  
**Timeline:** Completed across 6 structured phases  
**Cost:** $0 — built entirely within the Azure free tier

---

## 🌟 Why This Project Stands Out

Most beginner Azure portfolios show basic VM deployments or static websites. CloudGuard is different:

| What Most Beginners Build | What CloudGuard Demonstrates |
|---|---|
| VM deployment | Full security monitoring pipeline |
| Storage account | Custom RBAC roles (least privilege) |
| Static website | Azure Policy governance enforcement |
| Basic networking | KQL-based security investigation |
| — | Incident alerting with Action Groups |
| — | Defender for Cloud posture management |

This project tells a **complete enterprise security story** — from infrastructure to compliance.

---

## 🏗️ Architecture Overview

![Secure Azure Infrastructure Architecture](https://prasanth-portfolio-blond.vercel.app/static/images/azure-secure-storage-architecture.png)

```
Azure Subscription
        │
        ├── Resource Group (CloudGuard-Sec-RG)
        │         │
        │         ├── Virtual Network (10.0.0.0/16)
        │         │         ├── Public Subnet (10.0.1.0/24)
        │         │         └── Private Subnet (10.0.2.0/24)
        │         │                   └── NSG (IP Whitelisting /32)
        │         │
        │         └── Storage Account
        │
        ├── Log Analytics Workspace (law-phase3-monitoring)
        │         └── Diagnostic Settings → Activity Logs
        │                   └── KQL Security Queries
        │
        ├── Azure Monitor
        │         └── Alert Rules → Action Groups → Email Notifications
        │
        ├── Azure RBAC
        │         └── Custom Role (phase5-monitor-reader)
        │
        ├── Azure Policy
        │         └── Require Environment Tag (Subscription scope)
        │
        └── Microsoft Defender for Cloud
                  └── Secure Score + Compliance Dashboard
```

---

## 🛠️ Skills Demonstrated

| Category | Skills |
|---|---|
| **Networking** | VNet design, subnet segmentation, NSG rules, IP whitelisting |
| **Monitoring** | Log Analytics Workspace, Diagnostic Settings, Azure Monitor |
| **Investigation** | KQL queries, activity log analysis, failed operation detection |
| **Alerting** | Alert Rules, Action Groups, email incident notifications |
| **Access Control** | Custom RBAC roles, least-privilege principle, IAM |
| **Governance** | Azure Policy, resource tagging enforcement |
| **Security Posture** | Microsoft Defender for Cloud, Secure Score, compliance mapping |

---

## 📁 Project Phases

---

### Phase 1 – Infrastructure Setup

**Objective:** Build the foundational Azure environment with secure network segmentation.

Created a dedicated Resource Group, deployed a Virtual Network with isolated public and private subnets, and provisioned a Storage Account and Log Analytics Workspace as the foundation for all subsequent phases.

**Resources Created:**
- Resource Group: `CloudGuard-Sec-RG`
- Virtual Network: `10.0.0.0/16`
  - Public Subnet: `10.0.1.0/24`
  - Private Subnet: `10.0.2.0/24`
- Storage Account
- Log Analytics Workspace

**Screenshots:**

Resource Group Creation
![Resource Group](screenshots/phase-1/03-RG-Created.png)

Virtual Network Configuration
![VNet](screenshots/phase-1/01_VNet_Config.png)

Virtual Network Success
![VNet Success](screenshots/phase-1/02_VNet_Success.png)

Storage Account Setup
![Storage](screenshots/phase-1/Phase1_Storage_Config.png)

Storage Account Success
![Storage Success](screenshots/phase-1/Phase1_Storage_Success.png)

Log Analytics Workspace
![Log Analytics](screenshots/phase-1/02_LogAnalytics_Success.png)

---

### Phase 2 – Network Security & Monitoring

**Objective:** Harden the network with NSG rules and validate monitoring pipeline functionality.

Configured Network Security Group rules to restrict inbound traffic using IP whitelisting (/32 CIDR), attached the NSG to the private subnet, enabled diagnostic settings, and validated log ingestion using KQL queries. Reviewed security posture using Microsoft Defender for Cloud.

**Key Implementations:**
- Inbound NSG rules with strict IP whitelisting (/32 CIDR)
- NSG attached to private subnet
- Diagnostic settings enabled — logs streamed to Log Analytics
- KQL queries to confirm log ingestion
- Defender for Cloud initial security posture review

**Screenshots:**

NSG Inbound Rule Configuration
![NSG](screenshots/phase-2/02_NSG_InboundRule_Config.png)

NSG Attached to Subnet
![NSG Subnet](screenshots/phase-2/05_Subnet_NSG_Attached.png)

KQL Log Validation
![Logs](screenshots/phase-2/P2-KQL-NSG-Log-Validation.png)

Microsoft Defender Secure Score
![Defender](screenshots/phase-2/P2-Defender-Overview-SecureScore.png)

Architecture Resource Visualizer
![Architecture](screenshots/phase-2/P2-Architecture-ResourceVisualizer.png)

---

### Phase 3 – Cloud Security Monitoring & Log Analytics

**Objective:** Build a centralized security monitoring pipeline using Azure Activity Logs and KQL.

Deployed a dedicated Log Analytics Workspace and configured diagnostic settings to stream all Azure Activity Logs (administrative, security, policy, health) into the workspace. Used KQL to investigate administrative events, detect resource write operations, and query for failed operations — simulating real SOC analyst workflows.

**Resources Created:**
- Resource Group: `rg-phase3-monitoring`
- Log Analytics Workspace: `law-phase3-monitoring`
- Diagnostic Setting: `activitylog-to-law`

**KQL Queries Used:**

```kql
-- Recent activity investigation
AzureActivity
| sort by TimeGenerated desc
| limit 50

-- Resource modification monitoring
AzureActivity
| where OperationNameValue contains "write"
| sort by TimeGenerated desc
| limit 20

-- Failed operations detection
AzureActivity
| where ActivityStatusValue == "Failed"
| sort by TimeGenerated desc
```

> 💡 **Real-world note:** After configuring diagnostic settings, Azure required several minutes to ingest logs before queries returned results. This ingestion delay is expected behaviour in production environments — and knowing this demonstrates genuine hands-on experience.

**Screenshots:**

Resource Group Created
![Resource Group](screenshots/phase-3/phase3-01-resource-group-created.png)

Log Analytics Workspace
![Log Analytics](screenshots/phase-3/phase3-02-log-analytics-workspace.png)

Activity Log Diagnostic Setting
![Diagnostic Setting](screenshots/phase-3/phase3-03-activity-log-export.png)

Activity Query Results
![Activity Query](screenshots/phase-3/phase3-04-activity-query.png)

Resource Write Query Results
![Write Query](screenshots/phase-3/phase3-05-resource-write-query.png)

Failed Operations Query
![Failed Query](screenshots/phase-3/phase3-06-failed-operations-query.png)

---

### Phase 4 – Alerting & Incident Notifications

**Objective:** Implement automated incident detection and administrator notification using Azure Monitor.

Configured an Alert Rule targeting Azure Activity Logs to detect administrative error events. Created an Action Group to automatically send email notifications when the alert fires — completing the incident response loop from detection to notification.

**Alert Rule Configuration:**

| Setting | Value |
|---|---|
| Alert Rule Name | `phase4-admin-change-alert` |
| Signal Type | Activity Log |
| Category | Administrative |
| Event Level | Error |
| Scope | Azure Subscription |
| Action Group | `ag-admin-alerts` |
| Notification | Email |

**Screenshots:**

Action Group Created
![Action Group Created](screenshots/phase-4/phase4-action-group-created.png)

Alert Action Group Configuration
![Alert Action Group](screenshots/phase-4/phase4-alert-action-group.png)

Alert Condition – Admin Operations
![Alert Condition](screenshots/phase-4/phase4-alert-condition-admin-operations.png)

Alert Rule Created
![Alert Rule](screenshots/phase-4/phase4-alert-rule-created.png)

Alert Scope – Subscription
![Alert Scope](screenshots/phase-4/phase4-alert-scope-subscription.png)

---

### Phase 5 – Security & Governance (Custom RBAC + Azure Policy)

**Objective:** Enforce least-privilege access control and automated governance across the Azure subscription.

Created a **custom RBAC role** (`phase5-monitor-reader`) with only the minimum permissions required for infrastructure visibility — no write or delete access. Assigned the role at subscription scope. Then implemented **Azure Policy** to enforce mandatory resource tagging across the entire subscription, ensuring governance compliance for all deployed resources.

**Custom RBAC Role – `phase5-monitor-reader`:**

| Permission | Purpose |
|---|---|
| `Microsoft.Resources/subscriptions/resourceGroups/read` | View resource groups |
| `Microsoft.Resources/resources/read` | View Azure resources |

> Users assigned this role have read-only visibility into Azure resources. They cannot create, modify, or delete any infrastructure — enforcing strict least-privilege access.

**Azure Policy Governance:**

| Setting | Value |
|---|---|
| Policy | `Require a tag on resources` |
| Tag Enforced | `Environment` |
| Scope | Azure Subscription |
| Effect | Deny non-compliant resources |

**Screenshots:**

Custom Role Permissions
![Custom Role Permissions](screenshots/phase-5/phase5-custom-role-permissions.png)

Monitor Reader Role
![Monitor Reader](screenshots/phase-5/phase5-monitor-reader.png)

Policy Assigned
![Policy Assigned](screenshots/phase-5/phase5-policy-assigned.png)

Policy Assignment Configuration
![Policy Config](screenshots/phase-5/phase5-policy-assignment-config.png)

Policy Definition
![Policy Definition](screenshots/phase-5/phase5-policy-definition.png)

---

### Phase 6 – Microsoft Defender for Cloud

**Objective:** Assess and document the security posture of the Azure environment against industry benchmarks.

Used Microsoft Defender for Cloud to review the Secure Score, investigate security recommendations, and map the environment's controls against the **Azure Security Benchmark** compliance framework. Identified improvement areas and documented findings — simulating a real security posture review performed by cloud security engineers.

**Key Activities:**
- Reviewed Secure Score across the subscription
- Investigated individual security recommendations
- Mapped controls to Azure Security Benchmark framework
- Documented compliance posture and improvement areas

**Screenshots:**

Secure Score Overview
![Secure Score](screenshots/phase-6/phase6-secure-score.png)

Security Recommendations
![Recommendations](screenshots/phase-6/phase6-security-recommendations.png)

Security Recommendation Details
![Recommendation Details](screenshots/phase-6/phase6-security-recommendation-details.png)

Regulatory Compliance
![Compliance](screenshots/phase-6/phase6-regulatory-compliance.png)

---

## 🧰 Tools & Services Used

| Service | Purpose |
|---|---|
| Azure Virtual Network (VNet) | Network segmentation and isolation |
| Network Security Groups (NSG) | Traffic control and firewall rules |
| Log Analytics Workspace | Centralized log storage and analysis |
| Azure Monitor | Metrics, diagnostics, and alerting |
| KQL (Kusto Query Language) | Log investigation and security queries |
| Alert Rules | Automated incident detection |
| Action Groups | Email notification on alert trigger |
| Azure RBAC | Identity and access management |
| Azure Policy | Governance and compliance automation |
| Microsoft Defender for Cloud | Security posture and compliance mapping |

---

## 📚 What I Learned

Through this project I built real hands-on skills in:

- Designing **secure Azure Virtual Networks** with subnet isolation
- Configuring **NSG rules and IP whitelisting** to control traffic
- Building a **centralized log monitoring pipeline** with Diagnostic Settings
- Writing **KQL queries** to investigate security events and detect anomalies
- Configuring **Azure Monitor Alert Rules** for automated incident detection
- Setting up **Action Groups** to notify administrators in real time
- Creating **custom RBAC roles** following least-privilege principles
- Enforcing **Azure Policy** for subscription-wide governance
- Assessing cloud **security posture** using Microsoft Defender for Cloud
- Understanding **log ingestion delays** and real-world monitoring behaviour

---

## 💬 Interview Summary

> *"I designed and implemented an enterprise-style Azure cloud environment covering the full security lifecycle — from network segmentation and traffic control with VNet and NSG, to centralized monitoring with Log Analytics and KQL-based security investigation, automated incident alerting with Azure Monitor, least-privilege access enforcement using custom RBAC roles, governance automation with Azure Policy, and security posture management with Microsoft Defender for Cloud. Every phase was built hands-on in the Azure Portal with a focus on real-world enterprise security practices."*

---

<div align="center">

**Built with 💙 on Microsoft Azure**

*If this project helped you or you found it interesting, consider leaving a ⭐*

</div>
