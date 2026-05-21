# DNS Resolution Failure

## Incident Information

**Incident Number:** INC0010007  
**Category:** Network Connectivity  
**Priority:** P1 (Critical)  
**Assignment Group:** Help Desk  
**Assigned To:** Dev Patel

## Problem Statement

User reported WiFi displaying "Connected" status but complete inability to access websites, email, or internal network resources. DNS name resolution failing despite valid network connection and IP assignment.

## Symptoms

- WiFi status shows "Connected" with full signal strength
- Browser displays "DNS_PROBE_FINISHED_NO_INTERNET"
- Unable to resolve domain names to IP addresses
- Direct IP access (ping 8.8.8.8) working correctly
- Local network resources inaccessible

## Root Cause

DNS cache corruption preventing proper name resolution. System DNS client service unable to resolve hostnames to IP addresses despite valid network connectivity and DHCP configuration.

## Diagnostic Process

1. Verified WiFi connection status - showed "Connected"
2. Executed ipconfig /all - confirmed valid DHCP IP assignment
3. Tested external IP connectivity via ping 8.8.8.8 - successful (external IP connectivity functional)
4. Tested domain name resolution via ping google.com - failed with "could not find host"
5. Checked DNS server configuration - pointed to router DNS
6. Executed nslookup google.com - timeout error indicating DNS resolution failure
7. Identified DNS cache corruption as root cause
8. Verified DNS Client service status - running but unresponsive

## Resolution Steps

1. Opened Command Prompt as Administrator
2. Executed ipconfig /flushdns - cleared DNS resolver cache
3. Configured network adapter to use Google Public DNS as primary resolver (8.8.8.8)
4. Configured Google Secondary DNS (8.8.4.4)
5. Executed ipconfig /registerdns - re-registered DNS records
6. Tested resolution with nslookup google.com - successful resolution confirmed
7. Tested browser connectivity - all websites loading correctly
8. Verified email client connectivity - Exchange connection restored
9. Confirmed internal resource access - file shares accessible
10. Updated ServiceNow Work Notes with diagnostic steps and resolution
11. Closed ticket with resolution timestamp

## Commands Executed

ipconfig /all
ipconfig /flushdns
ipconfig /registerdns
ping 8.8.8.8
ping google.com
nslookup google.com
nslookup google.com 8.8.8.8

## Screenshots

![Screenshot a2](./screenshots/a2.png)  
*ServiceNow incidents dashboard - INC0010007 In Progress*

![Screenshot b2](./screenshots/b2.png)  
*Browser DNS error message*

![Screenshot c2](./screenshots/c2.png)  
*ipconfig /all output showing network configuration*

![Screenshot d2](./screenshots/d2.png)  
*Successful ping to external IP address*

![Screenshot e2](./screenshots/e2.png)  
*Failed ping to domain name*

![Screenshot f2](./screenshots/f2.png)  
*nslookup showing DNS failure*

![Screenshot g2](./screenshots/g2.png)  
*Command Prompt elevated to Administrator*

![Screenshot h2](./screenshots/h2.png)  
*Network adapter properties - Device Manager view*

![Screenshot i2](./screenshots/i2.png)  
*Network adapters expanded in Device Manager*

![Screenshot j2](./screenshots/j2.png)  
*DNS server configuration - Google DNS settings*

![Screenshot k2](./screenshots/k2.png)  
*Successful nslookup after DNS flush*

![Screenshot m2](./screenshots/m2.png)  
*Browser connectivity restored*

![Screenshot n2](./screenshots/n2.png)  
*Email client reconnected*

![Screenshot o2](./screenshots/o2.png)  
*ServiceNow Resolution Information tab with documented steps*

![Screenshot p2](./screenshots/p2.png)  
*ServiceNow ticket marked Resolved*

## Outcome

**Time to Resolution:** 12 minutes  
**Impact:** Single user  
**Total Downtime:** 12 minutes  
**Follow-up Action:** Created KB article for DNS troubleshooting procedure

## Technical Skills Demonstrated

- DNS troubleshooting methodology
- Command-line network diagnostics (ipconfig, nslookup, ping)
- Understanding of DNS hierarchy and resolution process
- Google Public DNS configuration
- ServiceNow incident documentation
- Root cause analysis
- Sub-15-minute resolution time

## Key Insights

DNS cache corruption is a common Windows 11 issue after system updates or network changes. Always test both IP connectivity (ping 8.8.8.8) and name resolution (ping google.com) to isolate DNS vs network layer problems. Google Public DNS (8.8.8.8 / 8.8.4.4) provides reliable fallback when local DNS fails.
