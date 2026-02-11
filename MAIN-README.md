# TryHackMe Windows Fundamentals - Complete Series

Comprehensive documentation of TryHackMe Windows Fundamentals (Rooms 1, 2, and 3). Full Windows system administration and security foundation with 33 hands-on tasks, detailed notes, quick references, and portfolio-ready documentation.

**Series Status:** ✅ **COMPLETE** (All 3 rooms documented)

---

## Series Overview

Windows Fundamentals is a three-part series that teaches you to administer and secure Windows systems. This is not a user-level course—it covers what IT professionals and system administrators actually do.

### The Three Rooms

**Room 1: Desktop & System Administration Basics**
- Windows desktop environment and navigation
- File system hierarchy and organization
- NTFS permissions and access control
- User account management
- Basic administrative tools
- **Skills:** Navigate Windows, manage files/folders, understand permissions

**Room 2: System Administration Tools**
- System Configuration utility (msconfig)
- Task Scheduler and automation
- Computer Management (central hub)
- Services and startup management
- Event Viewer for troubleshooting
- Task Manager advanced features
- Resource and Performance monitoring
- Registry Editor
- Windows Management Instrumentation (WMI)
- Command-line administration
- **Skills:** Administer Windows, troubleshoot problems, automate tasks, monitor performance

**Room 3: Security Hardening**
- Windows Updates and patching
- Windows Defender antivirus
- Windows Firewall configuration
- Application and browser control
- Device security (TPM, Core Isolation)
- BitLocker encryption
- Windows Sandbox isolation
- **Skills:** Secure Windows, protect against threats, configure security features

### The Big Picture

```
PROGRESSION

Room 1: FOUNDATION
└─ "What is it? Where is it?"
   └─ Desktop, files, permissions, users
      └─ Understand the system

Room 2: ADMINISTRATION  
└─ "How do I manage it?"
   └─ Tools, services, scheduling, monitoring
      └─ Manage the system

Room 3: SECURITY
└─ "How do I protect it?"
   └─ Updates, antivirus, firewall, encryption
      └─ Protect the system

RESULT: Complete Windows System Administration Foundation
```

---

## Repository Contents

### Room-by-Room Documentation

