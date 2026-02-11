# TryHackMe Windows Fundamentals - Room 2: Detailed Notes

Comprehensive explanations of Windows system administration concepts covered in Room 2.

---

## Task 1: System Configuration & Advanced System Settings

### System Configuration Utility (msconfig)

**What is msconfig?**
System Configuration is a Windows utility that provides access to critical system settings in one place. It's where sysadmins go to manage startup services, boot options, and troubleshoot system issues.

**Access msconfig:**
```
Win+R → msconfig → Enter
Or: Windows search → "System Configuration"
```

### Boot Tab

**Boot Options:**
- Normal startup - Load all drivers and services
- Diagnostic startup - Load minimal drivers/services (troubleshooting)
- Selective startup - Load selected services (customized startup)

**Why use this?**
When troubleshooting, disable services one at a time to find what's breaking the system. Diagnostic mode is the fastest way to test if a service is the problem.

**Boot Timeout:**
Controls how long GRUB/boot menu appears. Default is 30 seconds. Longer timeout = more time to select boot options.

**Safe Mode options:**
- Minimal (minimal drivers)
- Alternate Shell (command-line only)
- Network (with network drivers)

**Use case:** If malware prevents normal booting, Safe Mode with Networking lets you download antivirus.

### Services Tab

**What are services?**
Programs that run in the background without user interaction. Examples: Windows Update, Print Spooler, Network Discovery.

**Service startup types:**
- Automatic - Starts at boot
- Manual - Starts on demand
- Disabled - Never starts (even if requested)

