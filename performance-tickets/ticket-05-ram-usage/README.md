# High RAM Usage - Applications Freezing

## Incident Information

**Incident Number:** INC0010010  
**Category:** Hardware  
**Subcategory:** Memory  
**Priority:** 3 - Moderate  
**Impact:** 2 - Medium  
**Urgency:** 2 - Medium  
**Assignment Group:** Help Desk  
**Assigned To:** Dev Patel  
**Caller:** Luke Wilson

## Problem Statement

User reported computer slow with applications freezing and crashing when running multiple programs. System experiencing extreme slowdowns during multitasking.

## Symptoms

- Applications freeze frequently
- Programs crash when running multiple applications simultaneously
- Computer extremely slow during multitasking
- System becomes unresponsive
- Applications take extended time to open

## Root Cause

Critically high RAM utilization at 94% (7.4 GB of 8.0 GB total capacity) caused by Google Chrome browser consuming over 1,832 MB memory across 22 separate processes. Additional memory consumption from 10 simultaneously open browser tabs containing media-heavy content (Gmail, Facebook, Outlook, weather, Azure portal, workday applications) and 6 installed Chrome extensions consuming background resources.

## Diagnostic Process

1. Opened Task Manager to verify system resource usage
2. Examined Memory column in Processes tab showing 94% utilization
3. Identified Google Chrome as primary memory consumer with 22 processes running
4. Reviewed Performance tab confirming 6.3 GB used of 7.8 GB available (81% utilization)
5. Inspected Chrome browser revealing 10 tabs open simultaneously
6. Examined Chrome extensions finding 6 extensions installed with security warnings
7. Verified system RAM capacity at 8.0 GB total installed memory

## Resolution Steps

1. Opened Task Manager and navigated to Processes tab
2. Reviewed Memory column identifying 94% utilization critically high
3. Located Google Chrome consuming 1,832.9 MB with 22 separate processes
4. Clicked Performance tab to view detailed Memory statistics
5. Confirmed 6.3 GB in use (456 MB) with only 1.5 GB available
6. Opened Google Chrome browser to identify open tabs
7. Counted 10 tabs open simultaneously including Gmail Facebook Outlook weather Azure portal workday applications
8. Accessed Chrome Extensions via three-dot menu and Manage extensions
9. Identified 6 extensions installed: Google Docs Offline, Less Notifications, McAfee WebAdvisor, Quick Speedtest, Screen Addict, Search Manager
10. Noted multiple extensions flagged with security warnings (policy violations, malware warnings, untrusted status)
11. Returned to Task Manager Processes tab
12. Selected Google Chrome process and clicked End task button
13. Verified memory usage dropped from 94% to 56% after Chrome termination
14. Confirmed Memory column showing significant reduction with available memory increased
15. Recommended removing unnecessary browser extensions with security warnings
16. Advised limiting open browser tabs to 5-7 maximum for optimal performance
17. Documented resolution steps in ServiceNow Work Notes
18. Updated incident to Resolved status

## Commands Executed

None - GUI-based troubleshooting using Task Manager and Chrome browser

## Screenshots

![Screenshot a5](./screenshots/a5.png)  
ServiceNow incidents list showing INC0010010 In Progress - Priority 3 Moderate assigned to Dev Patel

![Screenshot b5](./screenshots/b5.png)  
Task Manager Processes tab showing CPU 94% Memory 94% with Google Chrome 22 separate processes consuming 1,832.9 MB

![Screenshot c5](./screenshots/c5.png)  
Task Manager Performance tab Memory section displaying 8.0 GB total with 6.3 GB used 1.5 GB available 81% utilization

![Screenshot d5](./screenshots/d5.png)  
Google Chrome browser showing 10 tabs open simultaneously including Gmail Facebook Outlook weather Azure portal workday applications

![Screenshot e5](./screenshots/e5.png)  
Chrome Extensions page displaying 6 extensions with security warnings policy violations malware alerts untrusted status

![Screenshot f5](./screenshots/f5.png)  
Task Manager Processes tab showing Memory 68% with multiple Google Chrome processes still consuming resources

![Screenshot g5](./screenshots/g5.png)  
Task Manager Processes tab showing Memory 24% 56% after Chrome browser termination significant memory freed

![Screenshot h5](./screenshots/h5.png)  
ServiceNow incident INC0010010 details page showing Resolved state Hardware category Memory subcategory

![Screenshot i5](./screenshots/i5.png)  
ServiceNow Work Notes documenting Chrome process analysis browser tab inspection extensions review memory consumption findings

![Screenshot j5](./screenshots/j5.png)  
ServiceNow Resolution Information showing detailed resolution steps memory reduction browser optimization recommendations

![Screenshot k5](./screenshots/k5.png)  
ServiceNow incidents list showing INC0010010 Resolved status with resolution notification banner

## Outcome

**Time to Resolution:** 28 minutes  
**Status:** Resolved  
**Resolution Code:** Solution provided  
**Memory Freed:** 38% (from 94% to 56% utilization after Chrome termination)  
**Verified:** User confirmed immediate performance improvement with applications responding normally and multitasking capability restored

## Technical Skills Demonstrated

- Windows Task Manager resource monitoring
- RAM usage analysis and troubleshooting
- Browser memory consumption identification
- Chrome process management
- Browser extension security assessment
- System memory capacity evaluation
- Performance optimization recommendations
- ServiceNow incident documentation

## Key Insights

RAM stands for Random Access Memory serving as temporary working memory Windows uses to run applications. When memory usage reaches critically high levels system performance degrades dramatically causing freezing lagging and slow multitasking. Browser applications especially Chrome are biggest memory consumers with each open tab and extension creating separate processes. Modern applications and Windows 11 require minimum 16GB RAM with 32GB recommended for heavy multitasking. Limiting browser tabs to 5-7 maximum and removing unnecessary extensions significantly reduces memory consumption. Closing memory-intensive applications immediately frees RAM without requiring system restart.
