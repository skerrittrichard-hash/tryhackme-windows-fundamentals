# TryHackMe Windows Fundamentals - Room 1: Complete

## Room Overview

**TryHackMe Room:** Windows Fundamentals  
**Status:** ✅ Complete - All quiz questions answered  
**Duration:** ~60 minutes (lab) + hands-on practice  
**Difficulty:** Beginner to Intermediate  
**Hands-On Labs:** Yes (interactive system exploration)

## What This Room Covers

Windows Fundamentals introduces the Windows operating system from a sysadmin perspective. Unlike many introductory courses focused on user navigation, this room covers system administration concepts including file system architecture, permissions, user accounts, and administrative tools—skills directly applicable to IT operations and system management roles.

### Topics Covered

1. **The Desktop**
   - Desktop layout and components
   - Taskbar and Quick Launch
   - System tray (notification area)
   - Icons and shortcuts
   - Start menu basics
   - Display settings and wallpaper
   - Visual customization options

2. **Start Menu & Personalization**
   - Accessing and organizing Start menu
   - Pinning applications
   - Windows app tiles
   - Recently used applications
   - Personalization settings (background, colors, themes)
   - Quick access to frequently used items
   - Customizing app display

3. **Taskbar & Notification Area**
   - Pinning applications to taskbar
   - Notification area icons (system tray)
   - Hidden icons and overflow
   - Clock, network, and volume controls
   - Action Center access
   - System settings access
   - Customizing taskbar behavior

4. **Introduction to Windows**
   - Windows operating system fundamentals
   - Windows versions and editions (Home, Pro, Enterprise)
   - User accounts and authentication
   - Password management basics
   - Command-line tools (WMIC, PowerShell basics)
   - System information access

5. **The File System**
   - Windows file hierarchy (C:, Program Files, Users, etc.)
   - User profile structure
   - Desktop, Documents, Downloads folders
   - File extensions and types
   - File organization best practices
   - User-specific vs system-level files

6. **File Permissions & Properties**
   - File properties dialog
   - Security tab and permissions
   - NTFS permissions (Read, Write, Modify, Execute)
   - File ownership and access control
   - Permission inheritance
   - Effective permissions calculation
   - Advanced security settings

7. **The Windows Directory & System Directories**
   - Windows system directory structure
   - System32 and SysWOW64 (32-bit vs 64-bit)
   - Program Files organization
   - Driver storage
   - Temporary files and cache
   - System configuration files
   - Critical system folders

8. **User Accounts & Administration**
   - Local user accounts
   - Administrator vs Standard user accounts
   - Microsoft accounts vs local accounts
   - Creating and managing user accounts
   - Account properties and settings
   - User groups and permissions
   - Guest accounts

9. **User Account Control (UAC)**
   - UAC prompts and elevation
   - Consent vs credential prompts
   - UAC settings and configuration
   - Running programs with elevated privileges
   - Administrator access control
   - Security implications of UAC
   - UAC configuration levels

10. **Settings & the Control Panel**
    - Settings app organization
    - Control Panel access and navigation
    - System, Display, Storage categories
    - Network & Internet settings
    - Accounts and user management
    - Device management
    - Administrative tools access
    - Legacy Control Panel vs modern Settings

11. **Network Settings & Personalization**
    - Network status and connectivity
    - Network adapter configuration
    - Change adapter options
    - Network diagnostics
    - Background personalization
    - Wallpaper and color customization
    - Theme and appearance settings

12. **Task Manager**
    - Accessing Task Manager (Ctrl+Shift+Esc)
    - Processes tab (running applications)
    - Performance tab (CPU, memory, disk monitoring)
    - App history and startup tabs
    - Services tab
    - Process monitoring and termination
    - Resource utilization tracking
    - System performance diagnostics

## Sysadmin Relevance

**Why These Skills Matter for Your Target Role:**

| Skill | Sysadmin Use |
|-------|--------------|
| File permissions | Securing user data, implementing access controls |
| User account management | Creating accounts, managing access rights |
| File system hierarchy | Locating config files, understanding folder structure |
| System directories | Knowing where drivers, apps, system files live |
| Task Manager | Monitoring processes, diagnosing performance issues |
| Control Panel/Settings | Managing system configuration, troubleshooting |
| UAC | Understanding privilege elevation, security controls |
| Network settings | Configuring network adapters, diagnostics |