**Managing services in msconfig:**
1. Check the box to enable service at boot
2. Uncheck to disable (won't start at boot)
3. Services still running can be manually started later

**Important caution:**
Disabling critical services (like Networking, Security) breaks Windows. Always know what a service does before disabling it.

### Startup Tab

**What's the difference between Services and Startup?**
- **Services tab** - System services (run as SYSTEM or Network Service account)
- **Startup tab** - User applications (run as logged-in user, like browser, antivirus)

**Managing startup programs:**
Disable unnecessary startup programs to speed up boot time. Each unchecked program saves seconds.

**Example:**
- Keep: Security software, essential utilities
- Disable: Games, media players, chat apps (auto-start wastes RAM)

### Tools Tab

Quick access to administrative tools without memorizing commands:

- **Device Manager** - Hardware management
- **Disk Management** - Partition management
- **Services** - Service management
- **Event Viewer** - System logs
- **Registry Editor** - System database
- **Performance Monitor** - Performance tracking
- **System Information** - Hardware/software details
- **Task Scheduler** - Scheduled tasks
- **Disk Cleanup** - Free disk space
- **Defragmentation** - Optimize disk

### Write Debugging Information (Crash Dump Types)

**When Windows crashes:**
A crash dump saves system memory to disk so crashes can be analyzed later.

**Dump types:**
- **None** - Don't save anything (default for servers)
- **Small memory dump (256 KB)** - Minimal info, saves quickly
- **Kernel memory dump** - Saves only kernel memory (useful for driver crashes)
- **Complete memory dump** - Saves entire RAM (useful for detailed analysis)
- **Automatic memory dump** - Windows decides what to save

**Sysadmin use:**
When a server crashes mysteriously, the crash dump file (C:\Windows\Memory.dmp) contains clues about what failed.

---

## Task 2: Task Scheduler & Computer Management

### Task Scheduler

**What is Task Scheduler?**
A Windows utility that runs programs or scripts on a schedule (like cron on Linux).

**Access Task Scheduler:**
```
Win+R → taskschd.msc → Enter
Or: Admin Tools → Task Scheduler
```

**Creating a task:**
1. Right-click Task Scheduler Library → Create Task
2. Name the task
3. Set trigger (when to run: daily, weekly, at logon, etc.)
4. Set action (what program to run)
5. Set conditions (only if battery > 50%, only on WiFi, etc.)

**Real-world examples:**
- Daily antivirus scan at 2 AM
- Weekly system backup every Sunday at 1 AM
- Monthly cleanup of temp files
- Security scan on network connection

**Task Scheduler vs Services:**
- **Task Scheduler** - Runs programs/scripts on schedule
- **Services** - Always running in background

### Computer Management

**What is Computer Management?**
Central hub for all system management tasks. Contains System Tools, Storage, and Services/Applications sections.

**Access Computer Management:**
```
Win+R → compmgmt.msc → Enter
Or: Right-click This PC → Manage
```

**Key sections:**

**System Tools:**
- Task Scheduler - Schedule tasks
- Event Viewer - View system logs
- Performance Monitor - Monitor performance
- Device Manager - Manage hardware
- Disk Management - Manage partitions
- Services - Manage background services

**Storage:**
- Disk Management - Partition management
- Disk Defragmentation - Optimize disk

**Services & Applications:**
- Services - Manage running services
- WMI Control - Remote management
- Services for NFS - Network file services

### Services in Computer Management

**What are Services?**
Background programs providing functionality:
- Networking (TCP/IP stack)
- Print Spooler (printing)
- Windows Update (updates)
- Security essentials

**Service States:**
- Running - Service is active
- Stopped - Service is inactive
- Paused - Service temporarily stopped

**Service startup types:**
- Automatic - Starts at boot
- Manual - Starts on demand
- Disabled - Won't start

**Why manage services?**
- Start/stop for troubleshooting
- Disable unused services (improves boot time)
- Set startup type (automatic vs manual)
- Monitor service status

**Example:**
If Print Spooler is disabled, printing fails. Enable it with Services.

### Event Viewer

**What is Event Viewer?**
A log of everything happening on the system. Every error, warning, and event is logged.

**Log types:**
- **Application** - Application errors and events
- **Security** - Login attempts, account changes, security events
- **System** - Driver issues, service failures, OS errors

**Finding errors:**
1. Open Event Viewer
2. Click Application (or System)
3. Look for Red "Error" entries
4. Click to see detailed message

**Sysadmin use:**
When something fails, Event Viewer tells you why. Is it a driver problem? Permission issue? Out of disk space?

---

## Task 3: Advanced System Settings & Performance

### System Protection & Restore Points

**What is System Protection?**
A backup of system files and registry that can restore Windows to a previous state.

**How it works:**
1. Windows automatically creates restore points before major changes
2. If system becomes unstable, restore to previous point
3. Restores system files, registry, drivers
4. Doesn't restore personal files (documents, photos stay)

**Manual restore point:**
1. Settings → System → System Protection → Create
2. Name the point (e.g., "Before installing graphics driver")
3. If driver breaks system, restore to this point

**Sysadmin use:**
Before installing critical updates or driver, create restore point. If something breaks, you can rollback.

### Startup and Recovery Settings

**Startup options:**
- **Default OS** - Which Windows version boots by default (multi-boot systems)
- **Timeout** - How long to wait before booting default OS

**Recovery options:**
- **Write event to log** - Record crash in Event Viewer
- **Send admin alert** - Alert administrator of crash
- **Automatic restart** - Reboot after crash
- **Crash dump** - Save memory for analysis

**Example use case:**
If server crashes at 3 AM unattended, automatic restart ensures it's back online. Crash dump lets you analyze what caused it.

### Performance Options

**What affects performance?**
- Visual Effects (animations, transparency)
- Processor scheduling (favor programs vs background services)
- Virtual memory (use disk as RAM when memory runs out)

**Visual Effects:**
Modern Windows has animations and transparency that use CPU. Disable them on older machines.

- **Animate windows when minimizing/maximizing** - Fancy but slower
- **Fade or slide menus into view** - Fancy but slower
- **Use smooth scrolling** - Fancy but slower
- **Show thumbnails instead of icons** - Slower on network drives

**Processor Scheduling:**
- **Programs** - Favor foreground application (faster responsiveness)
- **Background services** - Favor background tasks (better for servers)

**Virtual Memory:**
RAM is fast, disk is slow. Windows can use disk space as virtual RAM.

**How it works:**
When RAM fills up, Windows moves unused data to disk (pagefile.sys). When program needs it, Windows retrieves from disk.

**Performance impact:**
Disk is 100x slower than RAM. Excessive paging destroys performance. Solution: Add more RAM.

---

## Task 4: Windows Registry

### What is the Registry?

**Definition:**
A hierarchical database storing all Windows and application settings. Like a giant config file for entire system.

**Registry file locations:**
```
C:\Windows\System32\config\
- SAM (user accounts)
- SECURITY (security settings)
- SOFTWARE (installed programs)
- SYSTEM (system settings)
- DEFAULT (default user settings)
```

### Registry Structure

**Hives (root keys):**
- **HKEY_LOCAL_MACHINE (HKLM)** - System-wide settings
- **HKEY_CURRENT_USER (HKCU)** - Current user settings
- **HKEY_CLASSES_ROOT** - File associations, COM objects
- **HKEY_USERS** - All user profiles
- **HKEY_CURRENT_CONFIG** - Hardware profiles

**Example hierarchy:**
```
HKEY_LOCAL_MACHINE
├── SOFTWARE
│   ├── Microsoft
│   │   ├── Windows
│   │   │   ├── CurrentVersion
│   │   │   └── ...
│   │   └── ...
│   └── ...
├── SYSTEM
│   ├── CurrentControlSet
│   │   ├── Services
│   │   └── ...
│   └── ...
└── ...
```

### Registry Values

**Value types:**
- **REG_SZ** - Text string
- **REG_DWORD** - 32-bit number
- **REG_QWORD** - 64-bit number
- **REG_BINARY** - Binary data
- **REG_MULTI_SZ** - Multiple strings

**Example:**
```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
Value: ProductName = "Windows Server 2019"
Type: REG_SZ
```

### Registry Editing Caution

**Warning:**
Modifying registry can completely break Windows. Always:
1. Backup registry first
2. Know exactly what you're changing
3. Test on non-critical system first

**Backup registry:**
```
Regedit.exe → File → Export → Save registry file
If something breaks, File → Import to restore
```

---

## Task 5: User Account Control (UAC)

### UAC Overview

UAC is a security feature preventing programs from making system changes without permission.

**How it works:**
1. Program requests admin-level access
2. UAC prompt appears
3. User must approve (or enter admin password)
4. Only then can program modify system

**Why it exists:**
Malware wants system-level access. UAC forces the user to confirm system changes, preventing silent malware installation.

### UAC Settings

**Notification levels:**

1. **Never notify** (least secure)
   - No prompts at all
   - Any program can modify system
   - Danger: Malware runs silently

2. **Notify when apps make changes** (default)
   - Prompt when programs modify system
   - Doesn't prompt for Settings app changes
   - Balance of security and usability

3. **Always notify** (most secure)
   - Prompt for any system change
   - Even changing date/time triggers prompt
   - Very annoying but maximally secure

4. **Never notify + disable UAC** (dangerous)
   - Complete UAC off
   - Not recommended (essentially running as admin always)

### Admin Approval Mode

**What is Admin Approval Mode?**
Even Administrator accounts get UAC prompts. When enabled:
- Admin programs must still be approved
- Prevents admin from accidental system damage
- Prevents malware from abusing admin account

**Without Admin Approval Mode:**
- Admin account = no UAC prompts = can accidentally break system = danger

**Best practice:**
Keep Admin Approval Mode on. Even admins benefit from confirmation prompts.

---

## Task 6: Computer Management Deep Dive

### Services in Detail

**Critical services (don't disable):**
- Networking - TCP/IP, network connectivity
- Remote Procedure Call (RPC) - Core Windows function
- Windows Update - Security patches
- Event Log - System logging
- Task Scheduler - Scheduled tasks

**Optional services (safe to disable):**
- Print Spooler - If no printers
- Windows Media Player Network Sharing Service - If not used
- Bluetooth Support Service - If no Bluetooth devices
- Xbox Live Gaming Service - If not gaming

**Stopping a service:**
1. Computer Management → Services
2. Right-click service → Stop
3. Service stops immediately (doesn't restart until next boot)

**Disabling a service:**
1. Right-click → Properties
2. Startup type → Disabled
3. Won't start at next boot

### Device Manager

**What is Device Manager?**
Shows all hardware connected: graphics card, network adapter, printer, USB devices, etc.

**Common uses:**
- Update drivers (right-click device → Update driver)
- Disable hardware (right-click → Disable)
- Remove device (right-click → Uninstall)
- Check for errors (yellow ! icon = problem)

**Yellow exclamation mark:**
Means driver is missing or broken. Update the driver.

---

## Task 7: Resource Monitor & Performance Monitor

### Resource Monitor (resmon)

**What is it?**
Real-time view of system resources: CPU, Memory, Disk, Network.

**Tabs:**
- **CPU** - Process CPU usage
- **Memory** - RAM usage per process
- **Disk** - Disk I/O per process
- **Network** - Network traffic per process

**Real-world use:**
System is slow. Open Resource Monitor → Memory tab → See which process is using all RAM → End that process.

**Example:**
Browser using 8GB RAM (leak). Kill it, memory freed, system responsive again.

### Performance Monitor (perfmon)

**What is it?**
Track system metrics over time. Create graphs of CPU, Memory, Disk, Network usage.

**Use cases:**
1. Baseline - What does system look like normally?
2. Trending - Is memory usage growing over weeks?
3. Diagnostics - When did performance degrade?

**Data collector sets:**
Automatically collect data at intervals. Review patterns over time.

---

## Task 8: Windows Management Instrumentation (WMI)

### What is WMI?

**Definition:**
WMI is Windows' way of exposing system information to scripts and remote tools.

**Analogy:**
If Registry is the config database, WMI is the API to query and modify it programmatically.

### WMIC (WMI Command-line)

**What is WMIC?**
Command-line tool to query system information.

**Example queries:**
```
wmic os get caption
→ Shows Windows version

wmic computersystem get name
→ Shows computer name

wmic logicaldisk get name,size,freespace
→ Shows disk info
```

**Real-world use:**
Deploy script to 100 computers. Query all of them with WMIC to see OS version, available disk space, etc. without visiting each one.

### WMI Scripting

**PowerShell WMI queries:**
```powershell
Get-WmiObject Win32_OperatingSystem
→ Get OS info

Get-WmiObject Win32_ComputerSystem
→ Get hardware info
```

**Remote management:**
Query remote computer's WMI to see system info without logging in. Powerful for large-scale administration.

---

## Task 9: System Information

### System Information Utility (msinfo32)

**What it shows:**
- OS version and build number
- System manufacturer and model
- Processor name and speed
- Installed RAM
- System boot time
- Windows directory location

**Real-world use:**
Support ticket: "Windows won't update." Run msinfo32, check OS version. If it's Windows 7, that's why (unsupported). If Windows 10, something else.

### Environment Variables

**What are environment variables?**
Variables that programs use. Examples:
- **PATH** - Where to find executable files
- **USERPROFILE** - User's home directory
- **SystemRoot** - Where Windows is installed (usually C:\Windows)
- **TEMP** - Temporary file location

**Viewing:**
System Information → Environment Variables → See all variables and their values

**Example:**
ComSpec variable points to C:\Windows\System32\cmd.exe (the command interpreter).

---

## Task 10: Resource Monitor - Detailed Analysis

### CPU Tab

**Shows:**
- Process name
- CPU percentage
- Threads (parallel tasks within process)
- Average CPU
- Maximum CPU usage

**Finding CPU hog:**
1. Open Resource Monitor → CPU tab
2. Sort by % column descending
3. See which process maxes CPU
4. Kill the process or investigate why

### Memory Tab

**Shows:**
- Process name
- Working Set (RAM currently used)
- Shareable (memory that can be shared)
- Committed (memory allocated but maybe not used)
- Private (memory unique to this process)

**Memory leak:**
Application uses more and more RAM over time. Restarting it frees memory. Fix: Update app or restart it nightly.

### Disk Tab

**Shows:**
- Process doing disk I/O
- Disk read/write rates
- I/O bytes per second
- File being accessed

**Finding disk hog:**
Disk running constantly? Resource Monitor → Disk tab → See which process is doing I/O.

### Network Tab

**Shows:**
- Application using network
- Network bytes sent/received
- Network utilization percentage
- TCP connections per app

**Finding network hog:**
Network slow? Resource Monitor → Network tab → See which app is using bandwidth.

---

## Task 11: Command-Line Administration

### Command Prompt vs PowerShell

**Command Prompt (cmd.exe):**
- Legacy command-line tool
- Simpler syntax
- Works on all Windows versions
- Good for: Basic system info, file operations

**PowerShell:**
- Modern scripting language
- Complex syntax but powerful
- Object-oriented (not just text output)
- Good for: System administration, automation, complex logic

### Common Administrative Commands

```
systeminfo          Show detailed system information
tasklist /v         List running processes
taskkill /pid 1234  Kill process by ID
sc query             List all services
sc start servicename Start a service
sc stop servicename  Stop a service
ipconfig             Show network config
ipconfig /all        Detailed network info
getmac               Show MAC address
tracert host         Trace network path
nslookup google.com  DNS lookup
dir /s               List files recursively
attrib +h file       Hide a file
```

### Remote Command Execution

**Executing commands on remote computer:**
```
wmic /node:remotecomputer process list
→ Query processes on remote computer

psexec \\remotecomputer cmd
→ Open command prompt on remote computer
```

**Sysadmin superpower:**
Manage 100 computers from your desk without visiting each one.

---

## Task 12: Registry Editor

### Registry Editor Interface

**Access Registry:**
```
Win+R → regedit → Enter
```

**Left pane:** Hive tree (folder structure)
**Right pane:** Keys and values in current location

### Navigating Registry

**Similar to file explorer:**
- Click folder icon to expand hive
- Click item to see its values
- Right-click to add/edit/delete

**Searching:**
Edit → Find → Enter search term → Finds keys and values

**Example search:**
Search for "ProductName" → Finds Windows version in registry

### Adding/Editing Values

**Create new value:**
1. Right-click empty space in right pane
2. New → Type (String, DWORD, Binary, etc.)
3. Name the value
4. Set the data

**Edit existing value:**
1. Double-click value
2. Modify the data
3. Click OK

**Delete value:**
1. Right-click value
2. Delete
3. Confirm

### Backup & Restore

**Backup registry:**
```
File → Export → Give file name → Save
```

**Restore registry:**
```
File → Import → Select backup file → Confirm
```

**Sysadmin rule:**
Always backup before editing registry. One typo can break Windows.

---

## Command Cheatsheet (Quick Reference)

### System Information
```
systeminfo             Full system info
msinfo32               System Information GUI
wmic os get caption    Windows version
hostname               Computer name
```

### Services
```
sc query               List all services
sc query <name>       Query specific service
sc start <name>       Start service
sc stop <name>        Stop service
tasklist /svc         Processes and services
```

### Network
```
ipconfig               Basic network config
ipconfig /all          Detailed config
ipconfig /release      Release IP address
ipconfig /renew        Request new IP address
nslookup <host>       DNS lookup
tracert <host>        Trace network path
```

### Processes
```
tasklist               List running processes
tasklist /v           Detailed process list
taskkill /pid 1234    Kill by process ID
taskkill /im app.exe  Kill by app name
```

### Registry
```
regedit                Registry Editor GUI
reg query HKLM\...    Query registry from CLI
reg add HKLM\...      Add registry value from CLI
reg delete HKLM\...   Delete registry value from CLI
```

### Administrative Tools
```
taskmgr                Task Manager
devmgmt.msc           Device Manager
diskmgmt.msc          Disk Management
services.msc          Services
compmgmt.msc          Computer Management
eventvwr.msc          Event Viewer
perfmon                Performance Monitor
resmon                 Resource Monitor
msconfig               System Configuration
```

---

## Summary: Windows Administration Foundation

After Room 2, you understand:
1. How services work and how to manage them
2. How to schedule automated tasks
3. How to monitor system performance
4. How to access and use Event Viewer for troubleshooting
5. How to use Registry Editor (carefully)
6. How to manage hardware with Device Manager
7. How to use command-line for administration
8. How to understand system crashes via crash dumps
9. How to script and automate with WMI/PowerShell
10. How to optimize system performance

**You're now ready for:** Windows Server administration, Active Directory, system deployment, IT support roles.
