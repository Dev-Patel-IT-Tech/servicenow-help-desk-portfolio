# DNS Resolution Failure

## Incident Information

**Incident Number:** INC0010007  
**Category:** Network/VPN  
**Priority:** P1 (Critical)  
**Assignment Group:** Help Desk  
**Assigned To:** Dev Patel  
**Caller:** Mathew Taylor

## Problem Statement

WiFi showing "Connected" status with full signal strength but complete inability to access websites or network resources. Classic DNS resolution failure where device connects to router successfully but domain names fail to resolve.

## Symptoms

- WiFi status shows "Connected" with full signal bars
- Browser displays blank page when attempting to load websites
- Unable to access email or internal network resources
- ipconfig shows valid IP address and gateway assignment
- Direct IP connectivity functional (ping 8.8.8.8 successful)

## Root Cause

DNS resolution failure. Device connected to WiFi and could reach router/internet via IP addresses, but local DNS server was not resolving domain names to IP addresses.

## Diagnostic Process

1. Verified WiFi connection status - showed "Connected" with full signal
2. Opened browser and confirmed google.com returned blank page
3. Executed ipconfig - confirmed valid DHCP IP assignment and gateway
4. Tested router connectivity via ping to gateway IP - successful (0% loss, 4-19ms)
5. Tested internet connectivity via ping 8.8.8.8 - successful (0% loss, 4-20ms)
6. Isolated issue to DNS resolution layer - device reaches internet via IP but cannot resolve domain names

## Resolution Steps

1. Opened Command Prompt as Administrator
2. Executed ipconfig /flushdns - cleared DNS resolver cache
3. Opened Network Connections via Control Panel
4. Accessed WiFi adapter properties → Internet Protocol Version 4 (TCP/IPv4) Properties
5. Changed from "Obtain DNS server address automatically" to manual configuration
6. Configured Primary DNS: 8.8.8.8 (Google Public DNS)
7. Configured Secondary DNS: 8.8.4.4 (Google Public DNS)
8. Applied DNS configuration changes
9. Opened Device Manager → Network adapters
10. Right-clicked Intel(R) Wi-Fi 6 AX201 160MHz adapter → Disabled device
11. Right-clicked same adapter → Enabled device
12. Tested browser connectivity - google.com loaded successfully
13. Verified full internet access restored
14. Documented resolution steps in ServiceNow Work Notes
15. Closed ticket

## Commands Executed

ipconfig
ping [gateway IP]
ping 8.8.8.8
ipconfig /flushdns

## Screenshots

![Screenshot a2](./screenshots/a2.png)  
ServiceNow incidents list showing INC0010007 In Progress - Priority 1 Critical

![Screenshot b2](./screenshots/b2.png)  
Command Prompt - ipconfig output showing valid IPv4 address and default gateway

![Screenshot c2](./screenshots/c2.png)  
Successful ping to default gateway - 0% packet loss, 4 replies received, 4-19ms latency

![Screenshot d2](./screenshots/d2.png)  
Successful ping to 8.8.8.8 - 0% packet loss, 4 replies received, 4-20ms latency

![Screenshot e2](./screenshots/e2.png)  
ipconfig /flushdns command execution - Successfully flushed DNS Resolver Cache

![Screenshot f2](./screenshots/f2.png)  
Network adapter IPv4 Properties - Manual DNS configuration set to 8.8.8.8 and 8.8.4.4

![Screenshot g2](./screenshots/g2.png)  
Device Manager - Network adapters with right-click menu showing Disable device option

![Screenshot h2](./screenshots/h2.png)  
Device Manager - Network adapter right-click menu showing Enable device option

![Screenshot i2](./screenshots/i2.png)  
Device Manager - Network adapter successfully re-enabled and operational

![Screenshot j2](./screenshots/j2.png)  
Chrome browser successfully loading Google.com homepage after DNS fix

![Screenshot k2](./screenshots/k2.png)  
ServiceNow incident form INC0010007 showing incident details and In Progress state

![Screenshot m2](./screenshots/m2.png)  
ServiceNow Work Notes documenting diagnostic steps with timestamps (23:49-23:55)

![Screenshot n2](./screenshots/n2.png)  
ServiceNow Work Notes documenting resolution actions with timestamps (23:56-00:03)

![Screenshot o2](./screenshots/o2.png)  
ServiceNow incident form showing Resolution Information tab with complete resolution notes

![Screenshot p2](./screenshots/p2.png)  
ServiceNow incidents list confirming INC0010007 marked Resolved

## Outcome

**Time to Resolution:** 14 minutes  
**Impact:** Single user  
**Total Downtime:** 14 minutes  
**Follow-up Action:** Created KB article for DNS troubleshooting procedure

## Technical Skills Demonstrated

- DNS troubleshooting methodology
- TCP/IP networking fundamentals (DHCP, DNS, gateway, IP addressing)
- Command-line network diagnostics (ipconfig, ping)
- Windows network adapter configuration
- Google Public DNS implementation
- Device Manager proficiency
- ServiceNow incident documentation
- Root cause analysis
- Sub-15-minute resolution time

## Key Insights

DNS resolution failures are extremely common in help desk environments. WiFi showing "Connected" with full signal confuses users because it appears internet is working. Always isolate failure layer systematically: test gateway connectivity (local network), test external IP connectivity (internet), then test DNS resolution. Google Public DNS (8.8.8.8/8.8.4.4) provides reliable fallback when ISP DNS fails. Network adapter reset via Device Manager forces clean reconnection without system reboot.
