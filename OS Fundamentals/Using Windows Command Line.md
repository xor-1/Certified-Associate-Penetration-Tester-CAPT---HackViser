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

