# Network Adapter Driver Corruption

## Incident Information

**Incident Number:** INC0010006  
**Category:** Network Connectivity  
**Priority:** P3 (Medium)  
**Assignment Group:** Help Desk  
**Assigned To:** Dev Patel

## Problem Statement

Complete loss of internet connectivity on Windows 11 desktop. All network-dependent applications (browser, email, Teams) failed to load. WiFi icon displayed "Connected" status but no actual internet access available.

## Symptoms

- Browser error: "This site can't be reached"
- Outlook disconnected from Exchange server
- Microsoft Teams status stuck on "Connecting"
- Windows Network Diagnostics reported "Network adapter driver issue"

## Root Cause

Network adapter driver corruption caused by recent Windows Update. Driver version mismatch between OS kernel and network hardware prevented proper adapter initialization.

## Diagnostic Process

1. Verified physical network connection (Ethernet cable properly seated)
2. Executed ipconfig /all - confirmed valid IP assignment from DHCP
3. Tested external connectivity via ping 8.8.8.8 - Request timed out (no external access)
4. Tested internal connectivity via ping to default gateway - Successful (local network functional)
5. Opened Device Manager - identified yellow exclamation mark on network adapter
6. Reviewed driver properties - confirmed incorrect driver version
7. Checked Event Viewer System logs - located driver load failure entries

## Resolution Steps

1. Opened Device Manager (devmgmt.msc)
2. Navigated to Network adapters section
3. Right-clicked problematic adapter → selected "Uninstall device"
4. Enabled "Delete the driver software for this device" checkbox
5. Confirmed uninstallation
6. Initiated system restart
7. Windows automatically detected hardware on boot
8. Windows installed correct driver from driver store
9. Verified connectivity: ping google.com successful
10. Tested all affected applications: browser, Outlook, Teams - all functional
11. Documented resolution steps in ServiceNow Work Notes
12. Closed ticket with timestamp

## Commands Executed

```cmd
ipconfig /all
ipconfig /release
ipconfig /renew
ping 8.8.8.8
ping 192.168.1.1
ping google.com
devmgmt.msc
```

## Outcome

**Time to Resolution:** 23 minutes  
**Impact:** Single user  
**Total Downtime:** 23 minutes  
**Follow-up Action:** Created KB article documenting driver reinstallation procedure for future reference

## Technical Skills Demonstrated

- Network troubleshooting methodology (OSI model layer isolation)
- Windows Device Manager proficiency
- Command-line diagnostic tools (ipconfig, ping)
- Event Viewer log analysis
- ServiceNow incident lifecycle management
- Root cause analysis
- Knowledge base documentation

## Key Insights

Network adapter issues frequently resolve with driver reinstallation rather than advanced troubleshooting. Always verify Device Manager for hardware errors before escalating. Document driver versions in Work Notes for trend analysis across similar incidents.
