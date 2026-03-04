# CloudGuard – Azure Secure Infrastructure & Monitoring

## Overview
CloudGuard is a hands-on Microsoft Azure infrastructure project designed to demonstrate secure cloud networking, access control, monitoring, and governance using Azure-native services.

This project simulates a real-world cloud environment where network segmentation, security hardening, and centralized monitoring are implemented to protect cloud resources and improve operational visibility.

## Architecture Components

Resource Group: CloudGuard-Sec-RG  
Virtual Network: 10.0.0.0/16  

Subnets:
- Public Subnet: 10.0.1.0/24
- Private Subnet: 10.0.2.0/24

Security:
- Network Security Group (NSG)
- Restricted inbound rules
- IP Whitelisting (/32)

Monitoring:
- Log Analytics Workspace
- Diagnostic Settings
- KQL Queries

Security Posture:
- Microsoft Defender for Cloud

Governance:
- Role Based Access Control (RBAC)

---

## Key Implementations

### 1. Virtual Network Architecture
Created a Virtual Network with separated public and private subnets to simulate production-grade cloud segmentation and isolation.

### 2. Network Security Hardening
Configured Network Security Group (NSG) rules to control inbound and outbound traffic. SSH access was restricted using IP whitelisting (/32 CIDR) to minimize exposure.

### 3. Role Based Access Control (RBAC)
Implemented least-privilege access control by assigning the **Reader role** at the resource group level.

### 4. Monitoring & Logging
Enabled **Diagnostic Settings** on the Network Security Group and streamed logs into a **Log Analytics Workspace** for centralized monitoring.

### 5. Log Validation using KQL
Used Azure KQL queries to validate NSG event logs and confirm monitoring pipeline functionality.

Example Query:

AzureDiagnostics  
| where Category == "NetworkSecurityGroupEvent"  
| limit 10

### 6. Security Posture Review
Analyzed security recommendations using **Microsoft Defender for Cloud**.

### 7. Cost Governance
Reviewed Azure Cost Management and removed resources after testing to prevent unnecessary cloud charges.

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

## Future Improvements

Deploy a VM inside the public subnet  
Implement alert rules for NSG events  
Create monitoring dashboards  
Apply Azure Policy for governance automation
