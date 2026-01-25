## CMD vs PowerShell

**CMD** and **PowerShell** are Windows command-line interfaces, but PowerShell is more powerful and modern.

### Command Prompt (CMD)

- Based on **MS-DOS**
    
- Simple command syntax
    
- Used for basic commands & batch files
    
- Limited scripting capability
    
- Weak for automation & security
    
- Mainly kept for **backward compatibility**
    

### PowerShell

- Modern CLI + scripting language
    
- Uses **cmdlets** (action-based commands)
    
- **Object-oriented** (works with objects, not just text)
    
- Strong automation capabilities
    
- Supports advanced scripting (*.ps1)
    
- Includes security features:
    
    - Execution policies
        
    - Script signing
        
- Actively developed by Microsoft
    
- Backward compatible with CMD
    

### Key Difference

> CMD processes text, PowerShell processes objects.

### Recommendation

PowerShell is the preferred tool for **Windows administration, automation, and security tasks**.

---

## PowerShell Installation

Modern Windows systems already include PowerShell. Installation is mainly required for updates or non-Windows systems.

### Windows (Recommended: WinGet)

**WinGet** is Microsoft’s package manager for Windows 10/11 used to install, update, and manage software via CLI.

#### Search PowerShell

```
winget search Microsoft.PowerShell
```

#### Install PowerShell

```
winget install --id Microsoft.PowerShell --source winget
```

### Linux (Ubuntu)

Install PowerShell via Snap:

```
sudo snap install powershell --classic
```

### macOS

Install using Homebrew:

```
brew install powershell/tap/powershell
```

### Key Point

> WinGet, Snap, and Homebrew provide easy, secure, command-line installation of PowerShell across platforms.


---

## Introduction to CMD (Basic Commands)

CMD is a text-based interface used to navigate and manage files and folders in Windows.

### `dir`

- Lists files and directories in the current location
    
- Shows file size, timestamps, and free disk space
    

```
dir
```

### `cd`

- Changes current directory
    
- `.` = current directory
    
- `..` = parent directory
    

```
cd Documents
```

### `mkdir`

- Creates a new directory
    

```
mkdir newdir
```

### `rmdir`

- Deletes an **empty** directory
    

```
rmdir newdir
```

### `copy`

- Copies files
    

```
copy test.txt test1.txt
```

### `move`

- Moves or renames files/directories
    

```
move test.txt ..\Desktop
```

### `del`

- Deletes files
    

```
del test1.txt
```

### Key Concept

> CMD commands mainly perform basic file and directory operations.

### Transition Note

After learning basic CMD commands, we move to **PowerShell**, which offers advanced automation and object-based command handling.

---

## Introduction to PowerShell

PowerShell is a powerful command-line interface and scripting environment used for Windows management and automation.

### PowerShell Interfaces

- **Windows PowerShell:** Standard CLI
    
- **PowerShell ISE:** GUI-based environment for writing, testing, and debugging scripts
    

### First Command

Check PowerShell version:

```
$PSVersionTable
```

Displays version, build, edition, and remoting details.

### Cmdlets

- PowerShell commands are called **cmdlets**
    
- Naming format: **Verb-Noun**
    
    - Example:
        
        - `Get-Process`
            
        - `Get-Service`
            

### Getting Help

#### Get-Help

- Displays help for cmdlets
    

```
Get-Help Get-Help
```

Shortcut:

```
<command> -?
```

#### Get-Command

- Lists all available commands, cmdlets, scripts, and functions
    

```
Get-Command
```

Detailed help:

```
Get-Help -Name Get-Command -Detailed
```

👉 **Get-Help + Get-Command = ~80% PowerShell learning**

### Update-Help

- Updates help documentation
    
- Requires admin privileges
    

```
Update-Help
```

### Aliases

- Shortcuts for cmdlets
    
- Useful for CMD/Linux users
    

Example:

```
cd → Set-Location
```

View aliases:

```
alias
alias cd
```

### Tab Completion

- Press **Tab** to auto-complete commands/paths
    
- Cycles through options with repeated Tab presses
    

Example:

```
Set-Location do<TAB>
```

### One-Line Summary

> PowerShell uses cmdlets, built-in help, aliases, and tab completion to provide powerful and efficient system management.

---

## PowerShell Basic Usage

## File & Directory Basics

- `.` → current directory
    
- `..` → parent directory
    

---

## File & Directory Cmdlets

### Get-ChildItem (`ls`)

- Lists files and directories
    

```
Get-ChildItem
```

---

### Set-Location (`cd`)

- Changes working directory
    

```
Set-Location .\Documents\
```

---

### New-Item

- Creates files or directories
    
- Default → empty file
    

```
New-Item file.txt
New-Item -ItemType Directory logs
```

