# ServiceNow Help Desk Portfolio

Help desk incident management across network connectivity and Windows 11 performance optimization. ServiceNow ITSM workflows with diagnostic troubleshooting, Work Notes documentation, and knowledge base articles.

![ServiceNow](https://img.shields.io/badge/ServiceNow-ITSM-green)
![Windows 11](https://img.shields.io/badge/Windows-11-blue)
![Active Directory](https://img.shields.io/badge/Active_Directory-2022-orange)
![PowerShell](https://img.shields.io/badge/PowerShell-7-blue)

## Overview

Resolved help desk incidents in ServiceNow Personal Developer Instance with full ITSM workflows from ticket creation through diagnostic troubleshooting to resolution closure. Documented Tier-1 technical support capabilities across network connectivity issues and Windows 11 performance optimization.

**Network incident resolution:** DNS cache corruption, DHCP addressing failures, IP address conflicts  
**Performance incident resolution:** Disk space critical alerts, high RAM utilization, slow boot times  
**ITSM methodology:** Incident creation, Work Notes, root cause analysis, resolution documentation, KB articles

## Incidents Resolved

### Network Connectivity

**[DNS Resolution Failure](./networking-tickets/ticket-02-wifi-dns/)**  
Diagnosed DNS cache corruption preventing name resolution despite valid WiFi connectivity. Flushed DNS cache via ipconfig /flushdns, configured Google DNS upstream resolvers (8.8.8.8 / 8.8.4.4), validated with nslookup. Restored internet access in under 15 minutes.

**[IP Address Conflict](./networking-tickets/ticket-03-ip-conflict/)**  
Traced duplicate static IP assignment causing intermittent network drops. Analyzed ARP table for MAC address conflicts, reassigned endpoint to DHCP pool via ipconfig /release and /renew, updated CMDB documentation.

**[Network Adapter Driver Corruption](./networking-tickets/ticket-01-no-internet/)**  
Resolved complete internet connectivity loss caused by driver version mismatch. Diagnosed via Device Manager and Event Viewer, uninstalled corrupted driver, triggered Windows automatic driver reinstallation on reboot.

### Windows 11 Performance

**[Disk Space Critical - 2,269 Items Removed](./performance-tickets/ticket-04-disk-usage/)**  
Resolved C: drive at 92% capacity (6.8 GB free). Executed Storage Sense automation, Disk Cleanup for Windows Update cache, manual temp file purge via command line. Reduced usage to 61% (38.2 GB free).

**[High RAM Utilization - 94% to 56%](./performance-tickets/ticket-05-ram-usage/)**  
Diagnosed memory exhaustion (7.4 GB / 7.8 GB used) causing application freezes. Terminated Chrome's 22 background processes consuming 1,832 MB, disabled 4 unnecessary startup applications. Reduced utilization to 56% (4.4 GB used).

**[Boot Time Optimization - 5-10 min to 1-2 min](./performance-tickets/ticket-06-slow-boot/)**  
Reduced extreme boot delays caused by 20+ startup services. Audited startup applications via Task Manager and msconfig, disabled non-essential processes, verified SSD health. Achieved sub-2-minute boot time.

## Technical Capabilities

**ITSM Platform:** ServiceNow (incident lifecycle management, Work Notes, priority assignment, resolution documentation, KB articles)  
**Operating Systems:** Windows 11, Windows 10  
**Network Diagnostics:** TCP/IP, DNS, DHCP, ARP, ipconfig, nslookup, network adapter troubleshooting  
**Performance Tools:** Task Manager, Resource Monitor, Disk Cleanup, Storage Sense, Event Viewer  
**Directory Services:** Active Directory (user/group management, GPO)  
**Scripting:** PowerShell (basic automation)  
**Productivity:** Microsoft 365 (mailbox management, license assignment)

## Tools & Technologies

ServiceNow • Windows 11 • Active Directory • PowerShell • Task Manager • ipconfig • nslookup • Disk Cleanup • Event Viewer • Microsoft 365

## Documentation Methodology

ServiceNow Personal Developer Instance with Windows 11 lab environment. Every ticket follows ITSM best practices: problem statement, diagnostic commands, root cause analysis, resolution steps with timestamps, knowledge base documentation.

## Contact

**LinkedIn:** [linkedin.com/in/devpatel-itsupport](https://www.linkedin.com/in/devpatel-itsupport/)  
**Email:** devpatel6217@gmail.com  
**Location:** Greater Toronto Area, Ontario, Canada

**Additional Labs:**
- [Active Directory on Windows Server 2025](https://github.com/Dev-Patel-IT-Tech/Active-directory-windows-server-2025) - 11,367 provisioned identities, GPO-enforced lockout policy
- [osTicket Help Desk](https://github.com/Dev-Patel-IT-Tech/osticket-helpdesk) - IIS deployment, SLA tiers, role-based access control
- [Azure Network Analysis](https://github.com/Dev-Patel-IT-Tech/azure-network-analysis) - Wireshark protocol analysis across ICMP, SSH, DHCP, DNS, RDP
- [AWS Multi-AZ Infrastructure](https://github.com/Dev-Patel-IT-Tech/aws-multi-az-infrastructure) - EC2, ALB, VPC, CloudFormation, S3, ECS Fargate

---

**Dev Patel** | Help Desk Technician | ServiceNow • Active Directory • Windows 11
