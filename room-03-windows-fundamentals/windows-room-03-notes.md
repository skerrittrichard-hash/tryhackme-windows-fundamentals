# TryHackMe Windows Fundamentals - Room 3: Detailed Notes

Comprehensive explanations of Windows built-in security features covered in Room 3.

---

## Task 1: Windows Updates & Security

### What is Windows Update?

Windows Update is the mechanism by which Microsoft delivers security patches and feature updates to Windows systems.

**Why updates matter:**
- **Security patches** fix vulnerabilities that malware exploits
- **Bug fixes** solve stability problems
- **Driver updates** improve hardware compatibility
- **Feature updates** add new functionality

**Without updates:**
Your system is vulnerable to known exploits. Malware authors specifically target unpatched systems.

### Types of Updates

**Critical/Security Updates:**
- Fix security vulnerabilities
- Usually require restart
- Should install immediately
- Example: Patch for ransomware vulnerability

**Important Updates:**
- Fix stability issues
- Improve performance
- Less urgent than critical
- Example: Network driver improvement

**Recommended/Optional Updates:**
- Hardware drivers
- Non-security fixes
- Can be skipped if not needed
- Example: Printer driver update

**Feature Updates:**
- New Windows version (like 20H2, 21H1)
- Major changes and new features
- Larger download and install
- Usually annual release

### KB Articles

**KB = Knowledge Base**

Each update has a KB number (example: KB4012215).

**Why KB numbers matter:**
- Track exactly what was patched
- Look up what a specific KB fixes
- Report bugs with KB number (helps Microsoft identify the problem)
- Check if specific vulnerability is patched

**Example use:**
"We're vulnerable to PrintNightmare. Check Windows Update history for KB5004693. If not installed, apply it."

### Update Cycle

**Patch Tuesday:** Second Tuesday of each month
- Microsoft releases updates
- Windows systems automatically download
- Install at next restart or scheduled time

**Out-of-band updates:** When critical
- Critical vulnerability discovered mid-month
- Microsoft releases emergency patch
- Example: WannaCry ransomware in 2017

**Windows Update History:**
Windows keeps log of updates installed:
- Settings → System → About → View update history
- Shows date, KB number, status
- Useful for troubleshooting after update

### Troubleshooting Updates

**Stuck on "Installing updates":**
- Don't force restart (can corrupt files)
- Wait overnight
- If still stuck next day: Safe Mode, run Windows Update again

**Update fails to install:**
- Disk full? Run Disk Cleanup
- Conflicting antivirus? Temporarily disable
- Corrupted update cache? Delete temporary files

**Update broke something:**
- Settings → System → About → View update history
- Right-click recent update → Uninstall
- Windows reverts to previous version
- Restart when prompted

---

## Task 2: Windows Security

### Windows Security Dashboard

**What is Windows Security?**
Central hub for all Windows security features. One place to see status of all security components.

**Access Windows Security:**
```
Settings → Privacy & Security → Windows Security
Or: Windows search → "Windows Security"
```

**Main sections:**
1. **Virus & threat protection** - Antivirus status
2. **Account protection** - Account security
3. **Firewall & network protection** - Network security
4. **App & browser control** - Application security
5. **Device security** - Hardware security
6. **Device performance & health** - System status
7. **Family options** - Parental controls

### At a Glance Status

Quick overview showing:
- Green checkmark = Protected
- Yellow warning = Warning (needs attention)
- Red X = Problem (immediate action needed)

**Example scenario:**
Red X next to "Virus & threat protection" → Real-time protection is off → Click to fix it → Enable protection

### Real-Time Protection Status

Shows if Windows Defender is:
- Actively monitoring for threats
- Scanning files in real-time
- Updating threat definitions

**If OFF:** Why?
- Malware disabled it (scan in Safe Mode)
- Conflicting antivirus installed (uninstall it)
- Settings disabled it manually (re-enable)

---

## Task 3: Virus & Threat Protection

### Windows Defender Overview

