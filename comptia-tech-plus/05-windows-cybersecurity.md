# 05 - Windows Cybersecurity

## 1. Introduction to Windows Security

Windows includes built-in security features that help protect computers, user accounts, files, applications, and network connections.

Organizations also use administrative tools and security policies to manage many Windows computers consistently.

### Main Security Goals

The CIA triad describes three important security objectives:

- Confidentiality: Information is accessible only to authorized people.
- Integrity: Information remains accurate and is not changed without authorization.
- Availability: Systems and information remain accessible when needed.

Example:
A company protects employee records with access permissions (confidentiality), change controls (integrity), and reliable backups (availability).

## 2. Microsoft Defender Antivirus

Microsoft Defender Antivirus is a built-in Windows security feature that helps detect, block, and remove malicious software.

It can help protect against threats such as:
- Viruses
- Trojans
- Spyware
- Ransomware-related threats
- Other potentially malicious files and activity

### Important Features

- Real-time protection: Checks files and activity for threats as they occur.
- Security intelligence updates: Provides updated information used to detect threats.
- Scans: Checks files and system locations for malicious software.
- Threat history: Shows detected threats and relevant actions.

### Good Security Practices

- Keep protection enabled.
- Install security intelligence updates.
- Investigate security alerts rather than ignoring them.
- Avoid opening unexpected attachments or running unknown downloads.

Antivirus software is only one layer of defense. It does not guarantee that a computer is free of threats.

## 3. Windows Firewall

A firewall controls network traffic according to configured rules.

Windows Defender Firewall helps restrict unauthorized network connections to and from a Windows computer.

### Key Concepts

- Inbound traffic: Network traffic coming into a computer.
- Outbound traffic: Network traffic leaving a computer.
- Firewall rule: A rule that allows or blocks specified traffic.
- Network profile: A classification such as Domain, Private, or Public.

### Windows Network Profiles

| Profile | Typical Context |
|---|---|
| Domain | A computer connected to a recognized organization domain network |
| Private | A trusted home or small-office network |
| Public | An untrusted network, such as public Wi-Fi |

Windows applies firewall settings according to the active profile and its rules.

### Example

A laptop connects to public Wi-Fi in a café.

A suitable firewall configuration helps restrict unwanted inbound connections from other devices on that network.

### Exam Tip

A firewall filters network traffic. Antivirus focuses on detecting malicious software and related threats. They serve different purposes and work best as part of a layered security approach.

## 4. User Account Control (UAC)

User Account Control helps prevent unauthorized changes to Windows by requesting approval or administrative credentials for certain actions that require elevated privileges.

Examples include:
- Installing some applications.
- Changing protected system settings.
- Performing administrative tasks.

### Standard User vs. Administrator

| Account Type | Typical Capabilities |
|---|---|
| Standard user | Performs everyday tasks with limited privileges |
| Administrator | Can perform system-wide administrative tasks |

Using a standard account for everyday work can reduce the impact of some malicious activity.

UAC is not a replacement for least privilege, antivirus, firewall rules, or other security controls.

## 5. BitLocker Drive Encryption

BitLocker is a Windows drive-encryption feature available in supported Windows editions and configurations.

It helps protect data if a computer or storage device is lost or stolen.

### Why Encryption Matters

Without effective encryption, someone with physical access to a storage device may be able to access its contents through another operating system or recovery method.

Drive encryption helps protect stored data from unauthorized access.

### Important Concepts

- Encryption: Transforms readable information into a protected form.
- Decryption: Converts protected information back into readable form.
- Recovery key: A key used to regain access in certain recovery situations.
- TPM: Trusted Platform Module, a hardware security component that can help protect encryption keys.

### Best Practices

- Follow organizational encryption policies.
- Store recovery keys securely.
- Verify recovery arrangements before changing hardware or firmware.
- Never share recovery keys publicly.

BitLocker availability and management options depend on Windows edition, hardware, and organizational configuration.

## 6. Windows Update and Patch Management

Windows Update delivers operating system updates, including security fixes, reliability improvements, and other updates.

A vulnerability is a weakness that could be exploited to affect a system's security.

A security patch corrects a known vulnerability or other software problem.

### Why Updates Matter

- Fix known security weaknesses.
- Improve system stability.
- Reduce exposure to publicly known vulnerabilities.
- Help maintain supported software.

### Example

A security advisory identifies a vulnerability in a Windows component. Installing the applicable security update can reduce the risk of exploitation.

### Organizational Patch Management

Businesses may test updates before deployment, schedule maintenance windows, track patch status, and prioritize urgent security fixes.

Updates should be managed promptly according to risk and organizational policy.

## 7. Group Policy

Group Policy is a Windows administrative technology used to manage configuration settings for users and computers.

It is commonly used in Windows domain environments through Active Directory Domain Services.

### Examples of Group Policy Settings

- Password and account policies.
- Screen-lock requirements.
- Windows security configuration.
- Application restrictions.
- Windows Firewall settings.
- Access to certain system features.

### Why Group Policy Is Useful

Instead of configuring every computer manually, administrators can apply consistent settings to many users and devices.

### Local Group Policy Editor

On supported Windows editions, administrators can open the Local Group Policy Editor by running:

`gpedit.msc`

Not every Windows edition includes this editor.

## 8. Active Directory

Active Directory Domain Services (AD DS) is a Microsoft directory service used in traditional Windows domain environments.

It helps organizations centrally manage users, computers, groups, authentication, and access to domain resources.

### Key Concepts

