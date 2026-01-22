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

