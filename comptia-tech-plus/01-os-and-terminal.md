# 01 - Introduction to Operating Systems and Terminal

## 1. What Is an Operating System?

An operating system (OS) is system software that manages computer hardware and provides services for applications.

### Main responsibilities

- Process management: controls running programs.
- Memory management: allocates and manages RAM.
- File management: organizes files and directories.
- Device management: coordinates hardware through drivers.
- Security: manages accounts, permissions, and access.
- User interface: allows users to interact with the computer.

### Examples of operating systems

| Operating System | Common Use |
|---|---|
| Windows | Personal computers and business environments |
| Linux | Servers, cloud systems, and security labs |
| macOS | Apple Mac computers |
| Android | Mobile devices |
| iOS | Apple iPhones |

## 2. GUI vs. CLI

### GUI - Graphical User Interface

A GUI uses visual elements such as windows, icons, menus, and buttons.

Example: Opening File Explorer and clicking a folder.

### CLI - Command-Line Interface

A CLI accepts text commands to perform tasks.

Examples include PowerShell, Command Prompt, and the Linux shell.

| Feature | GUI | CLI |
|---|---|---|
| Interaction | Visual elements | Text commands |
| Ease of learning | Often easier for beginners | Requires command knowledge |
| Automation | Possible | Well suited to scripting |
| Example | File Explorer | PowerShell |

## 3. Essential Windows Terminal Commands

### Navigation

```powershell
pwd
Get-Location
Get-ChildItem
Set-Location C:\Users
```

- `Get-Location`: displays the current directory.
- `Get-ChildItem`: lists files and directories.
- `Set-Location`: changes the current directory.
- `pwd`: displays the current location in PowerShell.

### File and directory management

```powershell
New-Item -ItemType Directory -Name TestFolder
New-Item -ItemType File -Name notes.txt
Get-Content notes.txt
Copy-Item notes.txt notes-backup.txt
Move-Item notes.txt notes-renamed.txt
Remove-Item notes-renamed.txt
```

Be careful with deletion commands. Check the target path before removing files.

### System information

```powershell
Get-ComputerInfo
Get-Process
Get-Service
ipconfig
```

- `Get-ComputerInfo`: displays computer information.
- `Get-Process`: lists running processes.
- `Get-Service`: lists Windows services.
- `ipconfig`: displays network configuration.

## 4. Files, Folders, and Paths

A file stores information. A directory, commonly called a folder, organizes files and other directories.

Example of an absolute Windows path:

`C:\Users\Student\Documents\notes.txt`

- `C:\` is the drive.
- `Users\Student\Documents` is the directory path.
- `notes.txt` is the file name.

An absolute path identifies a location from the root of a drive. A relative path identifies a location in relation to the current directory.

## 5. Processes and Services

A process is a running instance of a program.

A service is a background component that provides an operating system or application function.

Useful commands:

```powershell
Get-Process
Get-Service
```

Use Task Manager to inspect applications and resource usage. Do not terminate unfamiliar system processes without understanding their purpose.

## 6. Important Exam Terms

| Term | Definition |
|---|---|
| Operating system | Software that manages hardware and provides application services |
| GUI | Graphical user interface |
| CLI | Command-line interface |
| Process | A running instance of a program |
| Service | A background component providing a function |
| RAM | Volatile memory used by active programs and data |
| Driver | Software that enables communication between the OS and hardware |
| Directory | A location used to organize files |

## 7. Practice Questions

### Question 1
Which component manages computer hardware and provides services to applications?

A. Web browser  
B. Operating system  
C. Text document  
D. File extension  

### Question 2
Which PowerShell command lists files and directories in the current location?

A. Get-Process  
B. Get-Service  
C. Get-ChildItem  
D. Get-ComputerInfo  

### Question 3
What is a process?

A. A physical storage device  
B. A running instance of a program  
C. A type of network cable  
D. A file permission  

### Question 4
Which interface uses typed commands?

A. GUI  
B. CLI  
C. Desktop wallpaper  
D. File Explorer only  

### Question 5
Which command displays the current location in PowerShell?

A. Get-Location  
B. Get-Service  
C. Get-Process  
D. Remove-Item  

## Answers

1. B - Operating system
2. C - Get-ChildItem
3. B - A running instance of a program
4. B - CLI
5. A - Get-Location

## Revision Checklist

- [ ] Explain the purpose of an operating system.
- [ ] Distinguish GUI from CLI.
- [ ] Navigate directories in PowerShell.
- [ ] List files and create directories.
- [ ] Explain processes, services, and drivers.
- [ ] Identify absolute and relative paths.
- [ ] Answer the practice questions without looking at the answers.

## Further Reading

- [Microsoft Learn](https://learn.microsoft.com/)
- [PowerShell Documentation](https://learn.microsoft.com/powershell/)
- [CompTIA Tech+](https://www.comptia.org/certifications/tech)