| Term | Meaning |
|---|---|
| Domain | A managed collection of directory objects under a shared administrative structure |
| Domain Controller | A server running AD DS that authenticates users and manages directory services |
| User Account | An identity used to access resources |
| Security Group | A collection of accounts used to manage permissions |
| Organizational Unit (OU) | A container used to organize directory objects and delegate administration |
| Group Policy | A way to apply configuration settings to users and computers |

### Example

An employee signs in to a company-managed Windows computer using a domain account.

Active Directory can help authenticate the employee and provide access according to assigned groups and policies.

### Active Directory and Microsoft Entra ID

These are related but different technologies.

- Active Directory Domain Services is traditionally used for on-premises Windows domain environments.
- Microsoft Entra ID is Microsoft's cloud identity and access management service.

They can be integrated, but they are not interchangeable names for the same system.

## 9. Least Privilege and Defense in Depth

### Principle of Least Privilege

Users and applications should receive only the permissions required to perform their tasks.

Example:
An employee who only needs to read a report should not automatically receive permission to change or delete it.

### Defense in Depth

Defense in depth uses multiple security controls so that the failure of one control does not necessarily lead to a successful attack.

Examples:
- Antivirus
- Firewall
- Strong authentication
- Regular patching
- Least-privilege accounts
- Drive encryption
- Backups and monitoring

No single control can prevent every attack.

## 10. Basic Windows Security Checks

You can use these built-in tools to inspect aspects of Windows security.

### Open Windows Security

Use the Start menu to search for Windows Security.

Review the available sections, including virus protection and firewall settings.

### View Running Services

```powershell
Get-Service
```

This lists Windows services. Do not disable unfamiliar services without understanding their purpose.

### View Installed Hotfixes

```powershell
Get-HotFix
```

This displays information about installed Windows hotfixes. It is not a complete inventory of every update mechanism or component version.

### View Local User Accounts

```powershell
Get-LocalUser
```

This lists local user accounts on supported Windows systems. Domain accounts are managed separately.

### Security Reminder

Use inspection commands on systems you own or are authorized to administer. Avoid changing security settings on managed devices without approval.

## 11. Practice Questions

### Question 1

What is the main purpose of Windows Defender Antivirus?

A. Manage file permissions only  
B. Help detect and block malicious software  
C. Replace Windows Update  
D. Assign IP addresses  

### Question 2

What does Windows Defender Firewall primarily do?

A. Encrypt every file on the computer  
B. Filter network traffic according to rules  
C. Install all software automatically  
D. Manage user documents  

### Question 3

What is the purpose of UAC?

A. Help prevent unauthorized system changes through approval or credential prompts  
B. Encrypt network packets  
C. Replace administrator accounts  
D. Create virtual machines  

### Question 4

Which Windows feature can encrypt supported drives?

A. Task Manager  
B. BitLocker  
C. File Explorer  
D. Notepad  

### Question 5

Why are security updates important?

A. They remove the need for backups  
B. They can fix known vulnerabilities  
C. They guarantee that malware cannot run  
D. They disable all network connections  

### Question 6

What is a common use of Group Policy?

A. Centrally apply configuration settings to users and computers  
B. Replace the computer's processor  
C. Recover every deleted file  
D. Increase physical RAM  

### Question 7

What is a domain controller in a traditional Active Directory environment?

A. A network cable  
B. A server that provides directory and authentication services  
C. A type of firewall rule  
D. A file extension  

### Question 8

What does least privilege mean?

A. Give every employee administrator access  
B. Give users only the permissions they need  
C. Disable all security tools  
D. Share every password with the IT team  

### Question 9

What is the main purpose of BitLocker recovery information?

A. To improve CPU performance  
B. To help regain access to an encrypted drive in certain recovery situations  
C. To replace all account passwords  
D. To disable encryption permanently  

### Question 10

Which security approach combines multiple controls to reduce risk?

A. Defense in depth  
B. Single-factor access for every system  
C. Disabling updates  
D. Shared administrator accounts  

## Answers and Explanations

1. B - Defender Antivirus helps detect and block malicious software.
2. B - A firewall filters network traffic according to configured rules.
3. A - UAC prompts for approval or credentials for certain elevated actions.
4. B - BitLocker encrypts supported drives.
5. B - Security updates can correct known software vulnerabilities.
6. A - Group Policy helps centrally manage Windows configuration.
7. B - A domain controller provides AD DS directory and authentication services.
8. B - Least privilege limits access to what is necessary.
9. B - Recovery information can help restore access in certain situations.
10. A - Defense in depth combines multiple layers of protection.

## Revision Checklist

- [ ] Explain the CIA triad.
- [ ] Describe Microsoft Defender Antivirus.
- [ ] Explain the purpose of Windows Firewall.
- [ ] Distinguish standard users from administrators.
- [ ] Explain UAC.
- [ ] Describe BitLocker and recovery keys.
- [ ] Explain why patch management matters.
- [ ] Define Group Policy.
- [ ] Explain Active Directory and domain controllers.
- [ ] Distinguish AD DS from Microsoft Entra ID.
- [ ] Apply least privilege and defense in depth.

## Further Reading

- [CompTIA Tech+ Certification](https://www.comptia.org/certifications/tech)
- [Microsoft Windows Security](https://learn.microsoft.com/windows/security/)
- [Microsoft Defender Antivirus](https://learn.microsoft.com/defender-endpoint/microsoft-defender-antivirus)
- [Windows Firewall](https://learn.microsoft.com/windows/security/operating-system-security/network-security/windows-firewall/)
- [BitLocker Overview](https://learn.microsoft.com/windows/security/operating-system-security/data-protection/bitlocker/)
- [Active Directory Domain Services](https://learn.microsoft.com/windows-server/identity/ad-ds/)
