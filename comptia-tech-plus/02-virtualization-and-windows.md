# 02 - Virtualization and Windows

## 1. What Is Virtualization?

Virtualization is a technology that allows one physical computer to run multiple virtual computing environments.

Each virtual machine (VM) can run its own operating system and applications.

### Why Is Virtualization Useful?

- Run different operating systems on one computer.
- Test software in an isolated environment.
- Practice system administration and cybersecurity.
- Create test environments without buying additional hardware.
- Restore a virtual machine to a previous state using a snapshot.

## 2. Virtual Machines (VMs)

A virtual machine is a software-based computer that uses resources from a physical host.

A VM can have its own:
- Operating system
- Virtual CPU
- Virtual RAM
- Virtual disk
- Virtual network adapter

### Host vs. Guest

| Term | Meaning | Example |
|---|---|---|
| Host machine | Physical computer running the virtualization environment | Laptop running Windows 11 |
| Host OS | Operating system running on the physical computer, if applicable | Windows 11 |
| Guest OS | Operating system inside the VM | Ubuntu Linux |
| Virtual disk | File or storage volume representing a VM's disk | VirtualBox VDI file |
| Snapshot | Saved state of a VM at a particular point | Snapshot before installing software |

Example:

A laptop runs Windows 11 and VirtualBox. Inside VirtualBox, you run Ubuntu Linux.

- Host OS: Windows 11
- Guest OS: Ubuntu Linux
- Hypervisor software: VirtualBox

## 3. Hypervisors

A hypervisor creates and manages virtual machines.

### Type 1 Hypervisor

Runs directly on the physical hardware.

Examples:
- Microsoft Hyper-V in its bare-metal deployment model
- VMware ESXi

Commonly used in server and enterprise environments.

### Type 2 Hypervisor

Runs as an application on an existing operating system.

Examples:
- Oracle VirtualBox
- VMware Workstation

Commonly used for learning, development, and testing.

| Feature | Type 1 | Type 2 |
|---|---|---|
| Runs on | Physical hardware | Host operating system |
| Common environment | Servers and data centers | Desktops and laptops |
| Example | VMware ESXi | VirtualBox |

## 4. Virtual Machine Isolation and Snapshots

### Isolation

Virtualization separates guest environments from one another and from the host to help limit the impact of failures or activity inside a VM.

Isolation is not an absolute security guarantee. Misconfiguration, vulnerabilities, or shared resources can create risks.

### Snapshots

A snapshot records a VM's state so you can return to it later.

Example workflow:
1. Create a clean VM.
2. Take a snapshot.
3. Install software for a lab.
4. Test the software.
5. Revert to the snapshot if necessary.

A snapshot is not necessarily a full independent backup. Keep separate backups of important data.

## 5. Introduction to the Windows 11 GUI

A graphical user interface (GUI) lets users interact with the operating system through visual elements.

### Desktop

The main workspace after signing in.

### Start Menu

Used to launch applications, search, access account options, and find power controls.

### Taskbar

Provides access to pinned applications, open windows, and system tray icons.

### File Explorer

Used to browse and manage:
- Files and folders
- Internal and external drives
- Network locations
- File properties

### Settings

Used to configure display, network, accounts, Bluetooth, updates, privacy, and other operating system options.

## 6. Useful Windows Keyboard Shortcuts

| Shortcut | Function |
|---|---|
| Win + E | Open File Explorer |
| Win + I | Open Settings |
| Win + L | Lock the computer |
| Win + R | Open the Run dialog |
| Win + X | Open the Quick Link menu |
| Alt + Tab | Switch between open windows |
| Ctrl + Shift + Esc | Open Task Manager |
| Win + Shift + S | Capture a screen region |

## 7. Task Manager

Task Manager helps you monitor applications, processes, and system resource usage.

Important resources:

- CPU: Processes instructions and performs calculations.
- Memory (RAM): Stores data and programs currently in use.
- Disk: Shows storage activity.
- Network: Shows network activity for applications and processes.

### Example Scenario

Your computer becomes slow.