**What is Windows Defender?**
Built-in antivirus that detects and removes malware.

**How it works:**
1. **Signature-based detection** - Matches known malware signatures (like fingerprints)
2. **Heuristic detection** - Analyzes behavior of suspicious programs
3. **Cloud protection** - Sends suspicious files to Microsoft cloud for analysis

**Real-time protection:**
Continuously monitors:
- Files being created/modified
- Programs starting
- Downloads completing
- USB drives being inserted

If suspicious activity detected → Block/quarantine immediately

### Scans

**Quick Scan (1-2 minutes):**
- Scans common malware locations
- Checks startup files
- Checks browser extensions
- Good for regular checking

**Full Scan (15-30 minutes):**
- Scans entire system
- Every file and folder
- More thorough
- Run weekly or when suspected infection

**Custom Scan:**
- Scan specific folder or drive
- Choose start time
- Example: Scan external USB drive

**Offline Scan:**
- Boots into minimal environment
- Scans before Windows fully loads
- Useful for stubborn rootkits
- Requires restart

### Threat Management

**Current Threats:**
If malware is detected:
- Name of threat shown
- Severity level indicated
- Option to quarantine or remove
- Usually automatic quarantine

**Quarantine:**
Threat moved to isolated location where it can't run. Example:
```
Detected: Trojan:Win32/Emotet.C
Action: Quarantine
Location: C:\ProgramData\Microsoft\Windows Defender\Quarantine\
```

**Removal:**
Threat permanently deleted. Use this for confirmed malware.

**Restore from Quarantine:**
Sometimes legitimate file is flagged by mistake:
- Settings → Virus & threat protection → Manage settings
- Scroll down → Quarantined items
- Right-click item → Restore

### Exclusions

**Why exclude?**
Some programs trigger false positives (flagged as malware when harmless).

**Common exclusions:**
- Gaming programs (sometimes flagged for mods)
- Development tools (sometimes flagged for code analysis)
- Virtual machines (contain test malware)
- Backup software (accessing system files)

**How to exclude:**
```
Settings → Virus & threat protection → Manage settings
→ Add or remove exclusions
→ Add folder, file, or file type
```

**Example:**
```
Exclude folder: C:\Games\MyGame\
Reason: Game files trigger false positive
Result: Defender ignores this folder
```

### Ransomware Protection

**Controlled Folder Access:**
Prevents programs from modifying files in protected folders.

**How it works:**
Only approved programs can access Documents, Pictures, Videos folders. Ransomware tries to encrypt them → Blocked.

**Protected folders:**
- Documents
- Pictures
- Videos
- Music
- Downloads

**Allowing a program:**
If legitimate program needs access:
```
Settings → Virus & threat protection → Manage ransomware protection
→ Allow app through ransomware protection
→ Add the program
```

**Example:**
Backup software needs to access Documents → Add to allowed programs → Can now backup.

---

## Task 4: Firewall & Network Protection

### Windows Defender Firewall

**What is a firewall?**
A filter that controls which network traffic can enter/exit your computer.

**How it works:**
1. Incoming connection → Firewall checks
2. Is it from a trusted source? → Allow
3. Is it attempting known attack? → Block
4. Is it from unknown source? → Ask or block

**Default behavior:**
- **Inbound:** Block all (unless explicitly allowed)
- **Outbound:** Allow all (programs can send data out)

This is reasonable: Inbound = external attacks, Outbound = your programs doing work.

### Network Profiles

**Domain Profile:**
- Work network connected to company domain
- More lenient (company IT configured)

**Private Profile:**
- Home or trusted network
- Moderate filtering (allow some apps)

**Public Profile:**
- Coffee shop, airport, public WiFi
- Strictest filtering (block most inbound)

**Why three profiles?**
Home network = more trusted = relax restrictions. Public WiFi = less trusted = strict restrictions.

**Setting a network as trusted:**
```
Settings → Network & Internet → WiFi
→ WiFi name → Properties
→ Profile type → Private or Public
```

