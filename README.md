# CloudGuard – Azure Secure Infrastructure & Monitoring

📖 **Full case study:**  
https://prasanth-portfolio-blond.vercel.app/blog/azure-secure-storage-architecture

![Azure](https://img.shields.io/badge/Cloud-Microsoft%20Azure-blue)
![Security](https://img.shields.io/badge/Focus-Cloud%20Security-green)
![Monitoring](https://img.shields.io/badge/Monitoring-Log%20Analytics-orange)
![Infrastructure](https://img.shields.io/badge/Infrastructure-VNet%20%7C%20NSG-purple)

---

## Overview

CloudGuard is a hands-on Microsoft Azure infrastructure project designed to demonstrate **secure cloud networking, access control, monitoring, and governance** using Azure-native services.

This project simulates a real-world cloud environment where **network segmentation, security hardening, and centralized monitoring** are implemented to protect cloud resources and improve operational visibility.

---

## Architecture Diagram

The following diagram shows the Azure infrastructure architecture used in this project.

![Secure Azure Storage Architecture](https://prasanth-portfolio-blond.vercel.app/static/images/azure-secure-storage-architecture.png)

---

## Skills Demonstrated

• Azure Virtual Network (VNet) architecture  
• Subnet segmentation and network isolation  
• Network Security Group (NSG) rule configuration  
• Azure Log Analytics monitoring and diagnostics  
• KQL queries for log analysis  
• Microsoft Defender for Cloud security posture management  
• Azure Resource architecture visualization  

---

## Implementation Steps

1. Created Azure Resource Group for project isolation  
2. Configured Virtual Network with segmented subnets  
3. Applied Network Security Group rules for inbound security  
4. Enabled Azure Log Analytics for monitoring  
5. Configured Microsoft Defender for Cloud security posture management  
6. Used Azure Resource Visualizer to validate infrastructure architecture  

---

## Architecture Components

**Resource Group:** CloudGuard-Sec-RG  
**Virtual Network:** 10.0.0.0/16  

### Subnets

Public Subnet → 10.0.1.0/24  
Private Subnet → 10.0.2.0/24  

### Security Controls

Network Security Group (NSG)  
Restricted inbound rules  
IP Whitelisting (/32)

### Monitoring

Log Analytics Workspace  
Diagnostic Settings  
KQL Queries

### Security Posture

Microsoft Defender for Cloud

### Governance

Role Based Access Control (RBAC)

---

## Key Implementations

### 1. Virtual Network Architecture

Created a Virtual Network with separated **public and private subnets** to simulate production-grade cloud segmentation and isolation.

---

### 2. Network Security Hardening

Configured **Network Security Group (NSG)** rules to control inbound and outbound traffic.

SSH access was restricted using **IP whitelisting (/32 CIDR)** to minimize exposure.

---

### 3. Role Based Access Control (RBAC)

Implemented **least-privilege access control** by assigning the **Reader role** at the resource group level.

---

### 4. Monitoring & Logging

Enabled **Diagnostic Settings** on the Network Security Group and streamed logs into a **Log Analytics Workspace** for centralized monitoring.

---

### 5. Log Validation using KQL

Used Azure **KQL queries** to validate NSG event logs and confirm monitoring pipeline functionality.

### Example Query – View Recent NSG Events

```kql
AzureDiagnostics
| where Category == "NetworkSecurityGroupEvent"
| where TimeGenerated > ago(24h)
| project TimeGenerated, Resource, OperationName, Category
| order by TimeGenerated desc
```

### Example Query – Count Events by Operation

```kql
AzureDiagnostics
| where Category == "NetworkSecurityGroupEvent"
| summarize EventCount = count() by OperationName
| order by EventCount desc
```

---

### 6. Security Posture Review

Analyzed security recommendations and posture insights using **Microsoft Defender for Cloud**.

---

### 7. Cost Governance

Reviewed **Azure Cost Management** and removed resources after testing to prevent unnecessary cloud charges.

---

## Tools & Services Used

Microsoft Azure  
Azure Virtual Network (VNet)  
Azure Network Security Groups (NSG)  
Azure RBAC  
Log Analytics Workspace  
Azure Monitor  
Microsoft Defender for Cloud  
Kusto Query Language (KQL)

---

## What I Learned

Through this project I gained hands-on experience with:

• Designing secure **Azure Virtual Networks and subnet segmentation**  
• Implementing **Network Security Group rules for traffic control**  
• Streaming diagnostic logs to **Log Analytics Workspace**  
• Using **KQL queries to validate security logs**  
• Monitoring cloud resources using **Azure Monitor**  
• Reviewing security posture with **Microsoft Defender for Cloud**  
• Visualizing infrastructure using **Azure Resource Visualizer**

---

## Future Enhancements

• Implement **Azure Firewall** for advanced network protection  
• Deploy **Azure Bastion** for secure VM access without public SSH exposure  
• Configure **Azure Policy** for governance and compliance automation  
• Implement **Azure Monitor alert rules** for suspicious traffic detection  
• Automate deployment using **Terraform or ARM templates**

---

## Project Implementation Screenshots

Screenshots are organized by phase inside the **/screenshots directory**.

---

### Phase 1 – Infrastructure Setup

Resource Group Creation  
![Resource Group](screenshots/phase-1/03-RG-Created.png)

Virtual Network Configuration  
![VNet](screenshots/phase-1/01_VNet_Config.png)

Storage Account Setup  
![Storage](screenshots/phase-1/Phase1_Storage_Config.png)

Log Analytics Workspace  
![Log Analytics](screenshots/phase-1/02_LogAnalytics_Success.png)

---

### Phase 2 – Security & Monitoring

Network Security Group Configuration  
![NSG](screenshots/phase-2/02_NSG_InboundRule_Config.png)

NSG Attached to Subnet  
![NSG Subnet](screenshots/phase-2/05_Subnet_NSG_Attached.png)

Log Analytics Monitoring Validation  
![Logs](screenshots/phase-2/P2-KQL-NSG-Log-Validation.png)

Microsoft Defender Secure Score  
![Defender](screenshots/phase-2/P2-Defender-Overview-SecureScore.png)

---

## Result

This project demonstrates how Azure-native services can be combined to build a secure, monitored, and governed cloud infrastructure environment, simulating an enterprise cloud security architecture.