Help:

```
Get-Help New-Item -Examples
```

---

### Remove-Item (`rm`)

- Deletes files or directories
    

```
Remove-Item .\logs\
```

---

### Copy-Item (`cp`)

- Copies files or directories
    

```
Copy-Item file.txt file1.txt
```

---

### Move-Item (`mv`)

- Moves or renames items
    

```
Move-Item file1.txt ..\Desktop\
Move-Item ..\Desktop\file1.txt file01.txt
```

---

### Get-Content (`cat`)

- Displays file contents
    

```
Get-Content file.txt
```

---

## Processes & Services

#### Get-Process

- Lists running processes
    
- Supports filtering
    

```
Get-Process
Get-Process -Name win*
```

#### Stop-Process

- Terminates process by name or ID
    

```
Stop-Process -Id 5432
```

#### Get-Service

- Lists system services
    

```
Get-Service
```

#### Start-Service / Stop-Service

- Controls service state
    

```
Start-Service -Name Appinfo
Stop-Service -Name Appinfo
```

## Object Selection & Filtering

### Piping (`|`)

- Sends output of one command to another
    

```
Get-Process | Select-Object ProcessName, Id
```

#### Select-Object (`select`)

- Displays selected object properties
    

```
Select-Object ProcessName, Id
```

#### Where-Object (`where`)

- Filters objects based on conditions
    

```
Get-Service | Where-Object Status -eq "Running"
```

Common operators:

- `-eq` equal
    
- `-ne` not equal
    
- `-gt / -ge` greater
    
- `-lt / -le` less
    
#### Select-String

- Searches text using words or regex
    

```
Select-String -Pattern "today" file.txt
```

### Core PowerShell Concept

> PowerShell pipelines pass **objects**, not text — enabling powerful filtering and automation.

---

## User Management with PowerShell

PowerShell allows managing **users, groups, passwords, and permissions** on local machines and Active Directory (AD).

### Active Directory (AD) Overview

- Centralized directory service (Windows Server)
    
- Manages users, computers, groups, printers, apps
    
- Enforces:
    
    - Password policies
        
    - Access control
        
    - Group Policies (GPOs)
        
- Scales from small to enterprise networks
    

### RSAT (Remote Server Administration Tools)

- Enables remote Windows Server management
    
- Provides GUI tools + PowerShell cmdlets
    
- Required for AD cmdlets on client machines
    

#### RSAT Installation

```
Settings → Apps → Optional features → Add feature → RSAT → Install
```

### Why User & Group Enumeration Matters

- Detect excessive privileges
    
- Identify misconfigurations
    
- Find unauthorized group members
    

⚠ Requires **Administrator privileges**

## Local User Management

#### Get-LocalUser

- Lists local users
    

```
Get-LocalUser
```

#### New-LocalUser

- Creates local user
    

```
New-LocalUser -Name "j.doe" -Password (ConvertTo-SecureString "password123" -AsPlainText -Force)
```

#### Set-LocalUser

- Modifies user properties
    

```
Set-LocalUser -Name "j.doe" -Description "Test user"
```

#### Disable / Enable User

```
Disable-LocalUser -Name "j.doe"
Enable-LocalUser -Name "j.doe"
```

#### Remove-LocalUser

```
Remove-LocalUser -Name "j.doe"
```

## Local Group Management

#### Get-LocalGroup

```
Get-LocalGroup
```

#### New-LocalGroup

```
New-LocalGroup -Name "Students"
```

#### Set-LocalGroup

```
Set-LocalGroup -Name "Students" -Description "Improvise. Adapt. Overcome."
```

#### Add / Remove Group Members

```
Add-LocalGroupMember -Group "Students" -Member "j.doe"
Remove-LocalGroupMember -Group "Students" -Member "j.doe"
```

#### Remove-LocalGroup

```
Remove-LocalGroup -Name "Students"
```

## Active Directory User Management

#### Get-ADUser

```
Get-ADUser "j.doe"
Get-ADUser -Filter *
```

#### New-ADUser

```
New-ADUser -Name "j.doe" -SamAccountName j.doe -AccountPassword (ConvertTo-SecureString "sifre123!" -AsPlainText -Force)
```

#### Set-ADUser

```
Set-ADUser -Identity "j.doe" -Surname "doe"
```

#### Remove-ADUser

```
Remove-ADUser "j.doe"
```

## Active Directory Group Management

#### Get-ADGroup

```
Get-ADGroup "Students"
Get-ADGroup -Filter *
```

#### New-ADGroup

```
New-ADGroup -Name "Students" -GroupScope Universal
```

#### Set-ADGroup

```
Set-ADGroup -Identity "Students" -Description "Learn as if you were to live forever"
```

#### Group Membership