**Real-World Scenarios:**
- Troubleshoot why a user can't access a file: Check file permissions (Security tab)
- New employee setup: Create user account, set folder permissions
- Application won't start: Check Task Manager for errors, monitor resources
- Performance issues: Use Task Manager Performance tab to identify bottlenecks
- Network problems: Use Network settings to check adapter status
- Software deployment: Navigate Program Files, manage user profiles

## Lab Completion Evidence

✅ **All Quiz Questions Answered Correctly**

### Task Breakdown

**Task 1: The Desktop**
- ✅ Desktop components and layout
- ✅ Taskbar and notification area
- ✅ Start menu basics

**Task 2: Start Menu & Personalization**
- ✅ Start menu organization
- ✅ App pinning and customization
- ✅ Personalization settings

**Task 3: Taskbar & Notification Area**
- ✅ Taskbar customization
- ✅ Notification area icons
- ✅ System tray management

**Task 4: Introduction to Windows**
- ✅ Windows OS fundamentals
- ✅ User accounts and authentication
- ✅ Basic system tools

**Task 5: The File System**
- ✅ Windows file hierarchy
- ✅ User profile structure
- ✅ File organization

**Task 6: File Permissions & Properties**
- ✅ NTFS permissions
- ✅ File ownership
- ✅ Permission inheritance

**Task 7: The Windows Directory & System Directories**
- ✅ System32 and directory structure
- ✅ Program Files organization
- ✅ System file locations

**Task 8: User Accounts & Administration**
- ✅ Creating user accounts
- ✅ Account types and properties
- ✅ Account management

**Task 9: User Account Control (UAC)**
- ✅ UAC prompts and elevation
- ✅ UAC configuration
- ✅ Privilege management

**Task 10: Settings & the Control Panel**
- ✅ Settings app navigation
- ✅ Control Panel access
- ✅ System configuration

**Task 11: Network Settings & Personalization**
- ✅ Network configuration
- ✅ Adapter settings
- ✅ Personalization options

**Task 12: Task Manager**
- ✅ Process monitoring
- ✅ Performance tracking
- ✅ Application management

## Key Windows Concepts & Navigation

### File System Hierarchy

```
C:\ (Root)
├── Users\ (User profiles)
│   ├── Username\
│   │   ├── Desktop
│   │   ├── Documents
│   │   ├── Downloads
│   │   └── AppData (hidden by default)
├── Program Files\ (64-bit applications)
├── Program Files (x86)\ (32-bit applications)
├── Windows\ (System files)
│   ├── System32\ (System binaries)
│   ├── SysWOW64\ (32-bit system files)
│   └── Drivers\ (Device drivers)
└── Temp\ (Temporary files)
```

### File Permissions (NTFS)

**Basic Permissions:**
- **Read (R)** - Can view file/folder contents
- **Write (W)** - Can modify file/folder
- **Execute (X)** - Can run executable files
- **Modify (M)** - Can change contents
- **Full Control (F)** - All permissions

**Permission Levels:**
- **Creator Owner** - User who created the file
- **Administrators** - Full system access
- **SYSTEM** - System account (highest privilege)
- **Users** - Standard user group
- **Everyone** - All accounts on system

**How to Check Permissions:**
1. Right-click file/folder → Properties
2. Click "Security" tab
3. Select user/group → Click "Edit" to see permissions
4. Click "Advanced" for detailed, inherited permissions

### User Account Types

| Type | Permissions | Use Case |
|------|-------------|----------|
| Administrator | Full system access | IT staff, system administration |
| Standard User | Limited permissions | Regular users, security best practice |
| Guest | Minimal access | Temporary visitors |

### System Tools Access

**Task Manager:**
- `Ctrl+Shift+Esc` (fastest method)
- `Ctrl+Alt+Delete` → Task Manager
- Right-click taskbar → Task Manager
- Windows search → "Task Manager"

**Settings:**
- Start menu → Settings icon
- `Win+I` keyboard shortcut
- Right-click Start → Settings

**Control Panel:**
- Windows search → "Control Panel"
- Settings → Scroll down → "Related settings" link
- Administrative Tools (for advanced settings)

**Device Manager:**
- Settings → Device manager
- Or: Windows search → "Device Manager"

## Learning Experience

