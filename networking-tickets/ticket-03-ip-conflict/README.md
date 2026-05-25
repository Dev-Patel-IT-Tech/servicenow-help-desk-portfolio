# IP Address Conflict

## Incident Information

**Incident Number:** INC0010008  
**Category:** Network  
**Subcategory:** IP Address  
**Priority:** 3 - Moderate  
**Impact:** 2 - Medium  
**Urgency:** 2 - Medium  
**Assignment Group:** Help Desk  
**Assigned To:** Dev Patel  
**Caller:** Elisa Gracely

## Problem Statement

User receiving error message stating another device is using the same IP address. Connection issues preventing stable network access.

## Symptoms

- Windows error popup: "Windows has detected an IP address conflict"
- Message states another computer on network has same IP address
- Intermittent network connectivity
- Unable to maintain stable connection

## Root Cause

IP address conflict caused by DHCP lease assignment collision. Two devices on the network were temporarily assigned the same IP address, preventing stable connectivity.

## Diagnostic Process

1. Reviewed user-reported error message about duplicate IP address
2. Opened Command Prompt to begin IP troubleshooting
3. Executed ipconfig /release to clear current IP assignment
4. Executed ipconfig /renew to request new IP from DHCP server
5. Verified DHCP configuration using ipconfig /all
6. Confirmed network adapter set to obtain IP automatically
7. Verified WiFi connection settings in Windows Settings

## Resolution Steps

1. Opened Command Prompt as administrator
2. Executed ipconfig /release to release current IP address assignment
3. Executed ipconfig /renew to obtain new IP address from DHCP server
4. Verified new IP address successfully assigned from DHCP pool
5. Restarted system to clear cached network configurations and force fresh network initialization
6. Executed ipconfig /all after restart to verify DHCP configuration
7. Confirmed DHCP Enabled: Yes and valid IP assignment
8. Opened Network Connections and accessed WiFi adapter properties
9. Verified Internet Protocol Version 4 (TCP/IPv4) settings
10. Confirmed "Obtain an IP address automatically" option selected
11. Opened Windows Settings and navigated to Network & Internet
12. Accessed WiFi settings and selected Manage known networks
13. Verified current network accessible with option to forget/reconnect if needed
14. Tested network connectivity and confirmed stable connection
15. Documented resolution steps in ServiceNow Work Notes
16. Updated incident to Resolved status with detailed resolution information

## Commands Executed

ipconfig /release
ipconfig /renew
ipconfig /all

## Screenshots

![Screenshot a3](./screenshots/a3.png)  
ServiceNow incidents list showing INC0010008 In Progress - Priority 3 Moderate assigned to Dev Patel

![Screenshot b3](./screenshots/b3.png)  
Windows Network Error dialog displaying IP address conflict message

![Screenshot c3](./screenshots/c3.png)  
Command Prompt executing ipconfig /release command clearing IP assignment

![Screenshot d3](./screenshots/d3.png)  
Command Prompt executing ipconfig /renew obtaining new IP address from DHCP server

![Screenshot e3](./screenshots/e3.png)  
Windows Start menu Power Options with Restart option highlighted

![Screenshot f3](./screenshots/f3.png)  
Command Prompt ipconfig /all output showing DHCP Enabled Yes and valid IP configuration

![Screenshot g3](./screenshots/g3.png)  
Network adapter IPv4 Properties dialog with Obtain an IP address automatically selected

![Screenshot h3](./screenshots/h3.png)  
Windows Settings Network & Internet WiFi Manage known networks page with Forget option

![Screenshot i3](./screenshots/i3.png)  
ServiceNow incident INC0010008 details page showing Resolved state

![Screenshot j3](./screenshots/j3.png)  
ServiceNow Work Notes documenting troubleshooting steps and resolution process

![Screenshot k3](./screenshots/k3.png)  
ServiceNow Resolution Information with detailed resolution notes and steps performed

![Screenshot l3](./screenshots/l3.png)  
ServiceNow incidents list showing INC0010008 Resolved status

## Outcome

**Time to Resolution:** 22 minutes  
**Status:** Resolved  
**Resolution Code:** Solution provided  
**Verified:** User confirmed stable network connection with no further IP conflict errors

## Technical Skills Demonstrated

- IP address conflict troubleshooting
- DHCP client configuration management
- Windows command-line network diagnostics
- Network adapter configuration verification
- ServiceNow incident documentation
- Work notes and resolution information documentation

## Key Insights

IP address conflicts typically resolve through DHCP lease renewal using ipconfig /release and ipconfig /renew commands. Verifying DHCP configuration on network adapter ensures automatic IP assignment prevents future conflicts. System restart clears cached network configurations forcing fresh DHCP lease. Most IP conflicts resolve within first three troubleshooting steps without requiring advanced network analysis.