Each room has:
- **README.md** - Comprehensive overview with sysadmin relevance and real-world scenarios
- **notes.md** - Detailed concept explanations (how things work, why they matter)
- **commands-cheatsheet.md** - Quick reference (commands, keyboard shortcuts, settings navigation)
- **screenshots/** - Lab completion evidence with task documentation

### Quick Navigation

**Room 1 (Desktop Basics)**
- [room-01-README.md](room-01-README.md) - Overview
- [room-01-notes.md](room-01-notes.md) - Detailed concepts
- [room-01-commands-cheatsheet.md](room-01-commands-cheatsheet.md) - Quick reference

**Room 2 (Administration)**
- [room-02-README.md](room-02-README.md) - Overview
- [room-02-notes.md](room-02-notes.md) - Detailed concepts
- [room-02-commands-cheatsheet.md](room-02-commands-cheatsheet.md) - Quick reference

**Room 3 (Security)**
- [room-03-README.md](room-03-README.md) - Overview
- [room-03-notes.md](room-03-notes.md) - Detailed concepts
- [room-03-commands-cheatsheet.md](room-03-commands-cheatsheet.md) - Quick reference

**Progress Tracking**
- [LEARNING-LOG.md](LEARNING-LOG.md) - Series progress, key learnings, time investment

---

## What You'll Learn (Complete)

### Hands-On Skills (33 Total Tasks)

| Skill | Room | Mastery |
|-------|------|---------|
| Windows navigation | 1 | ✅ |
| File permissions | 1 | ✅ |
| User accounts | 1 | ✅ |
| Task Manager | 1 | ✅ |
| System Configuration | 2 | ✅ |
| Services management | 2 | ✅ |
| Task Scheduler | 2 | ✅ |
| Computer Management | 2 | ✅ |
| Event Viewer | 2 | ✅ |
| Registry Editor | 2 | ✅ |
| Command-line administration | 2 | ✅ |
| Windows Updates | 3 | ✅ |
| Antivirus (Defender) | 3 | ✅ |
| Firewall configuration | 3 | ✅ |
| Device security (TPM) | 3 | ✅ |
| BitLocker encryption | 3 | ✅ |
| Windows Sandbox | 3 | ✅ |

### Conceptual Understanding

**System Level:**
- How Windows starts up
- What runs in the background
- How resources are used
- What security is protecting you

**Administration Level:**
- How to manage users and permissions
- How to automate tasks
- How to troubleshoot problems
- How to monitor system health

**Security Level:**
- How to protect against threats
- How to recover from incidents
- How to encrypt sensitive data
- How to test suspicious files safely

---

## Career Relevance

### Job Titles That Use These Skills

- **System Administrator** - Daily use of Room 2 & 3 skills
- **IT Operations Specialist** - Daily use of all rooms
- **Support Technician** - Room 1 & 2 troubleshooting
- **Security Administrator** - Room 3 focus
- **Network Administrator** - Room 2 & 3 for network management
- **Help Desk Technician** - Room 1 & 2 for user support
- **Windows Systems Engineer** - All rooms as foundation

### Interview Preparation

**Common Interview Questions:**

*"How would you troubleshoot a slow Windows system?"*
- Answer: Task Manager → Performance tab → Identify bottleneck → Resource Monitor → Find culprit process

*"How do you speed up Windows startup?"*
- Answer: System Configuration → Services tab (disable unused) → Task Manager → Startup tab (disable apps)

*"Explain NTFS permissions."*
- Answer: Read, Write, Modify, Full Control. Inherited from parent folders. Use Security tab to assign.

*"How do you secure a Windows laptop?"*
- Answer: Windows Update (patches), Defender (malware), Firewall (network), BitLocker (encryption)

*"What's the difference between Administrator and Standard user?"*
- Answer: Admin has full system access (dangerous). Standard has limited access (safer). Best practice: Use Standard daily.

*"How would you schedule a daily backup?"*
- Answer: Task Scheduler → New task → Set trigger (daily time) → Set action (backup script) → Conditions → Save

---

## How to Use This Repository

### For Learning

1. **Start with Room 1:**
   - Read room-01-README.md for overview
   - Read room-01-notes.md for detailed concepts
   - Review room-01-commands-cheatsheet.md for quick lookups
   - Reference room-01-screenshots/ for task evidence

2. **Progress to Room 2:**
   - Same structure as Room 1
   - Builds on Room 1 knowledge
   - Introduces administration tools

3. **Complete with Room 3:**
   - Same structure as Rooms 1 & 2
   - Focuses on security hardening
   - Integrates Rooms 1 & 2 concepts

### For Job Interview Prep

1. **Week Before Interview:**
   - Read all three README files (1 hour)
   - Review cheatsheets (30 minutes)
   - Practice keyboard shortcuts (15 minutes)

2. **Day Before Interview:**
   - Skim LEARNING-LOG.md for key concepts (30 minutes)
   - Review common interview questions above (20 minutes)

3. **Before Interview:**
   - Confidently say: "I've completed TryHackMe Windows Fundamentals (all 3 rooms)"
   - Show repo on GitHub
   - Mention specific skills: "I can configure Task Scheduler, manage services, secure with BitLocker..."

### For Reference

- **Quick lookup needed?** → room-XX-commands-cheatsheet.md
- **Need to understand concept?** → room-XX-notes.md
- **Want overview of topic?** → room-XX-README.md
- **Track your progress?** → LEARNING-LOG.md

---

## Progression Path

### Difficulty: Beginner → Intermediate

```
Room 1: Beginner
├─ Understanding Windows structure
├─ Learning file system
├─ User account basics
└─ Accessible to anyone

Room 2: Intermediate  
├─ System administration concepts
├─ Managing services and tasks
├─ Troubleshooting methodology
└─ Requires Room 1 knowledge

Room 3: Intermediate-Advanced
├─ Security hardening concepts
├─ Protecting against threats
├─ Encryption and isolation
└─ Integrates Rooms 1 & 2 knowledge
```

### Time Investment

| Room | Lab Time | Documentation | Total | Cumulative |
|------|----------|---------------|-------|------------|
| Room 1 | 60 min | 90 min | 150 min | 150 min |
| Room 2 | 90 min | 120 min | 210 min | 360 min |
| Room 3 | 75 min | 100 min | 175 min | 535 min |
| **Total** | **225 min** | **310 min** | **535 min** | **8.9 hours** |

**ROI:** ~9 hours learning = foundational skills for IT/Security roles

---

## Sysadmin Tasks You Can Now Do

### User Management (Room 1)
- Create user accounts
- Manage permissions
- Understand file access control

### System Administration (Room 2)
- Schedule automated tasks (backups, updates, maintenance)
- Manage services (start, stop, disable)
- Troubleshoot using Event Viewer
- Monitor performance with Resource Monitor
- Configure system via Registry
- Manage hardware (Device Manager)

### Security Management (Room 3)
- Apply security updates
- Configure antivirus
- Manage firewall rules
- Encrypt sensitive data with BitLocker
- Test suspicious files safely in Sandbox
- Monitor security status

### Troubleshooting (All Rooms)
- Identify performance bottlenecks
- Find and fix problems via Event Viewer
- Restore from system restore points
- Safe boot for diagnostics
- Boot into Safe Mode

---

## Defense-in-Depth Security (Room 3)

Windows security uses multiple layers working together:

```
Layer 1: PREVENTION
├─ Windows Update (patches vulnerabilities)
├─ SmartScreen (blocks known malicious)
└─ Firewall (blocks incoming attacks)

Layer 2: DETECTION
├─ Real-time protection (finds malware)
├─ Scans (existing infections)
└─ Event Viewer (security logs)

Layer 3: CONTAINMENT
├─ Controlled Folder Access (ransomware)
├─ Exploit Protection (stops exploitation)
└─ Quarantine (isolates malware)

Layer 4: RECOVERY
├─ BitLocker (prevents theft)
├─ System Restore (recover from damage)
└─ Backups (restore lost data)

Result: Multiple defenses catch different threats
```

---

## Key Takeaways by Room

### Room 1: Foundation

**You learned:**
- Windows file system structure
- NTFS permissions (Read, Write, Modify, Full Control)
- User account types (Admin vs Standard)
- Basic system tools (Task Manager, Settings)

**Key insight:** Permissions control access. Understand them = secure systems.

### Room 2: Administration

**You learned:**
- System Configuration for startup management
- Task Scheduler for automation
- Services for background programs
- Event Viewer for troubleshooting
- Registry for system configuration

**Key insight:** Services control what runs. Events tell you what failed. Logs are your diagnostic tool.

### Room 3: Security

**You learned:**
- Windows Update keeps systems patched
- Defender antivirus detects threats
- Firewall blocks bad traffic
- BitLocker encrypts sensitive data
- Multiple security layers = defense-in-depth

**Key insight:** Security is layered. No single tool is perfect. Together they stop most threats.

---

## Real-World Application

### Day 1 on IT Job

You'll use:
- **Room 1 skills:** Understand file structure, manage user permissions
- **Room 2 skills:** Troubleshoot via Event Viewer, manage services, use Task Manager
- **Room 3 skills:** Apply security updates, verify antivirus, configure firewall

### Daily Sysadmin Work

Morning:
- Check Event Viewer for overnight errors (Room 2)
- Verify Windows Update applied (Room 3)
- Monitor performance with Resource Monitor (Room 2)

Afternoon:
- Create new user account (Room 1)
- Schedule backup task (Room 2)
- Configure firewall rule for new app (Room 3)

Emergency:
- System slow? Use Task Manager and Resource Monitor (Rooms 1 & 2)
- Security breach? Check Event Viewer, isolate in Sandbox (Rooms 2 & 3)
- Can't access file? Fix permissions (Room 1)

---

## Interview Stories

**Tell these in interviews (with specific examples from your repo):**

**Story 1: File Permission Problem**
"User couldn't access a shared folder. I right-clicked → Properties → Security tab → Checked permissions → User wasn't in the group → Added user → Problem solved. Demonstrated NTFS permission understanding."

**Story 2: System Performance**
"Manager said system was slow. I opened Task Manager → Performance tab → Disk maxed out. Resource Monitor → Found backup software hammering disk → Rescheduled to off-hours → Performance restored."

**Story 3: Security Configuration**
"Company needed to encrypt all laptops. I used BitLocker with TPM → All devices encrypted → Created recovery keys → Stored in secure location → Protected against theft."

**Story 4: Automation**
"Manually backing up files took 2 hours weekly. I created Task Scheduler job to run nightly → Saved 2 hours/week → 100+ hours/year saved."

---

## Technical Skills Demonstrated

**To recruiters, this repository shows:**

1. ✅ Windows system administration competency
2. ✅ Hands-on experience with key tools (30+ tools/utilities)
3. ✅ Understanding of security concepts
4. ✅ Problem-solving methodology
5. ✅ Ability to document technical knowledge
6. ✅ Professional portfolio organization
7. ✅ Time management (535 minutes invested)
8. ✅ Commitment to learning (comprehensive documentation)

---

## Comparison to Other Learning

| Method | Practical | Documented | Portfolio-Ready | Interview-Ready |
|--------|-----------|------------|-----------------|-----------------|
| YouTube videos | ✓ | ✗ | ✗ | Partial |
| Book learning | Partial | ✓ | ✗ | Partial |
| University course | ✓ | ✓ | ✗ | Partial |
| **This repo** | **✓** | **✓** | **✓** | **✓** |

**Advantage:** Hands-on practical + comprehensive documentation + portfolio ready + interview prep in one place.

---

## Next Learning Path

**After Windows Fundamentals:**

1. **Windows Server Administration** - Apply skills to server OS
2. **Active Directory Fundamentals** - User management at scale  
3. **CompTIA Security+** - Certification (uses this knowledge)
4. **PowerShell Scripting** - Automate everything
5. **Penetration Testing** - Find Windows vulnerabilities
6. **Network Administration** - Integrate Windows with networks

---

## Portfolio Impact

**GitHub Profile Improvement:**

- Before: Generic coding projects
- After: Professional IT infrastructure repo

**What recruiters see:**
- "This person understands Windows"
- "They can document technical knowledge"
- "They're serious about IT career"
- "They have hands-on experience"
- "They're organized and thorough"

**Interview conversation starter:**
"I have a GitHub repository with complete documentation of Windows Fundamentals. All 3 rooms, 33 hands-on tasks, detailed notes, and quick references. Want to take a look?"

---

## Repository Structure

```
tryhackme-windows-fundamentals/
│
├── README.md (this file - series overview)
├── LEARNING-LOG.md (progress tracking)
│
├── room-01-README.md (Room 1 overview)
├── room-01-notes.md (Room 1 detailed concepts)
├── room-01-commands-cheatsheet.md (Room 1 quick reference)
├── room-01-screenshots/ (12 task images)
│
├── room-02-README.md (Room 2 overview)
├── room-02-notes.md (Room 2 detailed concepts)
├── room-02-commands-cheatsheet.md (Room 2 quick reference)
├── room-02-screenshots/ (13 task images)
│
├── room-03-README.md (Room 3 overview)
├── room-03-notes.md (Room 3 detailed concepts)
├── room-03-commands-cheatsheet.md (Room 3 quick reference)
└── room-03-screenshots/ (8 task images)

Total: 10 markdown files + 33 screenshot images
```

---

## Getting Started

### If you're new to Windows administration:
1. Start with [room-01-README.md](room-01-README.md)
2. Read [room-01-notes.md](room-01-notes.md) for concepts
3. Use [room-01-commands-cheatsheet.md](room-01-commands-cheatsheet.md) for quick lookups

### If you're preparing for an interview:
1. Skim all three README files (1 hour)
2. Review all three cheatsheets (1 hour)
3. Check [LEARNING-LOG.md](LEARNING-LOG.md) for common questions
4. Practice explaining concepts to a friend

### If you need quick reference:
- [room-02-commands-cheatsheet.md](room-02-commands-cheatsheet.md) - Most comprehensive quick ref
- [room-03-commands-cheatsheet.md](room-03-commands-cheatsheet.md) - Security-focused quick ref
- [room-01-commands-cheatsheet.md](room-01-commands-cheatsheet.md) - Navigation and permissions

---

## Completion Status

✅ **Room 1: Complete** (12 tasks, 12 screenshots)
✅ **Room 2: Complete** (13 tasks, 13 screenshots)  
✅ **Room 3: Complete** (8 tasks, 8 screenshots)

**Series: COMPLETE** (33 total tasks)

---

## Support for Your Job Search

This repository is designed to:
1. ✅ Demonstrate Windows competency to recruiters
2. ✅ Prepare you for technical interviews
3. ✅ Serve as reference material on the job
4. ✅ Show your commitment to professional development
5. ✅ Prove you can learn and document independently

**Bottom line:** This is not just learning material—it's professional portfolio documentation that gets jobs.

---

## Final Thoughts

Windows Fundamentals teaches you not just what to do, but why it matters. You've learned:

- **Desktop & Basics** → Understand the system
- **Administration Tools** → Manage the system  
- **Security Hardening** → Protect the system

You now have the **foundation for IT career advancement**. Whether you pursue system administration, security, network administration, or IT support, these skills apply everywhere.

**Your next steps:**
1. Push this repo to GitHub
2. Share it in interviews
3. Reference it daily on the job
4. Build on it with advanced certifications

---

**Windows Fundamentals Complete.**  
**Ready for IT career advancement.**

---

**Repository Created:** February 2026  
**Total Time Investment:** 535 minutes (8.9 hours)  
**Total Documentation:** 10 markdown files + 33 screenshots  
**Career Impact:** Foundation for junior sysadmin role  
**Status:** ✅ Complete and portfolio-ready

**See individual room READMEs for detailed technical content.**