### Firewall Rules

**Allow an application:**
```
Windows Security → Firewall → Allow app through firewall
→ Check the app
→ Check Private and/or Public (which networks)
```

**Example:**
```
App: Chrome.exe
Private: Checked (allow on home network)
Public: Unchecked (block on public WiFi)
Result: Chrome can use home network but not public WiFi
```

**Block an application:**
```
Windows Security → Firewall → Allow app through firewall
→ Uncheck the app
```

**Advanced rules:**
Power users can create custom rules:
```
Windows Defender Firewall with Advanced Security
→ Inbound Rules or Outbound Rules
→ New Rule
→ Set program, port, direction, action
```

---

## Task 5: App & Browser Control

### SmartScreen

**What is SmartScreen?**
A feature that blocks known malicious websites and downloads.

**How it works:**
1. You click link or download file
2. Windows checks against list of known malicious sites/files
3. If on list → Show warning
4. User can ignore warning and proceed (not recommended)

**Real-world example:**
```
User downloads banking_update.exe from sketchy forum
SmartScreen recognizes it as known trojan
Shows: "Windows Defender prevented unrecognized app from running"
User cannot run it without explicitly choosing "Run anyway"
```

**SmartScreen for browsers:**
- Edge/Chrome integration
- Warns about malicious websites
- Blocks phishing sites
- Blocks download scams

**Configuring SmartScreen:**
```
Settings → Privacy & Security → Windows Security
→ App & browser control
→ Check apps and files
→ Choose filtering level
```

### Exploit Protection

**What is an exploit?**
Code that takes advantage of a vulnerability to gain unauthorized access.

**Example exploit:**
```
Vulnerability: Buffer overflow in old Windows version
Exploit: Specially crafted file causes buffer to overflow
Result: Malware gains system privileges
```

**Exploit Protection defenses:**

**Control Flow Guard (CFG):**
- Ensures program execution follows expected path
- Detects if exploit tries to jump to unexpected code
- Blocks the jump = stops exploit

**Data Execution Prevention (DEP):**
- Prevents code from running in data areas
- Malware often tries to execute from data section
- DEP blocks this = stops exploit

**Address Space Layout Randomization (ASLR):**
- Randomizes where programs load in memory
- Exploit assumes program at fixed address
- Program is at different address = exploit fails

**Real-time protection:**
All three above protections run continuously. Together they stop most exploits.

**Configuring Exploit Protection:**
```
Settings → Privacy & Security → Windows Security
→ App & browser control
→ Exploit protection settings
→ Turn on/off specific protections
```

---

## Task 6: Device Security

### Trusted Platform Module (TPM)

**What is TPM?**
A hardware chip on motherboard that stores cryptographic keys securely.

