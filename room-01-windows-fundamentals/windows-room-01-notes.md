# TryHackMe Windows Fundamentals - Room 1: Detailed Notes

Comprehensive explanations of Windows system administration concepts covered in Room 1.

---

## Task 1: The Desktop

The Windows desktop is your starting point. Everything on screen—taskbar, icons, background—is part of the desktop environment.

### Desktop Components

**Desktop (main area):**
- The large background area where you see icons and windows
- Shows your wallpaper/background image
- Where windows open and files display

**Taskbar (bottom of screen):**
- Shows running applications
- Contains Start menu (left)
- Shows system tray icons (right, clock/network/volume)
- Quick Launch area for frequently used apps
- Shows open applications as buttons

**System Tray / Notification Area (right side of taskbar):**
- Clock showing current time
- Network status indicator
- Volume control
- Battery indicator (laptops)
- Other system application icons
- Hidden icons (overflow) accessible via arrow

**Start Menu (left side of taskbar):**
- Opens when you click Windows logo
- Shows installed applications
- Shows recent files
- Access to Settings, Control Panel, Shutdown options

### Desktop Customization

**Wallpaper/Background:**
- Right-click desktop → Personalize
- Or: Settings → Personalization → Background
- Choose from built-in images or upload your own

**Display Settings:**
- Right-click desktop → Display settings
- Adjust resolution (pixels displayed)
- Change refresh rate (screen updates)
- Scaling (text size)
- Orientation (portrait/landscape)

**Icons on Desktop:**
- Right-click → New → Shortcut to create app shortcuts
- Right-click → Sort by to organize
- Delete icons you don't use

### Why Desktop Organization Matters for Sysadmins

Users see the desktop first. As a sysadmin you might:
- Deploy wallpapers company-wide (using Group Policy)
- Restrict what users can change (via policies)
- Troubleshoot display issues (resolution, drivers)

---

## Task 2: Start Menu & Personalization

The Start menu is your gateway to everything on Windows.

### Accessing Start Menu

Click Windows logo (bottom left) or press `Win` key.

### Start Menu Organization

**Top section - Quick Access:**
- Recently opened apps
- Frequently used items
- Pinned shortcuts

**App List:**
- All installed applications
- Organized alphabetically
- Search box to find apps

**Tiles (Windows 10/11 modern view):**
- Live tiles show app updates
- Can be pinned/unpinned
- Can be organized into groups

**Bottom of Start menu:**
- Settings shortcut
- Power options (Shutdown, Restart, Sleep)
- User profile menu

### Pinning Applications

**To pin to Start menu:**
1. Right-click app → Pin to Start
2. App appears as tile in Start menu

**To unpin:**
1. Right-click tile → Unpin from Start

This keeps frequently used apps easily accessible.

### Personalization Settings

**Start Menu appearance:**
- Settings → Personalization → Start
- Show/hide recommendations
- Show recently opened items
- Full screen Start menu toggle

**App tiles organization:**
- Drag tiles to reorder
- Right-click tile to resize (small/large)
- Create groups by dragging tile to edge

### Why This Matters for Sysadmins

- Control which apps users see (remove distracting apps)
- Pin important tools to Start (Deploy standardized setup)
- Customize for different departments (Sales team gets Sales apps)
- Organize user environment for efficiency

---

## Task 3: Taskbar & Notification Area

The taskbar shows your active work and quick access to system tools.

### Taskbar Buttons

**Application buttons:**
- Click running app → brings to front
- Click again → minimizes it
- Right-click → close option
- Multiple windows of same app group together

**Quick Access buttons:**
- Pinned apps at left of taskbar
- Right-click app icon → Pin to taskbar
- Faster access than searching Start menu

### Notification Area (System Tray)

**Always visible:**
- Clock (click to see calendar)
- Network status (connected/disconnected)
- Volume control
- Battery (laptops)

**Hidden icons:**
- Click arrow (^) to see hidden icons
- Click icon to activate its application
- Regularly-used apps get permanent spots

**Hidden icon management:**
- Right-click taskbar → Taskbar settings
- Scroll down → Notification area
- Turn icons on/off individually

### Action Center

**Access:** Click notification icon (speech bubble) in taskbar

**Contains:**
- System notifications (updates, warnings)
- Quick action buttons (WiFi, Bluetooth, Brightness, etc.)
- Settings shortcuts

