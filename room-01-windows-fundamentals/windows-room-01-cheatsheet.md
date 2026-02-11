# TryHackMe Windows Fundamentals - Room 1: Quick Reference Cheatsheet

Fast reference for navigating Windows, accessing settings, and using system tools.

---

## Keyboard Shortcuts

### System Navigation
```
Win                    Open/close Start menu
Win+I                  Open Settings
Win+E                  Open File Explorer
Win+D                  Show/hide desktop
Win+X                  Quick access menu (Settings, Device Manager, etc.)
Win+V                  Open clipboard history
Win+Shift+V            Access clipboard sharing
Alt+Tab                Switch between open apps
Alt+F4                 Close current window
Ctrl+Alt+Delete        Lock screen / Task Manager / Power options
Ctrl+Shift+Esc         Open Task Manager (fastest)
Windows+Pause/Break    System properties
```

### Task Management
```
Ctrl+Shift+Esc         Open Task Manager directly
Ctrl+Alt+Delete        Open security screen (includes Task Manager)
Ctrl+Alt+Delete → U    Lock computer
Ctrl+Alt+Delete → S    Switch user
```

### File Management
```
Ctrl+C                 Copy selected file
Ctrl+X                 Cut selected file
Ctrl+V                 Paste file
Ctrl+A                 Select all files
Delete                 Send to Recycle Bin
Shift+Delete           Permanently delete (bypass Recycle Bin)
Ctrl+Z                 Undo last action
Ctrl+Y                 Redo last action
F2                     Rename selected file
F5                     Refresh (File Explorer)
```

### Other Shortcuts
```
Win+L                  Lock Windows (go to login screen)
Win+R                  Open Run dialog (execute commands)
Win+T                  Cycle through taskbar items
Win+Number            Open app at taskbar position (Win+1, Win+2, etc.)
```

---

## Accessing Common Settings

### User & Account Settings
```
Settings → Accounts

Change password:
Settings → Accounts → Your info → Change your password

Create new user account:
Settings → Accounts → Other people → Add account

Change account type:
Settings → Accounts → Other people → Select account → Change account type
```

### Display & Appearance
```
Display settings:
Settings → System → Display
(Or: Right-click desktop → Display settings)

Personalization:
Settings → Personalization
(Or: Right-click desktop → Personalize)

Change wallpaper:
Settings → Personalization → Background

Change theme/colors:
Settings → Personalization → Colors

Text size:
Settings → System → Display → Scale and layout → Text size
```

### Network & Internet
```
WiFi settings:
Settings → Network & Internet → WiFi

Ethernet settings:
Settings → Network & Internet → Ethernet

Network status:
Settings → Network & Internet → Status
(Or: Right-click network icon → Network settings)

Advanced network options:
Settings → Network & Internet → Advanced network options
```

### File System & File Explorer
```
Open File Explorer:
Windows key + E
(Or: Click folder icon on taskbar)

Show hidden files:
File Explorer → View → Show → Hidden items

View folder properties:
Right-click folder → Properties

Check disk space:
File Explorer → C: drive → Right-click → Properties
```

### Task Manager & Performance
```
Open Task Manager:
Ctrl+Shift+Esc (fastest)
(Or: Ctrl+Alt+Delete → Task Manager)

Check processes:
Task Manager → Processes tab

Monitor performance:
Task Manager → Performance tab

Check startup programs:
Task Manager → Startup tab

End unresponsive program:
Task Manager → Processes tab → Right-click app → End task
```

### User Account Control (UAC)
```
UAC is automatic - prompts appear when needed

Change UAC level:
Settings → System → About → Device specifications
(Or: Control Panel → User Accounts → Change User Account Control settings)

Run as Administrator:
Right-click program → Run as administrator
(Or: Program properties → Advanced → Check "Run as administrator")
```

### Control Panel & Administrative Tools
```
Open Control Panel:
Windows search → "Control Panel"
(Or: Settings → scroll to bottom → Related settings link)

Administrative Tools:
Windows search → "Administrative Tools"
(Or: Control Panel → Administrative Tools)

Device Manager:
Windows search → "Device Manager"
(Or: Win+X → Device Manager)

Services:
Windows search → "Services"
(Or: Win+X → Computer Management → Services)

Event Viewer:
Windows search → "Event Viewer"
(Or: Control Panel → Administrative Tools → Event Viewer)

Task Scheduler:
Windows search → "Task Scheduler"
(Or: Control Panel → Administrative Tools → Task Scheduler)

Disk Management:
Windows search → "Disk Management"
(Or: Win+X → Disk Management)
```

