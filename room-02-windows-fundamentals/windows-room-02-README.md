# TryHackMe Windows Fundamentals - Room 2: Complete

## Room Overview

**TryHackMe Room:** Windows Fundamentals 2  
**Status:** ✅ Complete - All quiz questions answered  
**Duration:** ~90 minutes (lab) + hands-on practice  
**Difficulty:** Intermediate  
**Hands-On Labs:** Yes (system configuration, registry editing, command-line tools)

## What This Room Covers

Windows Fundamentals 2 builds on Room 1 fundamentals and dives deeper into Windows system administration. This room covers the advanced tools and utilities that sysadmins use daily: System Configuration, Task Scheduler, Computer Management, Registry Editor, Resource Monitor, and command-line administration. These are not user-level features—they're the core of Windows system administration.

### Topics Covered

1. **System Configuration & Advanced System Settings**
   - System Configuration utility (msconfig)
   - Boot tab (boot options, startup settings)
   - Services tab (startup services management)
   - Startup tab (startup programs control)
   - Tools tab (quick access to administrative tools)
   - Startup and Recovery settings
   - Write Debugging Information (crash dump types)
   - Crash dump options (automatic, kernel, small, complete, none)

2. **Task Scheduler & Computer Management**
   - Task Scheduler for creating and managing scheduled tasks
   - Task triggers and conditions
   - Computer Management utility (compmgmt.msc)
   - Services management within Computer Management
   - Device Manager for hardware management
   - Event Viewer for system events
   - Disk Management for partitions
   - Managing services (start, stop, pause, resume)

3. **Advanced System Settings & Performance**
   - System Properties and Advanced settings
   - System Protection and restore points
   - Startup and Recovery configuration
   - Performance Options
   - Visual Effects customization
   - Processor scheduling
   - Virtual memory management
   - Crash dump recovery options
   - Hardware profiles

4. **Windows Registry & System Configuration**
   - Registry Editor access (regedit.exe)
   - Registry structure and hives
   - HKEY_LOCAL_MACHINE (HKLM)
   - HKEY_CURRENT_USER (HKCU)
   - HKEY_CLASSES_ROOT
   - HKEY_USERS
   - HKEY_CURRENT_CONFIG
   - Registry keys and values
   - Registry value types (DWORD, String, Binary)
   - Registry editing and backup

5. **Change UAC Settings**
   - User Account Control configuration
   - Admin Approval Mode
   - UAC notification levels
   - Secure Desktop option
   - Privilege elevation control
   - Consent vs credential prompts
   - UAC security implications

6. **Computer Management Deep Dive**
   - System Tools organization
   - Services and device management
   - Task Scheduler integration
   - Event Viewer for diagnostics
   - Performance monitoring
   - Storage and disk management
   - Application monitoring

7. **Resource Monitoring & Performance Analysis**
   - Resource Monitor (resmon)
   - Performance Monitor (perfmon)
   - Real-time resource monitoring
   - CPU, Memory, Disk, Network monitoring
   - Process-level resource tracking
   - Performance counters
   - Data collector sets
   - Historical performance data

8. **Windows Management Instrumentation (WMI)**
   - Windows Management Instrumentation basics
   - WMI Command-line (WMIC) tool
   - WMI scripting capabilities
   - System information queries
   - WMI classes and objects
   - Remote management via WMI
   - VBScript and PowerShell scripting

9. **System Information & Registry**
   - System Information utility (msinfo32)
   - Hardware resources
   - System components
   - Software environment
   - Device information
   - Registry structure basics
   - Registry hive organization

10. **Resource Monitor - Detailed Analysis**
    - Resource Monitor tabs (CPU, Memory, Disk, Network)
    - Process-level resource consumption
    - System-wide resource overview
    - Real-time performance tracking
    - Network traffic analysis
    - Disk I/O monitoring
    - Memory usage analysis

11. **Command-Line Administration Tools**
    - Command Prompt (cmd.exe)
    - PowerShell basics
    - System administration via CLI
    - Administrative commands
    - Registry command-line access
    - Service management from command line
    - Process management commands
    - System information retrieval
    - Network configuration commands

12. **Registry Editor**
    - Registry Editor interface
    - Navigation and searching
    - Value modification
    - Registry backup and restore
    - Registry data types
    - System configuration via registry
    - Application settings storage