### Taskbar Customization

**Lock the taskbar:**
- Right-click taskbar → Lock the taskbar
- Prevents accidental moving/resizing

**Hide the taskbar:**
- Right-click taskbar → Taskbar settings
- Auto-hide the taskbar toggle
- Taskbar appears when you move mouse to bottom

**Position taskbar:**
- Drag taskbar to top, left, or right edge
- Or right-click → Properties → Position

### Why Taskbar Management Matters for Sysadmins

- Users get confused with too many icons → Hide unnecessary icons
- Important system tools should be visible (remind users to check updates)
- Taskbar lock prevents accidental changes (stability)
- Clean taskbar = better user experience

---

## Task 4: Introduction to Windows

### Windows Operating System Basics

**What is Windows?**
A graphical operating system that manages computer hardware and software. The OS handles files, user accounts, security, and all running applications.

### Windows Editions

**Home Edition:**
- Consumer-focused
- Single user or small home network
- Basic features (File Sharing, Backup)
- Cannot join domains (Enterprise networks)

**Pro Edition:**
- Business-focused
- Can join Active Directory domains
- Remote Desktop (control PC remotely)
- BitLocker (full disk encryption)
- Group Policy Editor (system administration)
- More expensive than Home

**Enterprise Edition:**
- Large organizations
- Advanced security and management
- Software deployment tools
- Licensing through volume purchase

**Server Edition:**
- Designed for servers, not desktops
- File/Print/Web/Email services
- Active Directory (user management)
- Supports more RAM and processors
- Different licensing model

### User Accounts

**Two main types:**
1. **Microsoft Account** - Cloud-based (uses Microsoft online services)
2. **Local Account** - Computer-specific (works offline)

**Local Account Types:**
- Administrator - Full system access, can install software, change settings
- Standard User - Limited access, cannot make system changes, safer

### Why This Matters

- Microsoft accounts use OneDrive cloud storage
- Local accounts are more private (no cloud sync)
- Administrators can do anything (dangerous if compromised)
- Standard users are safer (malware has limited access)
- Sysadmins typically use admin accounts with care

---

## Task 5: The File System

### Windows File Hierarchy

**Root directory: C:\ (or D:, E:, etc. for other drives)**

```
C:\
├── Users\ - User profile folders
│   ├── Username\ - Individual user folder
│   │   ├── Desktop\ - User's desktop files
│   │   ├── Documents\ - User's documents
│   │   ├── Downloads\ - Downloaded files
│   │   └── AppData\ - Application settings (hidden)
├── Program Files\ - 64-bit applications
├── Program Files (x86)\ - 32-bit applications
├── Windows\ - Operating system files
│   ├── System32\ - System binaries
│   ├── SysWOW64\ - 32-bit system files
│   └── Drivers\ - Device drivers
├── Temp\ - Temporary files
└── ProgramData\ - Application data (shared)
```

### Key Directories Explained

**Users folder:**
- Contains separate folders for each user
- Each user has their own Documents, Downloads, Desktop
- Users cannot access each other's files (permissions prevent it)

**Program Files:**
- Default location for installed applications
- 64-bit apps go in "Program Files"
- 32-bit apps go in "Program Files (x86)"

