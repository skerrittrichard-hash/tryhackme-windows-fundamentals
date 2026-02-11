# TryHackMe Windows Fundamentals - Room 2: Quick Reference Cheatsheet

Fast reference for accessing tools, commands, and managing Windows administration.

---

## Quick Access - Keyboard Shortcuts

### Launching Administrative Tools
```
Win+R                  Open Run dialog (type command to execute)
Ctrl+Shift+Esc        Open Task Manager (fastest)
Win+I                 Open Settings
Win+E                 Open File Explorer
Win+X                 Quick admin menu
```

### Windows Pause Menu
```
Win+Pause/Break        System Properties
Win+D                  Show/hide desktop
Win+V                  Clipboard history (if enabled)
Alt+Tab                Switch between apps
```

---

## Administrative Tools - Launch Methods

### Quickest Method (Win+R)
```
Win+R → [command below] → Enter
```

### Tools Quick Reference

| Tool | Command | Function |
|------|---------|----------|
| System Configuration | msconfig | Startup/services/boot options |
| Task Scheduler | taskschd.msc | Schedule automated tasks |
| Computer Management | compmgmt.msc | Central admin hub |
| Services | services.msc | Manage background services |
| Device Manager | devmgmt.msc | Hardware management |
| Event Viewer | eventvwr.msc | System event logs |
| Disk Management | diskmgmt.msc | Partitions and volumes |
| Task Manager | taskmgr | Processes and performance |
| Resource Monitor | resmon | Real-time resource usage |
| Performance Monitor | perfmon | Performance tracking |
| Registry Editor | regedit | System database editor |
| System Information | msinfo32 | System details |
| User Accounts | netplwiz | Manage user accounts |
| Group Policy | gpedit.msc | System policies (Pro/Enterprise) |
| Command Prompt | cmd | Command-line interface |
| PowerShell | powershell | Advanced scripting/admin |
| UAC Settings | UserAccountControlSettings.exe | Change UAC notification level |

---

## System Configuration (msconfig)

### Access
```
Win+R → msconfig → Enter
Or: Settings → System → About → Advanced system settings → Startup
```

### Boot Options
- **Normal startup** - All drivers and services
- **Diagnostic startup** - Minimal drivers/services (troubleshooting)
- **Selective startup** - Selected services only

