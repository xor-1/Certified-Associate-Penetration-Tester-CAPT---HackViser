I have completed the Linux fundamentals and did noted them as I am using Linux (Kali and Ubuntu) for years and I have a strong grip on them.

I am starting out with Windows Fundamentals.

**Summary:**
This windows fundamental course will guide you through the general structure, security features and usage of a windows based system. A bit of history of windows is also touched.

---

## Windows Architecture

### System Files

**Program Files:**

- \Program Files: For 64-bit programs on 64-bit Windows.
- \Program Files (x86): For 32-bit programs on 64-bit Windows.
- \ProgramData: For program data independent of users.

**User Data:**

- \Users: Contains a profile folder for each user.
- \Public: For files shared among users.
- [username]\AppData: For per-user application data and settings.

**Windows System:**

- \Windows: Contains Windows itself.
- \System, \System32, \SysWOW64: Contains Windows core components and dynamic link libraries (DLLs).
- \WinSxS: Windows component store (including updates and service packs).

**Other:**

- \PerfLogs: Windows performance logs (empty by default).

### File System Architecture evolution

```
FAT -> FAT32 -> exFAT -> NTFS
```

---
## Access Control List (ACL)

ACL stands for Access Control List. This list determines who can access a resource (file, folder, printer, network resource, etc.) on a computer system and what access permissions they have.

ACL allows system administrators and users to protect sensitive data and ensure that only authorized individuals can access specific resources.

In NTFS disks, access permissions for files and folders can be set.

The adjustable permissions are:

- Full control
- Modify
- Read and execute
- List folder contents
- Read
- Write

---

## ADS (Alternate Data Streams)

**ADS (Alternate Data Streams)** is a feature of the Windows **NTFS file system** that allows a file to store hidden additional data streams along with the main file content.

### Key Points

- ADS exists only in **NTFS** file system.
    
- Normal file has one stream → ADS allows multiple hidden streams.
    
- Hidden streams are **not visible** in Windows Explorer.
    
- File size does **not change visibly** when data is stored in ADS.
    

### Syntax

```
filename:streamname
```

Example:

```
test.txt:secret.txt
```

### Legitimate Uses

- Storing metadata
    
- Compatibility with Macintosh systems
    
- Security zone information
    

### Malicious Uses

- Hiding malware
    
- Bypassing antivirus detection
    
- Maintaining persistence
    
- Concealing payloads inside legitimate files
    

### Detection

```
dir /r
```

or forensic/security tools.

### Why Attackers Use ADS

- Hidden from normal directory listing
    
- Difficult to detect
    
- File appears normal to users
    
- Often ignored by basic antivirus scans
    
### One-Line Summary
ADS is an NTFS feature that allows attackers to hide malicious data inside legitimate files using invisible data streams.

---
## Shadow Copy
Shadow copy is a feature in Windows that allows you to create and store a copy of a file or folder at a specific point in time. This helps you restore files or folders if you accidentally delete or modify them.

---

## Windows User Structure

Windows uses a user structure to assign different access rights to users.

### Main User Types

#### 1. Administrators

- Full control over the system
    
- Can change system settings
    
- Install/uninstall software
    
- Manage user accounts
    
- Modify sensitive system files
    
- Should be given only to trusted users
    

#### 2. Standard Users

- Basic system usage permissions
    
- Can run programs and edit files
    
- Cannot change system settings
    
- Cannot install/uninstall programs
    
- Cannot manage other accounts
    
- Helps maintain system security
    

#### Other User Types

- **Guest:** Temporary user with very limited access
    
- **Assigned Access:** Restricted user for specific applications
    

## Managing User Accounts

Accounts can be managed using **Local Users and Groups**:

Steps:

1. Open Start Menu
    
2. Search **PowerShell** and open it
    
3. Type:
    

```
lusrmgr
```

4. Manage users and groups from the window
    

You can:

- Change account types
    
- Enable/disable accounts
    
- Edit user properties
    

---

## User Account Control (UAC)

**UAC (User Account Control)** is a Windows security feature that asks for user confirmation before performing actions that require administrative privileges.

### Purpose

- Prevent unauthorized system changes
    
- Protect against malware installation
    
- Reduce accidental system damage
    

### How It Works

When a program tries to:

- Install software
    
- Change system settings
    
- Modify protected files
    

➡ UAC prompts user to **Allow or Deny**.

### UAC Levels (High → Low)

1. **Always Notify** – Most secure
    
2. **Notify for programs only (Default)** – Balanced security
    
3. **Notify without dim desktop** – Less secure
    
4. **Never Notify** – UAC disabled (Unsafe)
    

### Advantages

- Improves system security
    
- Prevents unauthorized changes
    
- User controls admin actions
    

### Disadvantages

- Frequent prompts can be annoying
    
- Some apps may not work properly
    

### One-Line Summary

> UAC protects Windows by requiring user approval before executing administrative actions.

---

## Microsoft Windows — Overview

**Microsoft Windows** is a widely used operating system for personal and corporate computers and a major target for malware and attackers.

### Windows History (Timeline)

- **1985 – Windows 1.0:** GUI over MS-DOS, low success
    
- **1987 – Windows 2.0:** Word & Excel increased adoption
    
- **1990 – Windows 3.0:** First major success
    
- **2001 – Windows XP:** Merged NT + DOS lines, very popular
    
- **2006 – Vista:** Innovations but poor adoption
    
- **2009 – Windows 7:** Stable successor
    
- **2012 – Windows 8.x:** Short lifespan
    
- **2015 – Windows 10:** Widely adopted
    
- **2021+ – Windows 11:** Current version
    
- **Server version:** Windows Server 2025
    

👉 Training focuses on **Windows 10** due to popularity.

### Accessing Windows

#### Local Access

- Physical access to the computer
    
- Login using local credentials
    
#### Remote Access

- Uses **RDP (Remote Desktop Protocol)**
    
- Allows remote control over network
    
- Example client: **Remmina**
    
### Windows Interface

Windows interface enables users to manage programs, files, and settings.

#### Main Components

- **Desktop:** Main working area
    
- **Start Menu:** Access apps & system tools
    
- **Search Box:** Find files, apps, settings
    
- **Taskbar:** Shows running apps & notifications
    
### One-Line Summary

> Windows is a GUI-based operating system with a long evolution, widely used in home and enterprise environments, and commonly accessed locally or via RDP.

---