**Windows folder:**
- System core files (don't delete or modify!)
- System32 contains system libraries and utilities
- SysWOW64 allows 32-bit apps to run on 64-bit Windows

**AppData (hidden):**
- Application settings stored per user
- Roaming, Local, LocalLow subfolders
- Hidden by default (enable via View → Hidden items)

### File Extensions & Types

**Common file types:**
- `.exe` - Executable program
- `.txt` - Text file
- `.pdf` - PDF document
- `.jpg`, `.png` - Images
- `.mp4`, `.avi` - Videos
- `.docx`, `.xlsx` - Microsoft Office
- `.zip` - Compressed archive
- `.dll` - Library file (system)

### Hidden Files

Some files are hidden by default (system files, configuration files).

**To see hidden files:**
1. Open File Explorer
2. Click View → Options → Change folder and search options
3. Click View tab
4. Check "Show hidden files, folders, and drives"

**Why hidden?** Protects important system files from accidental deletion.

### File Organization Best Practices

- Store work documents in Documents folder
- Downloads folder for downloaded files
- Create subfolders for projects
- Don't store files on Desktop (cluttered, slower)
- Regular backups of important files

---

## Task 6: File Permissions & Properties

### Understanding NTFS Permissions

Windows uses NTFS (New Technology File System) to control access to files and folders. Permissions define who can do what.

### Permission Types

**Basic Permissions:**
- **Read (R)** - Can open and view file contents
- **Write (W)** - Can modify (create, edit, delete) file
- **Execute (X)** - Can run executable files
- **Modify** - Can change contents but not permissions or ownership
- **Full Control** - Complete access (change permissions, ownership, delete)

**Permission Levels:**
- **Allow** - Grant permission
- **Deny** - Block permission (overrides Allow)

### How Permissions Work

Permissions are assigned to:
- Specific users
- Groups (collection of users)
- SYSTEM (operating system itself)
- Administrators group

**Example permission structure:**
```
File: C:\Users\John\Documents\Report.docx

John (creator): Full Control
Administrators: Full Control
SYSTEM: Full Control
Everyone: No access (Deny)
```

Result: Only John and Administrators can access the file.

### Checking File Permissions

1. Right-click file → Properties
2. Click "Security" tab
3. See list of users/groups with access
4. Click "Edit" to change permissions
5. Click "Advanced" for inheritance details

### Permission Inheritance

**Inheritance = Child files inherit parent folder permissions**

Example:
- Folder C:\Shared has permission: Users = Read
- Any file created inside inherits Users = Read permission
- Saves time (don't set each file individually)

**Exception:** You can disable inheritance if a specific file needs different permissions.

### Principle of Least Privilege

Grant minimum permissions needed:
- Users need to read files? Grant Read only
- Need to modify? Grant Modify
- Don't grant Full Control unless necessary

This prevents accidental deletion or unauthorized access.

### Why Permissions Matter for Sysadmins

- Share folders securely (Read-only access for some users)
- Protect payroll files (Accountants only)
- Prevent users deleting system files (Deny write to Windows folder)
- Troubleshoot "access denied" errors (check Security tab)

---

## Task 7: The Windows Directory & System Directories

### Critical System Folders

**C:\Windows** - Core operating system
- Cannot delete or rename this folder
- Don't modify files unless you know exactly what you're doing

**C:\Windows\System32** - System 64-bit binaries
- Contains .exe and .dll files for operating system
- Examples: cmd.exe (command prompt), notepad.exe
- Critical to Windows operation

**C:\Windows\SysWOW64** - System 32-bit binaries
- Compatibility layer for 32-bit applications
- Allows old 32-bit programs to run on 64-bit Windows
- Named "WOW64" = "Windows 32 on Windows 64"

**C:\Windows\Drivers** - Device drivers
- Software that controls hardware (printer, graphics card, network)
- Windows stores driver files here

**C:\Windows\Temp** - Temporary files
- Applications store temporary data
- Safe to delete (but running programs may fail)
- Accumulates over time (can free up disk space)

**C:\ProgramData** - Shared application data
- Applications store configuration files
- Shared across all users
- Not user-specific

### Why You Need to Know This

**Troubleshooting:**
- Can't print? Driver might be in C:\Windows\Drivers
- Strange file appearing? Check C:\Windows\Temp
- Application won't start? System file corruption might be in C:\Windows\System32

**Cleanup:**
- Old temp files accumulate → Free disk space
- Disk cleanup utility safely deletes temp files
- Don't manually delete from C:\Windows\System32 (could break OS)

**Malware detection:**
- Unusual files in C:\Windows directories = suspicious
- Legitimate programs shouldn't be modifying system files

---

## Task 8: User Accounts & Administration

### Local User Accounts

User accounts control:
- Who can log in
- What they can access
- What permissions they have

### Account Types

**Administrator Account:**
- Full system access
- Can install/remove software
- Can change system settings
- Can create/delete other accounts
- Can change other users' passwords

**Standard User Account:**
- Limited access
- Cannot install software (needs admin approval)
- Cannot change system-wide settings
- Cannot create other accounts
- Safer (malware has limited damage)

### Creating a User Account

1. Settings → Accounts → Other people
2. Click "Add account"
3. Enter email or username
4. Choose account type (Administrator vs Standard)
5. Click Next

### Account Properties

**To modify account:**
1. Settings → Accounts → Other people
2. Click account → Change account type
3. Change from Administrator to Standard or vice versa

**Changing password:**
1. Settings → Accounts → Your info
2. Click "Change your password"

### Why Account Types Matter for Sysadmins

- Users should use Standard accounts daily (safer)
- Only use Administrator when installing software
- Prevent user from breaking system by accident
- Isolate user profiles (one user's settings don't affect others)
- Create separate accounts for different roles

### Guest Account

- Temporary access (doesn't require password)
- Very limited permissions
- Use for visitors who need temporary access
- Disabled by default

---

## Task 9: User Account Control (UAC)

### What is UAC?

User Account Control is a Windows security feature that prompts you when a program or action needs administrator-level access. It's a checkpoint preventing unauthorized system changes.

### How UAC Works

**Standard User runs program:**
1. Program requests administrator access
2. UAC prompt appears asking for administrator password
3. User enters admin password
4. Program runs with admin privileges

**Administrator account runs program:**
1. Program requests administrator access
2. UAC prompt asks "Allow this app to make changes?"
3. User clicks "Yes"
4. Program runs with admin privileges

### UAC Prompt Types

**Consent prompt (Administrator):**
- "Do you want to allow this app to make changes?"
- Click Yes/No
- No password needed

**Credential prompt (Standard User):**
- "Enter administrator password"
- Requires actual admin account password
- Standard user cannot bypass this

### UAC Configuration Levels

**Never notify (least secure):**
- No prompts at all
- Any program can make system changes
- Dangerous (malware runs without warning)

**Notify only when programs make changes:**
- Default level
- Prompts when programs modify system
- Doesn't prompt for Settings changes

**Notify for all changes (most secure):**
- Prompts for any system change
- Even changing date/time triggers prompt
- More annoying but more secure

**Never (disabled):**
- UAC completely off
- Not recommended

### Why UAC Matters

**Good:**
- Prevents accidental system changes
- Blocks malware from silently modifying Windows
- Makes administrator actions intentional

**Annoying:**
- Constant prompts slow workflow
- Some legacy software incompatible

### Best Practice

Keep UAC at default level. The prompts protect your system.

---

## Task 10: Settings & the Control Panel

### Settings App (Modern Windows)

Modern Windows (10/11) organizes configuration in the Settings app.

**Common Settings categories:**
- **System** - Display, Storage, About, Power settings
- **Devices** - Printers, Bluetooth, USB devices
- **Network & Internet** - WiFi, Ethernet, VPN
- **Personalization** - Background, Colors, Fonts, Themes
- **Apps** - Installed apps, Startup programs
- **Accounts** - Password, Account settings, Sign-in options
- **Time & Language** - Date/time, Regional format, Language
- **Gaming** - Xbox settings, Game mode
- **Accessibility** - High contrast, Text size, Voice control

**Access Settings:**
- Click Settings icon in taskbar
- Or: `Win+I` keyboard shortcut
- Or: Start menu → Settings icon

### Control Panel (Legacy)

Older interface still available for advanced settings.

**Still use for:**
- Advanced network settings
- Hardware management
- Legacy application settings
- Administrative tools

**Access Control Panel:**
- Windows search → "Control Panel"
- Or: Settings → Related settings link (takes to Control Panel)

### Administrative Tools

**What are they?**
Advanced system management tools for sysadmins.

**Common administrative tools:**
- Device Manager - Manage hardware and drivers
- Services - Control running background services
- Task Scheduler - Schedule automated tasks
- Event Viewer - View system logs
- Performance Monitor - Monitor system performance
- Disk Management - Manage disk partitions

**Access Administrative Tools:**
- Windows search → "Administrative Tools"
- Control Panel → Administrative Tools
- Computer Management (combines many tools)

### Why This Matters

- Users use Settings for basic configuration
- Sysadmins use Control Panel and Admin Tools
- Know where settings are located (fast troubleshooting)
- Different tools for different tasks (Device Manager for drivers, Services for background tasks)

---

## Task 11: Network Settings & Personalization

### Network Settings

**Network & Internet settings include:**
- WiFi status and available networks
- Ethernet connection details
- VPN setup
- Mobile hotspot
- Data usage
- Proxy settings

**Access:**
- Settings → Network & Internet
- Or: Right-click network icon in taskbar → Network settings

### Network Adapter Configuration

**Advanced network settings:**
- Settings → Network → Advanced network options
- Change adapter options (Ethernet, WiFi, VPN)
- Network diagnostics

**Change adapter options shows:**
- All network connections
- Ethernet (wired)
- WiFi (wireless)
- VPN tunnels

### Troubleshooting Network Issues

1. Check Network settings → Status
2. If disconnected, click "Troubleshoot" button
3. Windows runs network diagnostic
4. Shows errors and fixes if available

### Why Network Settings Matter

- Users can't connect? Check Network settings first
- VPN configuration for remote access
- Proxy settings for corporate networks
- Network diagnostics help identify connectivity problems

### Personalization Settings

**Appearance customization:**
- Background - Wallpaper image
- Colors - Accent colors, light/dark mode
- Lock screen - Image and notifications
- Fonts - Text style and size
- Themes - Complete color and style sets
- Start menu - App tiles, layout

**Access:**
- Settings → Personalization
- Or: Right-click desktop → Personalize

### Why Personalization Matters for Sysadmins

- Deploy company branding company-wide (via Group Policy)
- Standardize appearance across organization
- Accessibility settings (high contrast, large text) for users with vision/hearing issues
- Dark mode for comfortable evening work

---

## Task 12: Task Manager

### Accessing Task Manager

**Multiple methods:**
- `Ctrl+Shift+Esc` (fastest)
- `Ctrl+Alt+Delete` → Task Manager
- Right-click taskbar → Task Manager
- Windows search → "Task Manager"

### Tabs Overview

**Processes tab (default):**
- Shows all running applications
- CPU usage percentage
- Memory (RAM) usage
- Disk I/O activity
- Network usage

**Performance tab:**
- Overall system performance
- CPU usage over time (graph)
- Memory usage trend
- Disk activity
- Network usage
- GPU usage (if available)

**App history tab:**
- Which apps use most resources
- CPU, memory, network usage over time
- Helpful for identifying resource hogs

**Startup tab:**
- Programs that launch at Windows startup
- Slow down boot time if too many
- Disable unnecessary startup apps

**Services tab:**
- Background Windows services
- Advanced (for sysadmins)
- Stop/start critical services

**Details tab:**
- Detailed process information
- Process ID (PID)
- Memory usage
- Priority level
- Path to executable

**Users tab:**
- Logged-in users
- Resources used by each user

### Using Task Manager for Diagnostics

**High CPU usage?**
1. Open Task Manager → Processes
2. Click CPU column to sort
3. See which program uses most CPU
4. Right-click problematic app → End task (closes it)

**System running slow?**
1. Check Performance tab
2. Look for red/orange usage spikes
3. Identify bottleneck (CPU, Memory, Disk, Network)

**Program unresponsive?**
1. Find program in Processes tab
2. Right-click → End task
3. Program closes (may lose unsaved work)

**Too many startup programs?**
1. Click Startup tab
2. Right-click unnecessary program → Disable
3. Won't launch at next boot

### Why Task Manager is Critical

- **Diagnose performance issues** - Identify resource bottlenecks
- **Kill frozen programs** - Faster than restarting
- **Monitor system health** - See real-time CPU, memory usage
- **Manage startup** - Faster boot by disabling unnecessary programs
- **Find malware** - Unusual processes might be malware

---

## Windows vs Linux Administration

| Task | Windows | Linux |
|------|---------|-------|
| Change permissions | Security tab (GUI) | `chmod` (command) |
| Manage users | Settings/Control Panel | `useradd`, `usermod` |
| Monitor processes | Task Manager (GUI) | `ps aux`, `top` (command) |
| View logs | Event Viewer | `/var/log` files, commands |
| Configure network | Settings GUI | `/etc/network/` files |
| Install software | Settings GUI or installer | `apt install` (command) |

**Key difference:** Windows emphasizes GUI tools, Linux emphasizes command-line tools. Both achieve the same administrative goals.

---

## Summary: Windows System Administration Foundation

After Room 1, you understand:
1. Windows desktop environment and navigation
2. File system hierarchy (C:\Users, Program Files, Windows, etc.)
3. NTFS permissions and access control
4. User accounts and administrator privileges
5. System security (UAC, permission inheritance)
6. Network configuration basics
7. System monitoring (Task Manager, Settings)

**These foundations prepare you for:**
- Windows Server administration
- Active Directory user/computer management
- System troubleshooting and diagnostics
- User support and IT operations