## Sysadmin Relevance

**Why These Skills Matter for Your Target Role:**

| Skill | Sysadmin Use |
|-------|--------------|
| System Configuration (msconfig) | Manage startup services, boot options, troubleshooting |
| Task Scheduler | Automate administrative tasks, backups, maintenance |
| Computer Management | Central location for all system administration |
| Services management | Start/stop services, control what runs at boot |
| Task Manager performance | Monitor system health, troubleshoot slowness |
| Resource Monitor | Identify resource bottlenecks, problem processes |
| Event Viewer | Diagnose errors, track system events, security |
| Registry Editor | Configure system settings, troubleshoot issues |
| UAC settings | Balance security with usability |
| WMI / Command-line | Automate repetitive tasks, remote management |

**Real-World Scenarios:**
- Service won't start: Check Computer Management → Services, view error in Event Viewer
- System running slow: Open Resource Monitor, identify CPU/Memory hog process
- Need to schedule daily task: Task Scheduler → Create task → Set trigger and action
- Configure system settings: Registry Editor (when GUI unavailable)
- Automate deployment: Use WMIC or PowerShell to query/configure systems
- Troubleshoot boot issues: System Configuration → Boot tab, disable startup services
- Monitor performance: Performance Monitor for trending, Resource Monitor for real-time
- Remote management: WMI from command line to query remote systems

## Lab Completion Evidence

✅ **All Quiz Questions Answered Correctly**

### Task Breakdown

**Task 1: System Configuration & Advanced System Settings**
- ✅ Boot options and startup settings
- ✅ Services tab management
- ✅ Startup programs control
- ✅ Crash dump configuration

**Task 2: Task Scheduler & Computer Management**
- ✅ Task Scheduler creation
- ✅ Computer Management organization
- ✅ Services management
- ✅ Event Viewer access

**Task 3: Advanced System Settings & Performance**
- ✅ System Protection settings
- ✅ Startup and Recovery options
- ✅ Performance tuning
- ✅ Virtual memory management

**Task 4: Windows Registry & System Configuration**
- ✅ Registry structure understanding
- ✅ Registry hive navigation
- ✅ Configuration verification

**Task 5: Change UAC Settings**
- ✅ UAC notification levels
- ✅ Admin Approval Mode
- ✅ Privilege elevation control

**Task 6: Computer Management Deep Dive**
- ✅ System Tools overview
- ✅ Services and devices
- ✅ Performance monitoring
- ✅ Storage management

**Task 7: Resource Monitoring & Performance Analysis**
- ✅ Resource Monitor usage
- ✅ Performance Monitor
- ✅ Real-time monitoring
- ✅ Data collection

**Task 8: Windows Management Instrumentation (WMI)**
- ✅ WMI basics
- ✅ WMIC command-line tool
- ✅ System information queries
- ✅ Remote management

**Task 9: System Information & Registry**
- ✅ System Information utility
- ✅ Hardware resources
- ✅ Software environment
- ✅ Registry basics

**Task 10: Resource Monitor - Detailed Analysis**
- ✅ CPU, Memory, Disk, Network tabs
- ✅ Process-level monitoring
- ✅ Real-time tracking
- ✅ Network traffic analysis

**Task 11: Command-Line Administration Tools**
- ✅ Command Prompt usage
- ✅ PowerShell basics
- ✅ System administration CLI
- ✅ Remote command execution

**Task 12: Registry Editor**
- ✅ Registry navigation
- ✅ Value modification
- ✅ Backup and restore
- ✅ System configuration

## Key Administration Tools & Commands

### System Configuration (msconfig)
```
Win+R → msconfig → Enter
```

### Task Scheduler
```
Win+R → taskschd.msc → Enter
```

### Computer Management
```
Win+R → compmgmt.msc → Enter
```

### Services
```
Win+R → services.msc → Enter
```

### Event Viewer
```
Win+R → eventvwr.msc → Enter
```

### Task Manager
```
Ctrl+Shift+Esc
```

### Resource Monitor
```
Win+R → resmon → Enter
```

### Performance Monitor
```
Win+R → perfmon → Enter
```