1. Open Task Manager using Ctrl + Shift + Esc.
2. Review CPU and memory usage.
3. Identify applications consuming unusually high resources.
4. Investigate the cause before ending a task.

Do not terminate unfamiliar system processes without understanding their purpose.

## 8. Device Manager and Windows Tools

### Device Manager

Displays installed hardware and allows you to inspect device status and manage drivers.

Use it when:
- A device is not working correctly.
- A driver is missing or outdated.
- A device displays a warning symbol.

### Windows Update

Provides operating system updates, including security patches.

### Windows Security

Provides access to built-in security features such as Microsoft Defender Antivirus and firewall settings.

### User Account Control (UAC)

Helps prevent unauthorized changes by requesting approval or administrative credentials for certain actions requiring elevated privileges.

## 9. Virtualization vs. Physical Computers

| Feature | Physical Computer | Virtual Machine |
|---|---|---|
| Hardware | Uses physical hardware directly through the OS | Uses virtual hardware provided by the virtualization platform |
| Resources | Limited by installed hardware | Shares host resources with other workloads |
| Setup | May require physical installation and configuration | Can often be created from a VM template or installation image |
| Recovery | Depends on backup and recovery methods | May support snapshots and VM backups |
| Common use | Everyday computing | Testing, labs, servers, and development |

## 10. Practice Questions

### Question 1
What is the main purpose of a hypervisor?

A. Encrypt files  
B. Create and manage virtual machines  
C. Edit documents  
D. Manage Windows user passwords only  

### Question 2
Windows 11 is installed on a laptop, and Ubuntu runs inside VirtualBox. What is Ubuntu?

A. Host OS  
B. Guest OS  
C. Hypervisor  
D. Device driver  

### Question 3
Which is an example of a Type 2 hypervisor?

A. Oracle VirtualBox  
B. A physical CPU  
C. Windows File Explorer  
D. NTFS  

### Question 4
Which Windows shortcut opens Task Manager directly?

A. Win + E  
B. Win + I  
C. Ctrl + Shift + Esc  
D. Win + L  

### Question 5
Which tool helps investigate a hardware driver problem?

A. File Explorer  
B. Device Manager  
C. Start Menu  
D. Recycle Bin  

### Question 6
What is a VM snapshot primarily used for?

A. Increasing physical RAM  
B. Recording a VM state for later restoration  
C. Replacing the hypervisor  
D. Permanently preventing malware  

### Question 7
Which tool is used to configure Windows network and display settings?

A. Settings  
B. Task Manager only  
C. Recycle Bin  
D. Disk Cleanup only  

### Question 8
What is one purpose of virtualization isolation?

A. To guarantee that attacks are impossible  
B. To help separate virtual environments  
C. To remove the need for security updates  
D. To eliminate all hardware requirements  

## Answers and Explanations

1. B - A hypervisor creates and manages VMs.
2. B - Ubuntu is running inside the VM, so it is the guest OS.
3. A - VirtualBox runs as an application on a host OS.
4. C - Ctrl + Shift + Esc opens Task Manager.
5. B - Device Manager helps inspect hardware and drivers.
6. B - A snapshot records a VM state for later restoration.
7. A - Windows Settings provides system configuration options.
8. B - Isolation helps separate environments but does not guarantee perfect security.

## Revision Checklist

- [ ] Explain virtualization and virtual machines.
- [ ] Distinguish host OS from guest OS.
- [ ] Distinguish Type 1 from Type 2 hypervisors.
- [ ] Explain isolation and snapshots.
- [ ] Identify Windows 11 GUI components.
- [ ] Memorize important keyboard shortcuts.
- [ ] Use Task Manager to inspect resource usage.
- [ ] Explain the purpose of Device Manager.
- [ ] Understand Windows Update, Windows Security, and UAC.

## Further Reading

- [CompTIA Tech+ Certification](https://www.comptia.org/certifications/tech)
- [Microsoft Learn](https://learn.microsoft.com/)
- [VirtualBox Documentation](https://www.virtualbox.org/wiki/Documentation)
- [Microsoft Hyper-V Documentation](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/)