**What Worked Well:**
- Practical exploration of actual Windows system
- UI-based approach (no command line required for basic tasks)
- Real-world concepts (permissions, user management)
- Hands-on file system and settings navigation
- Preparation for Windows Server (applies similar concepts)

**Key Insights:**
1. **Permissions are foundational** - Like Linux, Windows file permissions control access. NTFS permissions (Read, Write, Modify) are security controls.
2. **File system hierarchy matters** - Knowing that drivers are in \Windows\Drivers and apps in Program Files helps troubleshooting.
3. **Task Manager is your diagnostic tool** - Performance issues? Check Task Manager first. It shows what's consuming resources.
4. **UAC is a security feature** - Admin prompts aren't annoyances; they prevent unauthorized system changes.
5. **User accounts control access** - Creating accounts with proper permissions is core sysadmin work.

**How This Fits Your Career Path:**
- **Job interviews:** Expect questions on NTFS permissions, user account management, Task Manager usage
- **Day 1 on job:** You'll manage user accounts, troubleshoot permissions, monitor system performance
- **Daily tools:** Task Manager, Settings, file permissions are used constantly
- **Windows Server foundation:** Everything here applies to Server administration (just on a larger scale)

## Comparison to Linux Fundamentals

| Concept | Linux | Windows |
|---------|-------|---------|
| **File permissions** | chmod (symbolic/numeric) | NTFS Security tab (GUI) |
| **User management** | useradd, usermod commands | User Accounts settings |
| **System diagnostics** | ps aux, top commands | Task Manager GUI |
| **Configuration** | Edit text files | Settings app |
| **File hierarchy** | /home, /etc, /var | Users, Program Files, Windows |
| **Privilege elevation** | sudo | UAC prompts |

**Key difference:** Windows emphasizes GUI administration while Linux emphasizes command-line. Both achieve the same goals (manage files, permissions, users, monitor systems) through different interfaces.

## Security+ Alignment

Room 1 supports Security+ in:
- **Access Control:** NTFS permissions as file-level RBAC (Role-Based Access Control)
- **Privilege Management:** UAC as elevation control, Admin vs Standard user separation
- **Principle of Least Privilege:** Creating Standard user accounts instead of always using Admin
- **Configuration Hardening:** Secure file permissions, proper user separation
- **Defense-in-Depth:** File permissions + User accounts + UAC = layered access control

**Exam connections:**
- File permissions are Detective controls (identify who accessed what)
- User account restrictions are Preventive controls (prevent unauthorized access)
- UAC is a Control limiting privilege escalation

## Portfolio Relevance

**Why Document Windows Fundamentals?**
1. **Rounds out portfolio:** Linux + Windows + Cloud (Azure) = full sysadmin coverage
2. **Demonstrates Windows knowledge:** Many junior roles require Windows system administration
3. **Shows progression:** Basic Windows UI → Windows Server (next level)
4. **Real-world applicable:** File permissions, user management, Task Manager are daily work
5. **Interviewer confidence:** Shows you understand both Unix-like and Windows systems

**Recruiter Perspective:**
- "Candidate understands Windows system administration fundamentals"
- "They know how to manage user accounts and permissions"
- "They can troubleshoot using Task Manager and system tools"
- "They're prepared for hybrid IT environments (Windows + Linux)"
- "Ready for Windows Server administration with training"

## Next Steps After This Room

1. **Windows Fundamentals Part 2** (if available) - Advanced Windows concepts
2. **Windows Server basics** - Apply these concepts to server operating system
3. **Active Directory fundamentals** - User and computer management at scale
4. **Group Policy** - Centralized configuration management
5. **Penetration testing on Windows** - Finding vulnerabilities in Windows systems

---

**Completed:** February 2026  
**Room Link:** https://tryhackme.com/room/windowsfundamentals1  
**Time Investment:** ~60 minutes  
**Skill Level After:** Beginner-Intermediate Windows user  
**Next Room:** Windows Fundamentals Part 2 (or Windows Server)

**Repository:** tryhackme-windows-fundamentals  
**Structure:** room-01-README.md, room-01-notes.md, room-01-commands-cheatsheet.md, room-01-screenshots/, LEARNING-LOG.md

---

**Windows Fundamentals Room 1 complete. Comprehensive Windows system administration foundation established.**
