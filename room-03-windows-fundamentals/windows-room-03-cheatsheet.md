# TryHackMe Windows Fundamentals - Room 3: Quick Reference Cheatsheet

Fast reference for Windows security settings, commands, and tools.

---

## Quick Access - Keyboard Shortcuts

### Security Settings
```
Win+I                 Open Settings (go to Privacy & Security)
Win+R               Open Run dialog
Ctrl+Shift+Esc      Open Task Manager (monitor security)
Win+R → ms-winsecuritycenter:  Windows Security dashboard
```

---

## Windows Security - Quick Navigation

### Access Windows Security
```
Settings → Privacy & Security → Windows Security
Or: Windows search → "Windows Security"
```

### Main Sections (Direct Links)

**Virus & Threat Protection:**
```
Windows search → "Virus & threat protection"
Or: Settings → Privacy & Security → Windows Security → Virus & threat protection
```

**Firewall & Network Protection:**
```
Windows search → "Firewall & network protection"
Or: Settings → Privacy & Security → Windows Security → Firewall & network protection
```

**App & Browser Control:**
```
Windows search → "App & browser control"
Or: Settings → Privacy & Security → Windows Security → App & browser control
```

**Device Security:**
```
Windows search → "Device security"
Or: Settings → Privacy & Security → Windows Security → Device security
```

---

## Windows Update

### Manual Updates

**Check for updates:**
```
Settings → System → About → Check for updates
Or: Windows search → "Windows Update"
```

**View update history:**
```
Settings → System → About → View update history
Or: Control Panel → Windows Update → View update history
```

**Uninstall a recent update:**
```
Settings → System → About → View update history
→ Right-click update → Uninstall
```

**Advanced update options:**
```
Settings → System → About → Advanced options
→ Receive updates for other Microsoft products
→ Optional updates
```

### Update Commands

```
Win+R → powershell (as admin)

Get-HotFix              List all installed updates
Get-HotFix -Id KB5004693  Check if specific KB installed
Get-WindowsUpdate       List available updates
Install-WindowsUpdate   Install available updates
```

### Understanding KB Numbers

**KB = Knowledge Base**

Examples:
```
KB5004693   - Critical security patch
KB5003254   - Important update
KB5002123   - Optional update

Search "KB[number]" on Microsoft website to see what it fixes
```

---

## Windows Defender - Antivirus Management

### Quick Scan

**Start quick scan:**
```
Windows Security → Virus & threat protection → Current threats
→ Scan options → Quick scan
```

**Time:** Usually 1-2 minutes

### Full System Scan

**Start full scan:**
```
Windows Security → Virus & threat protection → Current threats
→ Scan options → Full scan
```

**Time:** 15-30 minutes depending on drive size

### Offline Scan

**Start offline scan:**
```
Windows Security → Virus & threat protection → Current threats
→ Scan options → Microsoft Defender Offline scan
→ Scan button → Restart and scan
```

**Time:** 10-20 minutes (requires restart)

**Use when:** Stubborn rootkit, suspected malware persistence

### Scan History

**View scan history:**
```
Windows Security → Virus & threat protection
→ Scroll down → Scan history
```

**Shows:**
- Date of scan
- Type (quick, full, offline)
- Status (completed, found threats)
- Threats detected

### Threat Quarantine

**View quarantined items:**
```
Windows Security → Virus & threat protection
→ Scroll down → Quarantined items
```

**Restore if false positive:**
```
Right-click item → Restore
(Only if you're 100% sure it's safe)
```

### Exclusions

