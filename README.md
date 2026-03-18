# CloudGuard – Azure Secure Infrastructure & Monitoring

📖 **Full case study:** [Azure Secure Storage Architecture](https://prasanth-portfolio-blond.vercel.app/blog/azure-secure-storage-architecture)

![Azure](https://img.shields.io/badge/Cloud-Microsoft%20Azure-blue)
![Security](https://img.shields.io/badge/Focus-Cloud%20Security-green)
![Monitoring](https://img.shields.io/badge/Monitoring-Log%20Analytics-orange)
![Infrastructure](https://img.shields.io/badge/Infrastructure-VNet%20%7C%20NSG-purple)
![RBAC](https://img.shields.io/badge/Governance-RBAC%20%7C%20Policy-red)
![Defender](https://img.shields.io/badge/Security-Defender%20for%20Cloud-darkblue)

---

## Overview

CloudGuard is a hands-on Microsoft Azure portfolio project that simulates a real-world enterprise cloud environment. It demonstrates secure cloud networking, centralized monitoring, incident alerting, access governance, and security posture management using Azure-native services.

This project was built to reflect the core responsibilities of an Azure Administrator — from infrastructure setup and security hardening, to operational monitoring, automated alerting, and compliance enforcement.

---

## Architecture Diagram

![Secure Azure Infrastructure Architecture](https://prasanth-portfolio-blond.vercel.app/static/images/azure-secure-storage-architecture.png)

---

## Skills Demonstrated

- Azure Virtual Network (VNet) design and subnet segmentation
- Network Security Group (NSG) rule configuration and IP whitelisting
- Centralized logging with Log Analytics Workspace and Diagnostic Settings
- Security investigation using KQL (Kusto Query Language)
- Incident detection with Azure Monitor Alert Rules
- Automated notifications via Action Groups
- Custom RBAC role creation and least-privilege access enforcement
- Governance automation with Azure Policy
- Security posture management with Microsoft Defender for Cloud

---

## Project Phases

### Phase 1 – Infrastructure Setup

Built the foundational Azure environment including a Resource Group, Virtual Network with public and private subnet segmentation, and a Storage Account.

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

Configured Network Security Groups (NSG) to control inbound and outbound traffic. SSH access was restricted using IP whitelisting (/32 CIDR). NSG was attached to the subnet and diagnostic logs were streamed into Log Analytics for centralized monitoring.

**Key Implementations:**
- Inbound NSG rules with IP whitelisting (/32 CIDR)
- NSG attached to private subnet
- Diagnostic settings enabled on NSG
- KQL queries to validate log ingestion
- Microsoft Defender for Cloud security posture review

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

Built a centralized monitoring pipeline by connecting Azure Activity Logs to a dedicated Log Analytics Workspace. Configured diagnostic settings to stream administrative, security, policy, and health logs. Used KQL to investigate administrative events, detect resource modifications, and query failed operations.

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

**Note on log ingestion:** After configuring diagnostic settings, Azure required several minutes to ingest logs. This is expected behaviour in production environments and demonstrates real-world monitoring experience.

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

Configured Azure Monitor Alert Rules to automatically detect administrative operations and failed events. Created an Action Group to send email notifications when alerts fire, simulating a real enterprise incident response workflow.

**Alert Rule Configuration:**

| Setting | Value |
|---|---|
| Alert Rule Name | phase4-admin-change-alert |
| Signal Type | Activity Log |
| Category | Administrative |
| Event Level | Error |
| Scope | Azure Subscription |
| Action Group | ag-admin-alerts |

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

Implemented enterprise-grade access control by creating a custom RBAC role with least-privilege permissions scoped at the subscription level. Enforced governance using Azure Policy to require mandatory resource tagging across the environment.

**Custom RBAC Role – `phase5-monitor-reader`:**

| Permission | Purpose |
|---|---|
| Microsoft.Resources/subscriptions/resourceGroups/read | View resource group information |
| Microsoft.Resources/resources/read | View Azure resources |

Users with this role can view resources but cannot create, modify, or delete infrastructure — enforcing strict least-privilege access.

**Azure Policy:**
- Policy: `Require a tag on resources`
- Tag Enforced: `Environment`
- Scope: Azure Subscription

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

### Phase 6 – Microsoft Defender for Cloud (Security Posture)

Used Microsoft Defender for Cloud to assess and improve the overall security posture of the Azure environment. Reviewed security recommendations, investigated findings, and mapped controls against the Azure Security Benchmark compliance framework.

**Key Activities:**
- Reviewed Secure Score and security recommendations
- Investigated security findings across the subscription
- Reviewed regulatory compliance against Azure Security Benchmark
- Identified and documented improvement areas

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

## Tools & Services Used

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
| Microsoft Defender for Cloud | Security posture and recommendations |

---

## Interview Summary

> "I designed and implemented an enterprise-style Azure cloud environment covering the full security lifecycle — from network segmentation and traffic control with VNet and NSG, to centralized monitoring with Log Analytics and KQL-based investigation, automated alerting with Azure Monitor, least-privilege access enforcement using custom RBAC roles, governance automation with Azure Policy, and security posture management with Microsoft Defender for Cloud."

---

## About

Enterprise-style Azure secure infrastructure built to demonstrate real-world Azure Administrator skills including networking, security, monitoring, governance, and compliance.

**Topics:** `azure` `cloud-security` `azure-monitor` `log-analytics` `kql` `rbac` `azure-policy` `defender-for-cloud` `vnet` `nsg`