```
Get-ADGroupMember -Identity "Students"
Add-ADGroupMember -Identity "Students" -Members j.doe
Remove-ADGroupMember -Identity "Students" -Member j.doe
```

#### Remove-ADGroup

```
Remove-ADGroup "Students"
```

### Core Security Insight

> User and group misconfigurations are one of the **most exploited attack vectors** in Windows environments.

---

## PowerShell & Network Connections

PowerShell provides cmdlets and legacy tools to view, test, and manage network configurations.

### Gathering Network Information

#### Get-NetIPAddress

- Displays IP configuration of network interfaces
    

```
Get-NetIPAddress
```

#### IPConfig (Legacy CMD Tool)

- Shows IP address, subnet mask, gateway, DNS
    

```
ipconfig
```

### Viewing Network Connections

#### Netstat

- Displays active network connections
    
- Shows protocol, local/remote address, state
    

```
netstat
```

### DNS Queries

#### Nslookup

- Resolves domain names to IP addresses
    

```
nslookup example.com
```

### ARP Cache

#### ARP

- Maps IP addresses to MAC addresses
    
- Displays ARP table
    

```
arp -a
```

### Testing Connectivity

#### Test-NetConnection

- Tests network connectivity (ping & port checks)
    

```
Test-NetConnection
```

### Downloading Files

#### Invoke-WebRequest

- Sends HTTP/HTTPS requests
    
- Downloads web content
    

```
Invoke-WebRequest -Uri "<URL>" -OutFile "file.ext"
```

Example:

```
Invoke-WebRequest -Uri "https://upload.wikimedia.org/...png" -OutFile "powershell.png"
```

### Core Security Insight

> Network commands are heavily used in **enumeration, troubleshooting, and attacker reconnaissance**.

---

## Retrieving Information with PowerShell

PowerShell is used to enumerate **system, update, security, and file information**.

### System Information

#### Get-ComputerInfo

- Displays OS, hardware, BIOS, and system details
    

```
Get-ComputerInfo
```

#### WMI – win32_OperatingSystem

- Retrieves OS details via WMI
    
- Useful for system replication & testing
    

```
Get-WmiObject -Class win32_OperatingSystem
```

### Installed Updates

#### Get-Hotfix

- Lists installed Windows updates (KBs)
    

```
Get-Hotfix
```

### Defender Information

- Displays Defender-related services
    

```
Get-Service | Where-Object DisplayName -like '*Defender*'
```

## File Information

### Searching Text in Files

- Searches recursively for text patterns
    

```
Get-ChildItem -Recurse *.* | Select-String -Pattern "SEARCH_STR"
```

### File Permissions (ACL)

- Displays file/folder access rights
    

```
Get-Acl file.txt
```

### File Hashes

- Generates file hash for integrity checking
    

```
Get-FileHash file.txt
```

### Core Security Insight

> System, update, and permission enumeration is a **critical step in privilege escalation and attack planning**.

---

## PowerShell Scripting

### PowerShell ISE

- GUI-based PowerShell environment
    
- Used to **write, run, test, and debug scripts**
    
- Ideal for beginners and scripting
    

### PowerShell Scripts

- Text files with **.ps1** extension
    
- Used for **automation**
    

#### Common Use Cases

- System management (users, files, disks)
    
- Network configuration
    
- Data processing & reporting
    
- Software deployment & testing
    

### Control Structures

#### Variables

- Store and manipulate data
    

```
$name = "John Doe"
$age = 30
$firstName, $lastName = "John", "Doe"
```

#### Conditions

##### If–Else

```
if ($age -gt 18) { "Adult" } else { "Kid" }
```

##### Switch–Case

- Used for multiple conditions
    

```
switch ($dayOfWeek) { "Monday" { ... } Default { ... } }
```

### Loops

#### For

```
for ($i=1; $i -le 10; $i++) { $i }
```

#### While

```
while ($i -le 10) { $i; $i++ }
```

#### Do-While

```
do { $i; $i++ } while ($i -le 10)
```

#### Foreach

```
foreach ($name in $names) { $name }
```

### Writing & Saving Scripts

- Write scripts in **PowerShell ISE**
    
- Save as **.ps1** file
    
- Execute after setting execution policy
    

## PowerShell Gallery

- Central repository for PowerShell modules
    
- Contains Microsoft + community scripts
    
- Use with caution (security risk)
    

### Searching Modules

```
Find-Module -Name SysInternals
```

### Installing Modules

```
Install-Module -Name SysInternals
```

(NuGet may be installed automatically)

### Core Security Insight

> PowerShell scripts are powerful automation tools and are **commonly abused by attackers for living-off-the-land attacks**.

---

`Now here we are done with the windows fundamentals section and hence the OS Fundamentals module.
