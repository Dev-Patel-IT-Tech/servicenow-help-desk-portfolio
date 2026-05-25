# Slow Computer Performance - High Disk Usage

## Incident Information

**Incident Number:** INC0010009  
**Category:** Hardware  
**Priority:** 3 - Moderate  
**Impact:** 2 - Medium  
**Urgency:** 2 - Medium  
**Assignment Group:** Help Desk  
**Assigned To:** Dev Patel  
**Caller:** Rob Phillips

## Problem Statement

User reported computer extremely slow with applications freezing and lagging. Files not opening properly. System experiencing severe performance degradation.

## Symptoms

- Computer running extremely slow
- Applications freeze frequently
- Everything lags during normal operations
- Files and programs not opening properly
- System performance significantly degraded

## Root Cause

Critically low disk space (16.8 GB free of 236 GB) combined with excessive temporary file accumulation (29.6 GB) and unnecessary startup programs causing system performance degradation. Disk usage spikes reported reaching 100% during normal operations.

## Diagnostic Process

1. Confirmed issue by opening Task Manager and reviewing Processes tab
2. Examined Disk column to identify high disk usage patterns
3. Identified processes consuming disk resources
4. Checked Startup Apps for unnecessary programs launching at boot
5. Verified drive type and capacity in This PC
6. Reviewed Storage Settings to analyze disk space breakdown
7. Located temporary files accumulation in AppData Local Temp folder

## Resolution Steps

1. Opened Task Manager to verify disk usage patterns
2. Reviewed Processes tab and examined Disk column showing current 4% usage
3. Accessed Startup apps section in Task Manager
4. Identified unnecessary startup applications consuming resources
5. Disabled non-essential startup programs (Microsoft 365 Copilot, Microsoft Teams, JukeboxPlayer, EpicGamesLauncher)
6. Opened This PC to check available storage space
7. Confirmed C: drive showing 16.8 GB free of 236 GB total capacity
8. Opened Windows Settings and navigated to System Storage
9. Reviewed Storage breakdown showing 220 GB used with 29.6 GB temporary files
10. Navigated to C:\Users\dev patel\AppData\Local\Temp folder
11. Found 2,189 temporary files accumulated over extended period
12. Selected all temporary files for deletion
13. Executed Disk Cleanup utility on C: drive
14. Selected cleanup categories: Temporary Internet Files, Recycle Bin, system temporary files
15. Confirmed deletion and initiated cleanup process
16. Monitored cleanup progress (2,269 items recycled from Temp folder)
17. Verified total disk space freed exceeded 500 MB
18. Documented resolution steps in ServiceNow Work Notes
19. Confirmed with user immediate performance improvement
20. Updated incident to Resolved status

## Commands Executed

None - GUI-based troubleshooting using Task Manager, File Explorer, and Windows Storage Settings

## Screenshots

![Screenshot a4](./screenshots/a4.png)  
ServiceNow incidents list showing INC0010009 In Progress - Priority 3 Moderate assigned to Dev Patel

![Screenshot b4](./screenshots/b4.png)  
Task Manager Processes tab showing CPU 40% Memory 83% Disk 4% Network 0% current system resource usage

![Screenshot c4](./screenshots/c4.png)  
Task Manager Startup apps tab displaying enabled and disabled applications with startup impact

![Screenshot d4](./screenshots/d4.png)  
File Explorer This PC view showing Windows C: drive 16.8 GB free of 236 GB with red capacity indicator

![Screenshot e4](./screenshots/e4.png)  
Task Manager Startup apps with Microsoft 365 Copilot JukeboxPlayer and other programs showing Disabled status

![Screenshot f4](./screenshots/f4.png)  
Windows Settings System Storage showing C: drive 220 GB used 16.8 GB free with Temporary files 29.6 GB breakdown

![Screenshot g4](./screenshots/g4.png)  
File Explorer Temp folder C:\Users\dev patel\AppData\Local\Temp displaying 2,189 items before cleanup

![Screenshot h4](./screenshots/h4.png)  
File Explorer Temp folder with all 2,189 items selected showing file types and sizes ready for deletion

![Screenshot i4](./screenshots/i4.png)  
Windows Disk Cleanup for C: drive dialog with Temporary Internet Files Recycle Bin categories selected

![Screenshot j4](./screenshots/j4.png)  
Disk Cleanup confirmation dialog asking Are you sure you want to permanently delete these files

![Screenshot k4](./screenshots/k4.png)  
File Explorer showing Recycling 2,269 items from Temp progress bar at 58% complete

![Screenshot m4](./screenshots/m4.png)  
ServiceNow incident INC0010009 details page showing In Progress state Hardware category

![Screenshot n4](./screenshots/n4.png)  
ServiceNow Work Notes documenting diagnostic steps including Task Manager review Storage analysis and Temp folder cleanup

![Screenshot o4](./screenshots/o4.png)  
ServiceNow Resolution Information showing Resolved status with detailed resolution steps and user confirmation

## Outcome

**Time to Resolution:** 34 minutes  
**Status:** Resolved  
**Resolution Code:** Solution provided  
**Disk Space Freed:** 500+ MB  
**Verified:** User confirmed immediate performance improvement with applications opening faster and system lag eliminated

## Technical Skills Demonstrated

- Windows Task Manager resource monitoring
- Disk usage analysis and troubleshooting
- Startup program management
- Windows Storage Settings navigation
- Temporary file identification and cleanup
- Disk Cleanup utility operation
- System performance optimization
- ServiceNow incident documentation

## Key Insights

100% disk usage does not mean storage is full but indicates the drive is heavily used by background processes. Task Manager Disk column identifies processes causing high disk activity. Startup programs launching automatically at boot consume disk resources unnecessarily. Temporary files accumulate over time from application installations updates and system processes. Regular temp folder cleanup and Disk Cleanup utility execution prevent performance degradation. Low disk space under 10% capacity significantly impacts Windows performance. Disabling non-essential startup applications reduces boot time and background disk usage.