### Registry Editor
```
Win+R → regedit → Enter
```

### System Information
```
Win+R → msinfo32 → Enter
```

### Device Manager
```
Win+R → devmgmt.msc → Enter
```

### Disk Management
```
Win+R → diskmgmt.msc → Enter
```

### Command Prompt
```
Win+R → cmd → Enter
```

### PowerShell
```
Win+R → powershell → Enter
```

## Learning Experience

**What Worked Well:**
- Practical exploration of critical administration tools
- Progressive difficulty (desktop → system tools → command-line)
- Real-world scenarios for each tool
- Hands-on practice with registry and configuration
- Integration of multiple tools (msconfig → Computer Management → Registry)

**Key Insights:**
1. **System Configuration is the launching pad** - msconfig provides access to many administrative tools in one place
2. **Services control what runs** - Managing services is core sysadmin work (start/stop/disable)
3. **Task Scheduler enables automation** - Scheduled tasks handle backups, cleanup, monitoring
4. **Registry is powerful but dangerous** - One wrong setting can break Windows (backup first!)
5. **Monitoring tools are essential** - Resource Monitor and Performance Monitor identify problems
6. **Command-line is faster** - Once you know the commands, CLI is quicker than GUI navigation
7. **Event Viewer is your diagnostic log** - When things fail, Event Viewer shows what went wrong

**How This Fits Your Career Path:**
- **Job interviews:** Expect questions on troubleshooting with Event Viewer, managing services, scheduling tasks
- **Day 1 on job:** You'll manage services, schedule maintenance tasks, monitor system performance
- **Daily tools:** Computer Management, Task Scheduler, Event Viewer, Resource Monitor are used constantly
- **Problem-solving:** Event Viewer first (what failed?), then Resource Monitor (why failed?), then Registry (configuration issue?)
- **Automation:** Task Scheduler + PowerShell scripts automate routine work
- **Remote management:** WMI and command-line tools work on remote systems

## Comparison: Room 1 vs Room 2

| Area | Room 1 | Room 2 |
|------|--------|--------|
| **Focus** | Desktop & file system | System administration tools |
| **Main tools** | Desktop, File Explorer, Task Manager | Msconfig, Services, Registry, Event Viewer |
| **User focus** | Individual user experience | System administrator tasks |
| **Complexity** | Beginner | Intermediate |
| **Practical use** | Daily work | Daily troubleshooting & automation |

**Progression:** Room 1 teaches you the **what** (file system, permissions). Room 2 teaches you the **how** (tools and commands to manage it).

## Security+ Alignment

Room 2 supports Security+ in:
- **Configuration Management:** Services management, startup configuration
- **Change Management:** Task Scheduler for automated deployments
- **Incident Response:** Event Viewer for forensics and troubleshooting
- **System Hardening:** Disabling unnecessary services, UAC configuration
- **Access Control:** Service accounts, privilege levels
- **Monitoring:** Resource Monitor, Performance Monitor for security baseline
- **Automation:** Task Scheduler for security scanning, log rotation

**Exam connections:**
- Services running with minimal privileges (Principle of Least Privilege)
- Event logs as Detective controls (identify what happened)
- Task Scheduler for automated security tasks
- Registry for system hardening settings

## Windows Fundamentals Series Progression

```
Room 1: Desktop & Basics (what/where)
    ↓
Room 2: System Administration Tools (how)
    ↓
Room 3: Security Features (why)
    ↓
Windows Server Administration (scale)
```

**Room 1 + Room 2 = Complete Foundation**
- Room 1 gave you the landscape (file system, permissions, users)
- Room 2 gives you the tools to manage it (services, tasks, registry, monitoring)
- Together: You can administer a Windows system

---

**Completed:** February 2026  
**Room Link:** https://tryhackme.com/room/windowsfundamentals2  
**Time Investment:** ~90 minutes  
**Skill Level After:** Intermediate Windows system administrator  
**Series Status:** 2 of 3 complete

**Repository:** tryhackme-windows-fundamentals  
**Structure:** room-02-README.md, room-02-notes.md, room-02-commands-cheatsheet.md, room-02-screenshots/, LEARNING-LOG.md (updated)

---

**Windows Fundamentals Room 2 complete. Advanced system administration tools mastered.**
