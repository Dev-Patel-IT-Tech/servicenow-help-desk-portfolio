# Ticket 02: WiFi Connected But No Internet - DNS Resolution Failure

## Incident Information

**Incident Number:** INC0010007  
**Category:** Network/VPN  
**Priority:** 1 - Critical  
**Assignment Group:** Help Desk  
**Assigned To:** Dev Patel  
**Caller:** Mathew Taylor  
**Short Description:** Wi-Fi connected with full signal but websites won't load

## Problem Statement

User reported WiFi showing "Connected" status with full signal strength, but unable to load any websites in browser. Classic DNS resolution failure where device successfully connects to router and can reach internet via IP addresses, but domain names fail to resolve.

## Root Cause

DNS resolution failure. Device was connected to WiFi and could reach router (successful gateway ping) and internet (successful ping 8.8.8.8), but local DNS server was not resolving domain names to IP addresses.

## Troubleshooting Workflow

### Step 1: Understand the Problem
WiFi shows connected with full bars, but browser returns blank pages. This is NOT a "no WiFi" issue - device is connected to router, but router cannot reach internet DNS servers OR local DNS is failing.

### Step 2: Verify the Issue
Opened browser and attempted to load google.com - confirmed blank page, validating user's report.

### Step 3: Check IP Configuration
Ran `ipconfig` to verify device has valid IP address and default gateway from DHCP.

### Step 4: Test Router Connectivity
Ran `ping [gateway IP]` to confirm device can communicate with router. Successful ping proves WiFi connection is functional.

### Step 5: Test Internet Access
Ran `ping 8.8.8.8` (Google DNS) to test if device can reach internet via IP address. Successful ping proves internet connectivity is working - narrows issue to DNS resolution layer.

### Step 6: Flush DNS Cache
Ran `ipconfig /flushdns` to clear corrupted or outdated DNS cache entries.

### Step 7: Configure Google Public DNS
Navigated to: Network Connections → WiFi Properties → Internet Protocol Version 4 (TCP/IPv4) Properties

Manually configured DNS servers to force system to use Google DNS instead of ISP DNS:
- **Preferred DNS Server:** 8.8.8.8
- **Alternate DNS Server:** 8.8.4.4

### Step 8: Restart Network Adapter
Opened Device Manager → Network adapters → Intel(R) Wi-Fi 6 AX201 160MHz
- Right-click → Disable device
- Right-click → Enable device
This resets the connection cleanly and forces adapter to re-establish with new DNS configuration.

### Step 9: Verify Resolution
Opened browser and successfully loaded google.com - DNS resolution working correctly, full internet access restored.

## Commands Executed

```cmd
ipconfig
ping [gateway IP]
ping 8.8.8.8
ipconfig /flushdns
```

## Screenshots

![Screenshot a2](./screenshots/a2.png)  
**ServiceNow incidents dashboard** - Two network incidents visible: INC0010007 (Mathew Taylor, "Wi-Fi connected with full signal but websites won't load", Priority 1-Critical, In Progress) and INC0010006 (Chris Harris, Resolved). Demonstrates incident queue management and priority-based triage.

![Screenshot b2](./screenshots/b2.png)  
**Command Prompt - ipconfig output** - Wireless LAN adapter Wi-Fi showing valid IPv4 address (192.x) and default gateway (192.x). Multiple disconnected adapters visible above. Confirms device received IP from DHCP and is connected to router - local network connectivity is functional.

![Screenshot c2](./screenshots/c2.png)  
**Command Prompt - ping gateway** - Successful ping to default gateway (192.x): 4 packets sent, 4 received, 0% packet loss, response times 4-19ms. Red annotation highlights "Default Gateway" label and successful statistics. Confirms device can communicate with router - isolates issue to internet/DNS layer rather than local network.

![Screenshot d2](./screenshots/d2.png)  
**Command Prompt - ping 8.8.8.8** - Successful ping to Google DNS immediately after gateway ping: 4 packets sent, 4 received, 0% loss, response times 4-20ms. Proves internet connectivity is working and narrows root cause to DNS resolution failure (device can reach external IPs but cannot resolve domain names).

![Screenshot e2](./screenshots/e2.png)  
**Command Prompt - ipconfig /flushdns** - Command execution shown in red annotation box. Output displays "Successfully flushed the DNS Resolver Cache." Clears corrupted or outdated DNS cache entries that may be preventing domain name resolution. First DNS troubleshooting step before manually configuring DNS servers.

![Screenshot f2](./screenshots/f2.png)  
**Network Connections - DNS Configuration** - Wi-Fi Properties and IPv4 Properties dialogs open. DNS configuration changed from "Obtain DNS server address automatically" to "Use the following DNS server addresses": Preferred DNS 8.8.8.8, Alternate DNS 8.8.4.4. Forces system to use reliable Google public DNS instead of potentially failing ISP-provided DNS.

![Screenshot g2](./screenshots/g2.png)  
**Device Manager - Disable Network Adapter (Part 1)** - Device Manager open with Network adapters section expanded. Intel(R) Wi-Fi 6 AX201 160MHz adapter selected with right-click context menu showing "Disable device" option highlighted. Prepares to reset network connection cleanly by disabling adapter.