### Service Management
- Check box = Enable service at boot
- Uncheck box = Disable (won't start at boot)
- Can still manually start if disabled

### Startup Tab
- Shows programs that launch at login
- Disable unnecessary = faster boot
- Can re-enable anytime

### Tools Tab
- Quick access to Device Manager, Registry, etc.
- Click tool name → Click Launch

### Crash Dump Options
```
Startup & Recovery → Write Debugging Information dropdown

Options:
- None (don't save)
- Small memory dump (256 KB)
- Kernel memory dump (kernel only)
- Complete memory dump (entire RAM)
- Automatic memory dump (Windows decides)
```

---

## Task Scheduler

### Access
```
Win+R → taskschd.msc → Enter
Or: Computer Management → Task Scheduler
```

### Create Scheduled Task
1. Right-click Task Scheduler Library → Create Task
2. General tab - Name task
3. Triggers tab - When to run (daily, weekly, at logon, etc.)
4. Actions tab - What program to run
5. Conditions tab - Optional conditions (battery level, network, etc.)
6. Settings tab - Repeat, stop if running too long, etc.

### Common Triggers
- At logon
- At startup
- Daily at specific time
- Weekly on specific day/time
- On event (error logged, etc.)
- On connection to network

### Task States
- Ready - Ready to run
- Running - Currently running
- Queued - Waiting to start
- Disabled - Won't run

### Manage Existing Task
- Right-click task → Run (run immediately)
- Right-click task → End (stop running)
- Right-click task → Delete (remove)
- Right-click task → Properties (edit)

---

## Computer Management

### Access
```
Win+R → compmgmt.msc → Enter
Or: Right-click "This PC" → Manage
```

### Main Sections
1. **System Tools** - Task Scheduler, Event Viewer, Performance Monitor
2. **Storage** - Disk Management, Disk Defragmentation
3. **Services & Applications** - Services, WMI Control

### Services Management
- Right-click service → Start/Stop/Restart
- Right-click → Properties → Startup type (Automatic/Manual/Disabled)
- Log Name tab - View logs when service fails

### Device Manager
- Expand categories to see devices
- Yellow ! = Driver missing/broken
- Right-click → Update driver
- Right-click → Disable device
- Right-click → Uninstall device

### Event Viewer
- Application - App errors and events
- Security - Login, account changes, security events
- System - Driver/service/OS errors
- Click event to see details

---

## Services Management

### Access Services
```
Win+R → services.msc → Enter
Or: Computer Management → Services
Or: Task Manager → Services tab
```

### Service States
| State | Running | Restarting |
|-------|---------|-----------|
| Running | ✓ | - |
| Stopped | - | - |
| Paused | Partially | - |

### Startup Types
- **Automatic** - Starts at boot
- **Automatic (Delayed Start)** - Starts shortly after boot
- **Manual** - Starts when needed
- **Disabled** - Never starts

### Common Services

**Critical (don't disable):**
- Networking
- Remote Procedure Call (RPC)
- Windows Update
- Event Log
- Task Scheduler

**Optional (safe to disable):**
- Print Spooler (if no printers)
- Bluetooth (if no Bluetooth devices)
- Xbox Live Gaming Service (if not used)
- Windows Media Player Network Sharing

### Service Properties
```
Right-click service → Properties

- General tab: Current status, startup type
- Log On tab: Account running service
- Recovery tab: What to do if service crashes
- Dependencies tab: Other services needed
```

---

## Event Viewer

### Access
```
Win+R → eventvwr.msc → Enter
Or: Computer Management → Event Viewer
```

### Log Types

**Application**
- Programs crashing
- Application errors
- Installation issues

**Security**
- Login attempts
- Account changes
- Permission denied errors
- Security events

**System**
- Driver failures
- Hardware errors
- Service crashes
- OS errors

### Reading Events
```
Level:
- Error (red) - Something failed
- Warning (yellow) - Potential problem
- Information (white) - Noteworthy event
- Success (green) - Operation succeeded
```

### Troubleshooting Steps
1. Open Event Viewer → System or Application
2. Sort by date descending (newest first)
3. Look for red "Error" entries
4. Click error to read full message
5. Error description often explains the problem

---

## Registry Editor

### Access
```
Win+R → regedit → Enter
Or: regedit.exe
```

### Main Hives

**HKEY_LOCAL_MACHINE (HKLM)**
- System-wide settings
- Don't change unless you know what you're doing

**HKEY_CURRENT_USER (HKCU)**
- Current logged-in user settings
- Safer to modify than HKLM

**HKEY_CLASSES_ROOT**
- File associations
- COM objects

**HKEY_USERS**
- All user profiles
- Each user's settings

**HKEY_CURRENT_CONFIG**
- Hardware profiles
- Display settings

### Navigation
- Left pane - Folder tree structure
- Right pane - Values in current location
- Double-click folder to expand
- Double-click value to edit

### Value Types
- **REG_SZ** - Text string
- **REG_DWORD** - 32-bit number
- **REG_QWORD** - 64-bit number
- **REG_BINARY** - Binary data
- **REG_MULTI_SZ** - Multiple lines of text

### Basic Operations

**Find a registry value:**
```
Edit → Find
Type search term
Click Find All
```

**Add new value:**
```
Right-click empty space
New → [Type]
Name the value
Enter the data
```

**Edit existing value:**
```
Double-click value
Modify data
Click OK
```

**Delete value:**
```
Right-click value
Delete
Confirm
```

### Backup & Restore

**Backup (before editing):**
```
File → Export
Choose location and filename
Click Save
```

**Restore (if something breaks):**
```
File → Import
Select backup file
Click Open
Confirm
```

### Important Registry Paths

```
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion
→ Windows version and installation info

HKLM\SYSTEM\CurrentControlSet\Services
→ All installed services

HKCU\Software\Microsoft\Windows\CurrentVersion\Run
→ Programs that run at user logon

HKCU\Software\Microsoft\Windows
→ User interface settings
```

---

## User Account Control (UAC)

### Access UAC Settings
```
Win+R → UserAccountControlSettings.exe → Enter
Or: Settings → System → About → Advanced system settings → User Account Control
```

### Notification Levels

**Level 1 (Never notify)** - Least secure
- No UAC prompts
- Dangerous: Malware can run silently

**Level 2 (Notify when apps make changes)** - DEFAULT
- Prompts when programs modify system
- Doesn't prompt for Settings app changes
- Balance of security and usability

**Level 3 (Always notify)** - Most secure
- Prompts for any system change
- Very annoying but maximally secure

**Level 4 (Never notify + disable)** - Most dangerous
- UAC completely off
- Not recommended

### Using UAC

**Admin approval (Administrator account):**
- Program requests admin
- UAC prompt: "Allow this app to make changes?"
- Click Yes
- Program runs with elevated privileges

**Credential prompt (Standard user):**
- Program requests admin
- UAC prompt: "Enter administrator password"
- Type admin password
- Program runs with elevated privileges

### Running Program as Administrator
```
Right-click program → Run as administrator
```

---

## Resource Monitor

### Access
```
Win+R → resmon → Enter
Or: Task Manager → Performance tab → Open Resource Monitor
```

### Tabs Overview

**CPU Tab**
- Process name, CPU %, Threads
- Sort by % descending to find CPU hog
- Right-click process → End to kill

**Memory Tab**
- Working Set (RAM used), Shareable, Committed
- Find memory leaks (growing usage)

**Disk Tab**
- Process doing I/O, Read/Write speeds
- Find what's hammering the disk

**Network Tab**
- Process using network, Bytes sent/received
- Find bandwidth hogs

### Troubleshooting
```
System slow? → Resource Monitor
→ Identify bottleneck (CPU/Memory/Disk/Network)
→ See which process causing it
→ Kill the process or investigate
```

---

## Performance Monitor

### Access
```
Win+R → perfmon → Enter
Or: Computer Management → Performance Monitor
```

### Creating Performance Baseline
1. Performance Monitor → Create Data Collector Set
2. Add counters: CPU, Memory, Disk, Network
3. Run for 24 hours
4. Review graph to see normal usage patterns

### Monitoring
- View → Graph (real-time display)
- View → Report (summary statistics)
- View → Histogram (bar graph)

### Performance Counters (Examples)
- Processor → % Processor Time
- Memory → Available MBytes
- PhysicalDisk → % Disk Time
- Network Interface → Bytes Sent/Received

---

## Command Prompt & PowerShell

### Access
```
Win+R → cmd → Enter (Command Prompt)
Win+R → powershell → Enter (PowerShell)
Or: Right-click Start → Command Prompt/PowerShell
```

### System Information Commands
```
systeminfo              Full system information
systeminfo | findstr /c:"OS Name"  Just OS name
tasklist                List running processes
tasklist /v            Detailed process list
Get-ComputerInfo       PowerShell system info
```

### Service Commands (Command Prompt)
```
sc query                List all services
sc query <name>        Query specific service
sc start <name>        Start service
sc stop <name>         Stop service
sc config <name> start= disabled  Disable service
sc config <name> start= auto      Auto-start
```

### Service Commands (PowerShell)
```
Get-Service             List all services
Get-Service -Name <name>  Get specific service
Start-Service -Name <name>  Start service
Stop-Service -Name <name>   Stop service
Set-Service -StartupType Disabled  Disable
Set-Service -StartupType Automatic  Auto-start
```

### Network Commands
```
ipconfig                Show IP configuration
ipconfig /all           Detailed network info
ipconfig /release       Release IP address
ipconfig /renew         Request new IP
getmac                  Show MAC address
nslookup <hostname>     DNS lookup
tracert <hostname>      Trace network path
```

### Process Management
```
tasklist                List processes
tasklist /v            Detailed processes
taskkill /pid 1234     Kill by process ID
taskkill /im app.exe   Kill by application name
wmic process list      List processes via WMI
```

### Registry Commands (Command Prompt)
```
reg query HKLM\...     Query registry key
reg add HKLM\... /v name /d value  Add value
reg delete HKLM\... /v name        Delete value
```

### Registry Commands (PowerShell)
```
Get-ItemProperty -Path 'HKLM:\...'  Query key
New-ItemProperty -Path 'HKLM:\...' -Name key -Value val  Add
Remove-ItemProperty -Path 'HKLM:\...' -Name key  Delete
```

### Getting Help
```
help <command>         Show help for command
<command> /?           Show help (most commands)
Get-Help <command>     PowerShell help
```

---

## WMI Commands

### WMIC (WMI Command-line)
```
wmic os get caption            Windows version
wmic computersystem get name   Computer name
wmic logicaldisk get name,size,freespace  Disk info
wmic process list              All processes
wmic service list              All services
```

### PowerShell WMI
```
Get-WmiObject Win32_OperatingSystem  OS info
Get-WmiObject Win32_ComputerSystem   Hardware info
Get-WmiObject Win32_Process          Processes
Get-WmiObject Win32_Service          Services
```

### Remote WMI Query
```
wmic /node:computername process list
→ Query remote computer's processes
```

---

## System Information Utility

### Access
```
Win+R → msinfo32 → Enter
```

### Key Information Shown
- Windows version and build
- System manufacturer and model
- Processor name and speed
- Installed RAM
- System boot time
- Windows directory location
- Network adapters
- Environment variables

### Environment Variables Tab
- View all system variables
- ComSpec → Command interpreter (cmd.exe path)
- Path → Where executables are found
- Temp → Temporary files location
- UserProfile → User's home directory

---

## Disk Management

### Access
```
Win+R → diskmgmt.msc → Enter
Or: Computer Management → Disk Management
```

### Main View
- **Top section** - Volumes (logical drives)
- **Bottom section** - Physical disks and partitions

### Common Tasks
- Right-click volume → Extend Volume (add space)
- Right-click volume → Shrink Volume (reduce size)
- Right-click unallocated space → New Simple Volume (create drive)

---

## Quick Troubleshooting Checklist

### System Running Slow
```
□ Open Task Manager → Performance tab
□ Identify bottleneck (CPU/Memory/Disk/Network)
□ If CPU high: Resource Monitor → Processes → End heavy process
□ If Memory high: Close unnecessary programs, add RAM
□ If Disk high: Run disk cleanup, defragment
□ Check Event Viewer for errors
```

### Service Not Starting
```
□ Open Services
□ Right-click service → Properties
□ Check Startup type (Automatic?)
□ Click Start button
□ Check Status (should be Running)
□ If still fails, check Event Viewer for error message
```

### Can't Install Program
```
□ Right-click installer → Run as administrator
□ Check disk space available
□ Disable antivirus temporarily
□ Check Windows version compatibility
□ Review Event Viewer → Application for errors
```

### Blue Screen/Crash
```
□ Get crash dump file at C:\Windows\Memory.dmp
□ Check Event Viewer → System for Stop Code
□ Search error code online
□ Common fixes: Update drivers, restore system point, repair Windows
```

---

## File Locations

```
msconfig location:     C:\Windows\System32\msconfig.exe
Registry location:     C:\Windows\System32\config\
Crash dump:           C:\Windows\Memory.dmp
Event logs:           C:\Windows\System32\winevt\Logs\
Task Scheduler jobs:  C:\Windows\System32\Tasks\
Temp files:           C:\Users\[username]\AppData\Local\Temp\
```

---

## Key Takeaways

1. **msconfig** - First stop for startup/service troubleshooting
2. **Task Scheduler** - Automate routine maintenance
3. **Event Viewer** - Find out WHY something failed
4. **Registry** - Backup before editing (never)
5. **Resource Monitor** - Identify performance bottlenecks
6. **Services** - Disable what you don't use
7. **Command-line** - Faster than GUI for repeatable tasks
8. **UAC** - Keep it on (security vs convenience)

---

**Use this cheatsheet alongside the detailed notes for quick lookups.**