**Add exclusion (DON'T scan this):**
```
Windows Security → Virus & threat protection
→ Manage settings → Add or remove exclusions
→ Folder or File or File type
→ Choose to exclude
```

**Example exclusions:**
```
Folder: C:\Games\[GameName]\
Reason: Game files trigger false positive

File: C:\Backups\backup.exe
Reason: Legitimate backup program

File type: .iso
Reason: ISO files shouldn't be scanned
```

### Real-Time Protection

**Status check:**
```
Windows Security → Virus & threat protection
→ Virus & threat protection settings
→ Real-time protection: On/Off
```

**Should be:** ON (enabled)

If OFF:
```
1. Check if malware disabled it (run scan in Safe Mode)
2. Check if conflicting antivirus installed (uninstall it)
3. Click toggle to re-enable
```

---

## Windows Defender Firewall

### Check Firewall Status

**Quick check:**
```
Windows Security → Firewall & network protection
→ Shows status of each network (Domain, Private, Public)
```

**Detailed status:**
```
Windows search → "Windows Defender Firewall with Advanced Security"
```

### Allow App Through Firewall

**Add app:**
```
Windows Security → Firewall & network protection
→ Allow an app through firewall
→ Change settings → Add → Browse for program
→ Check Private and/or Public (which networks)
→ OK
```

**Example:**
```
App: Chrome.exe
Private: ✓ (allow on home network)
Public: ☐ (block on public WiFi)
```

### Advanced Firewall Rules

**Access advanced settings:**
```
Windows search → "Windows Defender Firewall with Advanced Security"
Or: Control Panel → Windows Defender Firewall → Advanced Settings
```

**Create inbound rule:**
```
→ Inbound Rules (left pane)
→ New Rule (right pane)
→ Choose type (Program, Port, Predefined)
→ Set parameters
→ Block or Allow
→ Apply to Domain/Private/Public
```

**Common ports:**
```
HTTP: 80 (web browsing)
HTTPS: 443 (secure web)
DNS: 53 (domain name resolution)
FTP: 21 (file transfer)
RDP: 3389 (remote desktop)
```

### Disable Firewall (NOT recommended)

**Temporarily disable all firewall:**
```
Windows Security → Firewall & network protection
→ Click each network (Domain, Private, Public)
→ Turn off (red X)
```

**Better option:** Add specific app to allowed list instead of disabling firewall

**Re-enable firewall:**
```
Windows Security → Firewall & network protection
→ Click each network
→ Turn on (blue checkmark)
Or: netsh advfirewall set allprofiles state on (PowerShell)
```

---

## App & Browser Control - SmartScreen

### Check SmartScreen Status

**SmartScreen for files:**
```
Windows Security → App & browser control
→ Check apps and files
→ Dropdown: Warn, Block, Off
```

**SmartScreen for Edge:**
```
Edge → Settings → Privacy, search, and services
→ Security → SmartScreen → On/Off
```

### Configure SmartScreen

**Levels:**
```
Warn - Show warning but allow running
Block - Show warning and prevent running
Off - Disable SmartScreen (not recommended)
```

**Recommended:** Warn (allows expert users to override, blocks novices)

---

## Exploit Protection

### View Exploit Protection Settings

**Access exploit protection:**
```
Windows Security → App & browser control
→ Exploit protection settings
```

**Shows status of:**
- Control Flow Guard (CFG)
- Data Execution Prevention (DEP)
- Address Space Layout Randomization (ASLR)
- Return-oriented Programming (ROP) protection

### Enable/Disable Individual Protections

**System-wide settings:**
```
Exploit protection settings → System settings
→ Toggle each protection on/off
```

**Per-program settings:**
```
Exploit protection settings → Program settings
→ Add program → Set custom protections for that program
```

**Recommended:** Keep all ON (slight performance impact worth security benefit)

---

## Device Security - TPM & Core Isolation

### Check TPM Status

**Via GUI:**
```
Windows search → "TPM Management Console"
Or: Device Manager → Security devices → Trusted Platform Module 2.0
```

**Via Command Prompt:**
```
wmic os get /format:list | find "TPM"
Or: Get-Tpm (PowerShell)
```

**Status should show:**
```
TPM Version: 2.0
Status: Ready
```

### Enable TPM (if disabled)

**In BIOS/UEFI:**
```
1. Restart computer
2. Press Delete or F2 during boot (varies by manufacturer)
3. Find Security → TPM section
4. Enable TPM 2.0
5. Save and restart
```

### Core Isolation & Memory Integrity

**Access Core Isolation:**
```
Windows Security → Device security
→ Core isolation details
```

**Toggle Memory Integrity:**
```
Memory integrity → On/Off
(May require restart)
```

**Status:**
```
Running = Actively protecting
Stopped = Disabled
Not available = Hardware doesn't support (rare)
```

### Secure Boot

**Check Secure Boot status:**
```
System Information (msinfo32)
→ Look for "Secure Boot State"
Should show: "On"
```

**If off (not recommended):**
```
Restart → BIOS/UEFI → Security section → Secure Boot → Enable
```

---

## BitLocker Encryption

### Check BitLocker Status

**Simple check (Home users):**
```
Settings → System → About
→ Look for "Device encryption"
```

**Detailed status (Pro/Enterprise):**
```
Control Panel → BitLocker Drive Encryption
Or: manage-bde -status
```

**Status meanings:**
```
On = Drive encrypted
Off = Not encrypted
Suspended = Temporarily off (during updates)
```

### Enable BitLocker (Home - Device Encryption)

**Turn on encryption:**
```
Settings → System → About
→ Device encryption → Turn on
→ Windows creates recovery key
→ Backup recovery key!
```

**Time to encrypt:** Hours (depending on drive size)
**Performance:** Minimal impact with modern hardware

### Enable BitLocker (Pro/Enterprise)

**Full BitLocker:**
```
Control Panel → BitLocker Drive Encryption
→ Turn on BitLocker
→ Choose TPM or Password
→ Create recovery key
→ Save key to USB/Microsoft account/Print
→ Start encryption
```

### Backup Recovery Key (CRITICAL)

**Save recovery key:**
```
When BitLocker prompts, save key to:
1. Microsoft account (cloud backup) ← Recommended
2. USB drive (physical backup)
3. Printed copy (stored safely)
```

**Using recovery key:**
```
If TPM fails and system won't boot:
1. Boot from Windows media
2. Choose Repair
3. Enter 48-digit recovery key
4. Drive decrypts and boots
```

### Disable BitLocker

**Turn off encryption:**
```
Control Panel → BitLocker Drive Encryption
→ Turn off BitLocker
→ Windows decrypts (takes time)
```

**Temporary suspend (for updates):**
```
Right-click BitLocker icon → Manage BitLocker
→ Suspend protection
→ Enable again after updates
```

---

## Windows Sandbox

### Check if Available

**Requirement:** Windows 10 Pro or higher (NOT Home)

**Check version:**
```
Settings → System → About
→ Look for "Windows 10 Pro" or "Windows 11 Pro"
If "Home" - Sandbox not available (need to upgrade)
```

### Enable Windows Sandbox

**Turn on feature:**
```
Control Panel → Programs → Turn Windows features on or off
→ Check "Windows Sandbox"
→ Click OK
→ Restart computer
```

**Verify enabled:**
```
Windows search → "Windows Sandbox"
→ Should show application
```

### Launch Sandbox

**Run Sandbox:**
```
Windows search → "Windows Sandbox"
→ Double-click
→ Wait 1-2 minutes to start
→ Opens isolated Windows environment
```

**Typical sandbox startup time:** 30-60 seconds

### Using Sandbox

**Copy files to sandbox:**
```
From your main computer:
1. Open File Explorer (both main and sandbox)
2. Drag file from main → Sandbox window
```

**Run suspicious file in sandbox:**
```
1. Copy file into sandbox
2. Run file (isolated - can't harm main system)
3. Observe behavior
4. Close sandbox → Changes disappear
```

**Share folders with sandbox:**
```
Right-click Sandbox settings file
→ Edit properties
→ MapFolders section
→ Add folder mapping
```

### Exit Sandbox

**Close everything:**
```
Sandbox → Close window
→ All changes discarded
→ Malware deleted
→ Sandbox ready for next use
```

---

## Common Windows Security Commands

### System Information

```
systeminfo                   Full system info (shows OS, updates, TPM)
wmic os get caption          Show Windows version only
wmic sysaccount list         Show SYSTEM account info
```

### Defender Commands

```
Get-MpComputerStatus                Show Defender status
Get-MpPreference                    Show Defender settings
mpcmdrun.exe -scan -scantype 1      Start quick scan
mpcmdrun.exe -scan -scantype 2      Start full scan
```

### Firewall Commands

```
netsh advfirewall show allprofiles               Show firewall rules
netsh advfirewall set allprofiles state on       Enable firewall
netsh advfirewall set allprofiles state off      Disable firewall
netsh advfirewall reset all                      Reset to defaults
Get-NetFirewallProfile                           PowerShell: show rules
```

### BitLocker Commands

```
manage-bde -status                   Check status
manage-bde -on c:                    Enable on C: drive
manage-bde -off c:                   Disable on C: drive
manage-bde -pause c:                 Pause encryption
manage-bde -resume c:                Resume encryption
```

### Update Commands

```
Get-HotFix                                  List installed updates
Get-WindowsUpdate                           List available updates
Install-WindowsUpdate                       Install available updates
wuauclt /detectnow                         Force update check
```

---

## Troubleshooting Quick Reference

### Problem: Real-Time Protection Off

```
Solution 1: Turn on
→ Windows Security → Virus & threat protection
→ Real-time protection toggle → On

Solution 2: If malware disabled it
→ Boot Safe Mode (F8 at startup)
→ Run full scan in Safe Mode
→ Restart normal

Solution 3: Reset Defender
→ netsh advfirewall reset all (PowerShell)
→ Restart
```

### Problem: Firewall Won't Turn On

```
Solution 1: Reset firewall
→ netsh advfirewall reset all (PowerShell as admin)
→ Restart

Solution 2: Restore default settings
→ Windows Security → Firewall
→ Restore firewalls to default
```

### Problem: TPM Not Showing

```
Solution 1: Check BIOS
→ Restart → BIOS/UEFI (Delete or F2 key)
→ Security → TPM → Enable
→ Save and restart

Solution 2: Update drivers
→ Device Manager → Unknown device
→ Right-click → Update driver
→ Search automatically
```

### Problem: BitLocker Stuck on Encrypting

```
Solution: Wait
→ Encryption in progress (can take hours)
→ Don't restart during encryption
→ Leave computer on until complete
→ Check progress: manage-bde -status
```

### Problem: Windows Update Stuck

```
Solution 1: Wait overnight
→ Don't force restart
→ Updates can take hours

Solution 2: Boot to Safe Mode
→ Try updating from Safe Mode

Solution 3: Delete update cache
→ Delete C:\Windows\SoftwareDistribution\Download folder
→ Delete C:\Windows\Temp\*
→ Restart (Windows will re-download)
```

---

## Defense-in-Depth Checklist

**Complete Windows Security Setup:**

- [ ] Windows Update enabled and automatic
- [ ] Real-time protection ON (Defender)
- [ ] Full scan run within past month
- [ ] Firewall ON on all networks
- [ ] SmartScreen enabled
- [ ] Exploit protection enabled
- [ ] Core isolation / Memory integrity ON
- [ ] TPM 2.0 present and ready
- [ ] Secure Boot enabled (in BIOS)
- [ ] BitLocker enabled on sensitive drives
- [ ] Recovery key backed up (NOT on encrypted drive)
- [ ] Ransomware protection (Controlled Folder Access) ON

**If all checked:** System is well-protected

---

## Windows Security Status Icons

```
Green checkmark ✓   = Protected, everything good
Yellow warning ⚠    = Warning, needs attention (soon)
Red X ✗             = Problem, needs immediate action
Gray gear ⚙        = Loading or checking status

When you see yellow or red → Click it to fix
```

---

## Key Takeaways

1. **Updates are critical** - Don't skip them
2. **Multiple layers = Better security** - Use all features together
3. **Firewall blocks external** - Antivirus stops what gets through
4. **BitLocker prevents theft** - Encrypt sensitive drives
5. **Sandbox isolates testing** - Safe to test suspicious files
6. **TPM enables security** - Modern hardware security
7. **Check status regularly** - Dashboard shows health

---

**Use this cheatsheet as quick reference. Refer to detailed notes for deeper understanding.**