---

## File Permissions (GUI Navigation)

### Check File Permissions
```
1. Right-click file/folder → Properties
2. Click "Security" tab
3. See list of users/groups with access
4. Click name → see specific permissions
```

### Change File Permissions
```
1. Right-click file/folder → Properties
2. Click "Security" tab
3. Click "Edit" button
4. Select user → Check/uncheck permissions
5. Click "Apply" then "OK"
```

### Advanced Permissions
```
1. Right-click file/folder → Properties
2. Click "Security" tab
3. Click "Advanced" button
4. View detailed permission inheritance
5. Click "Change permissions" to edit
```

### Change File Ownership
```
1. Right-click file/folder → Properties
2. Click "Security" tab
3. Click "Advanced"
4. Click "Change" next to Owner name
5. Type new owner name → Check Names → OK
```

---

## System Information & Diagnostics

### System Properties
```
View system info:
Settings → System → About
(Or: Ctrl+Pause/Break)

See Windows version:
Settings → System → About → Windows edition
(Shows version: 22H2, 21H2, etc.)

Check computer name:
Settings → System → About → Device name

See installed RAM:
Settings → System → About → Installed RAM
(Or: Task Manager → Performance → Memory)

View processor info:
Settings → System → About → Processor
```

### Disk Space & Storage
```
Check disk usage:
File Explorer → C: drive → Right-click → Properties

Free up disk space:
Settings → System → Storage
(Shows what's using disk space)
```

### Network Diagnostics
```
Check network status:
Settings → Network & Internet → Status

Run network troubleshooter:
Settings → Network & Internet → Status → Troubleshoot
(Or: Right-click network icon → Troubleshoot)

Check network adapters:
Settings → Network & Internet → Advanced network options → Network adapters
```

---

## Windows Directories Quick Reference

```
C:\Users\Username\Desktop        User's desktop files
C:\Users\Username\Documents      User's documents
C:\Users\Username\Downloads      Downloaded files
C:\Users\Username\AppData        App settings (hidden)

C:\Program Files\                64-bit applications
C:\Program Files (x86)\          32-bit applications

C:\Windows\                      Operating system files
C:\Windows\System32\             System 64-bit binaries
C:\Windows\SysWOW64\             32-bit system files
C:\Windows\Drivers\              Device drivers
C:\Windows\Temp\                 Temporary files

C:\ProgramData\                  Shared application data
C:\Temp\                         Temporary files
```

---

## File Permissions Quick Reference

### Basic Permission Levels
```
Read (R)           Can view file contents
Write (W)          Can modify file contents
Execute (X)        Can run executable files
Modify (M)         Can change and delete files
Full Control (F)   All permissions
```

### Common Permission Scenarios

**Public read-only folder:**
```
Users = Read
Administrators = Full Control
```

**Team shared folder:**
```
TeamGroup = Modify
Administrators = Full Control
Others = No access
```

**Secure personal folder:**
```
Username = Full Control
Administrators = Full Control
Everyone = Deny (explicitly blocked)
```

### Permission Inheritance
```
Folder permissions → Child files inherit
Unless inheritance is disabled
Right-click → Properties → Security → Advanced → Disable inheritance
```

---

## User Account Types

### Administrator Account
```
✓ Full system access
✓ Install/remove software
✓ Change system settings
✓ Create/delete user accounts
✓ Change other users' passwords
✗ More at risk from malware
```

### Standard User Account
```
✗ Cannot install software
✗ Cannot change system settings
✗ Cannot create accounts
✓ Safer (limited malware damage)
✓ Requires admin approval for changes
```

### Quick Change Account Type
```
Settings → Accounts → Other people → Select user → Change account type
```

---

## Task Manager Quick Guide

### Open Task Manager
```
Ctrl+Shift+Esc        Fastest method
Ctrl+Alt+Delete → Task Manager
Right-click taskbar → Task Manager
Windows search → Task Manager
```