**Why TPM matters:**
- Stores encryption keys in hardware (can't be stolen from software)
- Verifies system hasn't been tampered with
- Enables BitLocker encryption
- Required for Windows 11 Pro

**TPM specifications:**
- **TPM 1.2** - Older, less secure
- **TPM 2.0** - Modern, required for Windows 11
- Firmware-based TPM - Software-based (less secure)
- Discrete TPM - Hardware chip (more secure)

**Checking TPM:**
```
Windows search → "TPM Management Console"
Or: Device Manager → Security devices → Trusted Platform Module 2.0
```

**Status should show:**
```
TPM Version: 2.0
Status: Ready
```

If missing or not ready → Reboot and check BIOS/UEFI settings (might need to enable).

### Core Isolation & Memory Integrity

**What is Core Isolation?**
A security feature that isolates critical system functions in a separate protected area.

**Memory Integrity:**
Checks that system memory hasn't been modified by malware.

**How it works:**
1. Core isolation runs in secure container
2. Monitors memory for unauthorized changes
3. If malware tries to modify memory → Detects and blocks

**Performance impact:**
Slight (~3-5%) but worth security benefit.

**Enabling Core Isolation:**
```
Settings → Privacy & Security → Windows Security
→ Device security
→ Core isolation details
→ Memory integrity → Toggle on
```

### Secure Boot

**What is Secure Boot?**
Verifies that boot files are authentic before starting Windows.

**Prevents:**
- BIOS/UEFI rootkits that load before Windows
- Bootkits that hijack early boot process
- Unsigned boot code

**Status:**
```
Settings → System → About
→ Device specifications
→ Secure Boot: On (should be On)
```

If off → Enable in BIOS/UEFI.

---

## Task 7: BitLocker

### Full Disk Encryption

**What is BitLocker?**
Built-in full-disk encryption that encrypts entire drive.

**Why encrypt?**
- Laptop stolen? Data is unreadable without encryption key
- Drive repurposed? Data securely wiped
- Compliance requirement (healthcare, finance)

**How it works:**
1. All files encrypted with AES-256 (military-grade)
2. TPM stores encryption key
3. Only computer with matching TPM can decrypt
4. If hard drive removed and installed elsewhere → Can't read data

**Real-world scenario:**
```
Company laptop with BitLocker lost in taxi
Thief has the hard drive
Without BitLocker: All company secrets readable
With BitLocker: Files appear as random gibberish
Result: Data is safe
```

### BitLocker Requirements

**For automatic encryption (without TPM):**
- TPM 2.0 chip (hardware requirement)
- UEFI firmware with Secure Boot

**Without TPM:**
- Must set password as additional security
- Slower (more CPU intensive)
- Less convenient (type password at boot)

### Enabling BitLocker

**Check if available:**
```
Settings → System → About
→ Scroll to "Device encryption"
→ If available, can use BitLocker
```

**Turn on encryption:**
```
Settings → System → About
→ Device encryption → Turn on
→ May ask to create recovery key
→ Save recovery key safely!
```

**For Pro/Enterprise (full BitLocker):**
```
Control Panel → BitLocker Drive Encryption
→ Turn on BitLocker
→ Choose TPM or password
→ Create recovery key
→ Start encryption
```

**Encryption takes time:**
Depending on drive size, can take hours. System remains usable during encryption.

### Recovery Key

**What is recovery key?**
A long code (48-digit) that can decrypt BitLocker if TPM fails.

**Why critical:**
If TPM fails and you lose recovery key:
- Can't decrypt the drive
- Data is permanently inaccessible
- Even Microsoft can't help

**Storing recovery key:**
- Save to Microsoft account (cloud backup)
- Print and store in safe place
- Never store on encrypted drive itself
- Never share with untrusted people

**Using recovery key:**
If computer won't boot because TPM failed:
1. Insert Windows installation media
2. Choose Repair option
3. Enter recovery key
4. Drive decrypts and boots normally

---

## Task 8: Windows Sandbox

### What is Windows Sandbox?

Windows Sandbox is a lightweight virtual environment that runs isolated from main Windows.

**Real-world use:**
```
You receive suspicious email attachment
Don't want to run it on your real computer
Open Windows Sandbox
Run attachment in sandbox
If malware → Sandbox isolates it, real computer safe
Restart sandbox → Malware gone
```

**Key features:**
- Completely isolated from main system
- No network access to main computer
- Changes don't persist (reset when closed)
- Safe to test anything

### How to Enable Sandbox

**Requirements:**
- Windows 10 Pro or higher (not Home edition)
- Virtualization enabled in BIOS
- At least 4GB RAM (8GB recommended)

**Enable Windows Sandbox:**
```
Control Panel → Programs → Turn Windows features on or off
→ Check "Windows Sandbox"
→ Restart computer
```

**Launch Sandbox:**
```
Windows search → "Windows Sandbox"
→ Click "Windows Sandbox"
→ Wait 1-2 minutes for startup
→ Use like normal Windows (isolated copy)
```

### Using Windows Sandbox

**Typical workflow:**
```
1. Open Windows Sandbox
2. Copy suspicious file to sandbox
3. Run the file
4. Observe behavior (does it try to network? Modify files?)
5. Close sandbox without saving
6. Malware is gone
7. Main computer unaffected
```

**What's isolated:**
- File system (changes disappear)
- Network (can see main computer's network but isolated)
- Registry (sandbox registry is separate)
- Processes (sandbox processes can't access main system)

**What persists:**
- Main computer unaffected
- Downloads folder shows what you downloaded
- Windows Update still applies to main system

### Sandbox Security Implications

**Safe activities:**
- Test unknown programs
- Experiment with settings
- Download and run files from untrusted sources
- Manually test malware samples (in security research)

**Not fully safe:**
- Zero-day malware might escape
- Shouldn't replace antivirus
- Sandbox is belt-and-suspenders, not primary defense

**Use as supplement:**
Antivirus = primary defense. Sandbox = secondary defensive layer.

---

## Troubleshooting Guide

### "Real-time protection is off"

**Causes:**
- Malware disabled it
- Conflicting antivirus
- Settings disabled it

**Solution:**
```
1. Boot to Safe Mode (press F8 at startup)
2. Open Windows Defender
3. Run full scan
4. Settings → Virus & threat protection
5. Enable "Real-time protection"
```

### "Firewall is off"

**Causes:**
- Malware disabled it
- Manually turned off
- Domain policy disabled it

**Solution:**
```
Windows Security → Firewall → Restore firewall settings
Or: netsh advfirewall reset all (Command Prompt as admin)
```

### "BitLocker won't turn on"

**Causes:**
- TPM not ready
- Drive already encrypted differently
- Older BIOS doesn't support

**Solution:**
```
1. Check TPM: Device Manager → Security devices → TPM 2.0
2. If not present or error: Check BIOS/UEFI (enable TPM)
3. Restart computer
4. Try BitLocker again
```

### "Windows Update stuck"

**Causes:**
- Update in progress (wait)
- Corrupted update
- Antivirus interference

**Solution:**
```
1. Wait overnight (don't force restart)
2. If still stuck: Boot to Safe Mode
3. Run Windows Update again
4. If still stuck: Delete C:\Windows\SoftwareDistribution\Download (as admin)
5. Restart, Windows Update will re-download
```

---

## Quick Command Reference

### Windows Update Commands

```
wuauclt /detectnow              Force update check
Get-WindowsUpdate (PowerShell)   List available updates
Install-WindowsUpdate (PS)       Install updates
```

### Windows Defender Commands

```
mpcmdrun.exe -scan -scantype 1       Quick scan
mpcmdrun.exe -scan -scantype 2       Full scan
mpcmdrun.exe -removedefinitions      Remove threat definitions
Get-MpComputerStatus (PowerShell)    Show Defender status
```

### Firewall Commands

```
netsh advfirewall show allprofiles   Show firewall status
netsh advfirewall set allprofiles state on   Enable firewall
netsh advfirewall reset all           Reset to default
Get-NetFirewallProfile (PowerShell)    Show firewall rules
```

### BitLocker Commands

```
manage-bde -status               Show BitLocker status
manage-bde -on c:               Enable BitLocker on C: drive
manage-bde -off c:              Disable BitLocker on C: drive
```

---

## Summary: Windows Security Layers

**Layer 1: Prevention (Before malware arrives)**
- Windows Update - Patch vulnerabilities
- SmartScreen - Block known malicious downloads
- Firewall - Block incoming attacks

**Layer 2: Detection (If malware gets in)**
- Real-time protection - Detect malware on arrival
- Scans - Find existing infections
- Event Viewer - Log security events

**Layer 3: Containment (If malware runs)**
- Controlled Folder Access - Prevent ransomware
- Exploit Protection - Stop exploitation
- Quarantine - Isolate malware

**Layer 4: Recovery (After incident)**
- BitLocker - Prevent theft
- System Restore - Recover from damage
- Backups - Restore lost data

**All layers together = Defense-in-Depth.**