![Screenshot h2](./screenshots/h2.png)  
**Device Manager - Enable Network Adapter (Part 2)** - Same Intel(R) Wi-Fi 6 AX201 160MHz adapter with right-click context menu displaying "Enable device" option. Status bar at bottom reads "Enables the selected device." Completes adapter reset process, forcing system to reestablish connection with flushed DNS cache and newly configured Google DNS servers.

![Screenshot i2](./screenshots/i2.png)  
**Device Manager - Adapter Re-Enabled** - Network adapters section showing Intel(R) Wi-Fi 6 AX201 160MHz adapter now visible and active in list (no down arrow icon indicating disabled state). Adapter successfully re-enabled - system has reestablished WiFi connection with corrected DNS configuration.

![Screenshot j2](./screenshots/j2.png)  
**Chrome Browser - Resolution Verified** - Google.com homepage successfully loaded. Search bar, Google logo, "Google Search" and "I'm Feeling Lucky" buttons all visible. Confirms DNS resolution now working correctly and full internet access restored. User can now browse websites as expected.

![Screenshot k2](./screenshots/k2.png)  
**ServiceNow Incident Form - Full Details** - INC0010007 complete ticket details: Caller Mathew Taylor, Category Network/Subcategory VPN, State In Progress, Impact 1-High, Urgency 1-High, Priority 1-Critical, Assignment group Help Desk, Assigned to Dev Patel. Short description: "Wi-Fi connected with full signal but websites won't load." Work notes section visible at bottom.

![Screenshot m2](./screenshots/m2.png)  
**ServiceNow Work Notes - Troubleshooting Steps (Chronological)** - Timestamped troubleshooting progression from bottom to top:
- 23:49:09: Contacted user Mathew Taylor - WiFi shows connected but browser returns blank pages
- 23:51:02: Ran ipconfig - confirmed valid IP from DHCP
- 23:52:53: Ping 192.x gateway successful (0% loss, 4-19ms) - device communicates with router
- 23:54:34: Ping 8.8.8.8 successful (0% loss, 4-20ms) - internet connection working
- 23:55:45: Root cause identified - DNS resolution failure

![Screenshot n2](./screenshots/n2.png)  
**ServiceNow Work Notes - Resolution Actions** - Resolution steps documented from bottom to top:
- 23:56:55: Flushed DNS cache (ipconfig /flushdns) - resolver cache cleared
- 23:59:01: Manually configured Google DNS (8.8.8.8 / 8.8.4.4) via Network Connections > WiFi Properties > IPv4 Properties
- 00:01:15: Disabled WiFi adapter (Intel Wi-Fi 6 AX201 160MHz) in Device Manager to reset connection
- 00:02:07: Re-enabled adapter - connection re-established cleanly
- 00:03:09: Browser test successful - google.com loads, full internet access restored

![Screenshot o2](./screenshots/o2.png)  
**ServiceNow Resolution Information Tab** - Resolution code: "Solution provided." Resolution notes document complete troubleshooting workflow and root cause: DNS resolution failure - device connected to WiFi and could reach router/internet via IP (ping successful) but local DNS server not resolving domain names. Resolution steps listed: 1) Flush DNS cache, 2) Configure Google DNS servers (8.8.8.8 / 8.8.4.4), 3) Disable and re-enable adapter. Verified resolution: user confirmed websites loading properly, internet access fully restored, ticket closed.

![Screenshot p2](./screenshots/p2.png)  
**ServiceNow Incidents List - Ticket Resolved** - ServiceNow dashboard with blue info banner at top: "INC0010007 has been resolved." Incidents list shows INC0010007 status changed to "Resolved" (Mathew Taylor, "Wi-Fi connected with full signal but websites won't load", updated 2026-05-17 00:08:56). Demonstrates complete incident lifecycle from assignment through resolution.

## Outcome

**Time to Resolution:** 14 minutes (23:49:09 - 00:03:09)  
**Impact:** Single user  
**Root Cause:** DNS resolution failure  
**Resolution:** DNS cache flush + Google DNS configuration + adapter reset

## Technical Skills Demonstrated

- Systematic network troubleshooting methodology (no guessing - layer-by-layer isolation)
- TCP/IP fundamentals (DHCP, DNS, gateway, IP addressing)
- Command-line diagnostics (ipconfig, ping)
- DNS troubleshooting (cache flush, manual server configuration)
- Windows network adapter management (Device Manager)
- ServiceNow incident documentation with detailed work notes
- Sub-15-minute resolution time for Priority 1 issue
- Professional user communication and expectation management

## Key Takeaways

This is one of the most common help desk tickets. WiFi shows "Connected" with full bars, but nothing loads - confusing for beginners because it LOOKS like you have internet. The professional approach:

1. **Test each layer systematically** - router connectivity (ping gateway), internet connectivity (ping 8.8.8.8), DNS resolution (domain names)
2. **No guessing** - step-by-step isolation identifies root cause quickly
3. **Google DNS (8.8.8.8 / 8.8.4.4)** is reliable fallback when ISP DNS fails
4. **Document everything** - work notes show clear troubleshooting logic for knowledge transfer

Following this structured approach builds user trust and demonstrates professional competence. Users gave you their device - methodical troubleshooting shows you know what you're doing.