### Tabs
```
Processes           Running applications and resource usage
Performance         CPU/Memory/Disk/Network usage over time
App history         App resource history
Startup             Programs that launch at boot
Services            Background Windows services
Details             Process details (PID, paths)
Users               Logged-in users and resources
```

### Common Actions

**End frozen program:**
```
Processes tab → Find program → Right-click → End task
```

**Check high CPU usage:**
```
Processes tab → Click CPU column to sort highest first
See which program uses most CPU
```

**Monitor memory usage:**
```
Performance tab → Memory → See usage graph and total
```

**Disable slow startup programs:**
```
Startup tab → Right-click program → Disable
```

**Check system performance:**
```
Performance tab → Check CPU, Memory, Disk, Network graphs
Red/orange = bottleneck
```

---

## Run Dialog (Win+R)

Common commands to run:
```
Win+R → Type command → Enter

cmd                 Open Command Prompt
powershell          Open PowerShell
notepad             Open Notepad
calc                Open Calculator
devmgmt.msc         Device Manager
compmgmt.msc        Computer Management
services.msc        Services manager
diskmgmt.msc        Disk Management
eventvwr.msc        Event Viewer
taskschd.msc        Task Scheduler
mstsc                Remote Desktop Connection
control             Control Panel
ms-settings:        Settings app
explorer C:\        Open File Explorer at location
```

---

## Troubleshooting Checklist

### Program won't start
```
□ Check Task Manager - any error processes?
□ Right-click properties - Run as Administrator?
□ Check disk space - disk full?
□ Check Event Viewer logs - system errors?
□ Restart the program
□ Restart Windows
```

### System running slow
```
□ Open Task Manager → Performance tab
□ Identify bottleneck (CPU/Memory/Disk/Network)
□ Check Processes tab - any high-usage programs?
□ Check Startup tab - disable unnecessary auto-start programs
□ Check disk space - free up space if <10% remaining
□ Run disk cleanup (search "Disk Cleanup")
```

### Can't access file/folder
```
□ Check permissions - Right-click → Properties → Security
□ Verify you're the owner or in group with access
□ Try "Run as Administrator"
□ Check if file is locked by another program
```

### Network not working
```
□ Check Network status - Settings → Network & Internet
□ Verify WiFi/Ethernet connected
□ Right-click network icon → Troubleshoot
□ Restart modem/router
□ Restart Windows networking: Win+X → Device Manager → Network adapters → Right-click → Restart
```

### Can't install software
```
□ Running as Administrator? - Right-click installer → Run as Administrator
□ Disk space available? - Check storage in Settings
□ Administrator account? - Standard users need admin approval
□ Installer compatible with Windows version?
□ Try: Settings → Apps → Troubleshoot → select program → Run troubleshooter
```

---

## Tips & Tricks

**Fast access to settings:**
```
Win+X opens quick menu with Common admin tools
```

**Virtual desktops:**
```
Win+Tab              Open Task View
Win+Ctrl+D           Create new virtual desktop
Win+Ctrl+→           Switch to next desktop
Win+Ctrl+←           Switch to previous desktop
```

**Clipboard history:**
```
Win+V                Open clipboard history
(Must enable in Settings first)
```

**Snipping tool (screenshot):**
```
Win+Shift+S          Open Snip & Sketch
(Or: Windows search → Snipping Tool)
```

**System file check:**
```
Run as Administrator:
sfc /scannow         Scan and repair system files
```

**Full system shutdown:**
```
Shutdown /s /t 0     Shut down immediately
```

**Sleep/Hibernate:**
```
Win+X → U → S        Sleep
Win+X → U → H        Hibernate (save state, use no power)
```

---

## Windows vs Linux Quick Comparison

| Task | Windows | Linux |
|------|---------|-------|
| Open terminal | Win+X → PowerShell | Ctrl+Alt+T (GUI) |
| File permissions | Right-click → Properties → Security | chmod 755 |
| List files | File Explorer (GUI) | ls -la |
| Create user | Settings → Accounts | useradd |
| View processes | Task Manager | ps aux |
| Monitor CPU/Memory | Task Manager → Performance | top / htop |
| Install software | Installer / Microsoft Store | apt install |
| Check logs | Event Viewer | /var/log files |
| View network | Settings → Network | ifconfig / ip |
| Edit config files | Notepad / Text editor | nano / vim |

**Key difference:** Windows emphasizes graphical interfaces, Linux emphasizes command-line.

