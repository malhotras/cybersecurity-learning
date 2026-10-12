# 09 - PowerShell Streams, Pipes, Redirection, and Execution Policy

## 1. What Is a Data Stream?

A stream is a flow of data between a program and another destination.

Command-line tools commonly use standard input, standard output, and standard error.

| Stream | File Descriptor | Purpose |
|---|---:|---|
| stdin | 0 | Receives input |
| stdout | 1 | Provides normal output |
| stderr | 2 | Provides error messages |

### Standard Input (stdin)

Standard input supplies data to a program.

It can come from:
- The keyboard
- A redirected file
- Another command through a pipe

Example in PowerShell:

```powershell
Get-Content .\names.txt
```

This reads the contents of a file. It does not automatically mean every command receives that file through stdin; PowerShell commands commonly receive pipeline objects instead.

### Standard Output (stdout)

Standard output carries normal command results.

Example:

```powershell
Get-Process
```

This displays information about running processes.

### Standard Error (stderr)

Standard error is intended for error messages and diagnostic information.

In PowerShell, errors are handled through the error stream, numbered 2.

Example:

```powershell
Get-Item C:\ThisFileDoesNotExist.txt
```

This normally produces an error because the path does not exist.

Important: PowerShell has six numbered streams:
- 1: Success
- 2: Error
- 3: Warning
- 4: Verbose
- 5: Debug
- 6: Information

The terms stdin, stdout, and stderr are standard operating-system conventions. PowerShell's numbered output streams are related concepts, but they are not identical in every implementation detail.

## 2. Output Redirection

Redirection changes where command output is sent.

Instead of displaying output in the terminal, you can save it to a file.

### Overwrite: >

In PowerShell, `>` sends success output to a file and replaces the file's existing contents.

```powershell
Get-Process > .\processes.txt
```

This saves the command's success output in `processes.txt`.

Be careful: existing contents are overwritten.

### Append: >>

The `>>` operator appends success output to the end of a file.

```powershell
Get-Date >> .\activity.log
```

This adds the date and time to the end of `activity.log` rather than replacing its contents.

### Redirect Errors

PowerShell uses `2>` to redirect the error stream.

```powershell
Get-Item C:\MissingFile.txt 2> .\errors.txt
```

The error output is written to `errors.txt`.

Use `2>>` to append errors to an existing file:

```powershell
Get-Item C:\MissingFile.txt 2>> .\errors.txt
```

### Redirect Success and Error Output Together

PowerShell can redirect errors to the same destination as success output.

```powershell
Get-ChildItem C:\ -ErrorAction Continue *> .\results.txt
```

The `*>` operator redirects all PowerShell output streams to the file, subject to the behavior of the individual command.

### Redirection Summary

| Operator | Meaning |
|---|---|
| `>` | Write success output, replacing existing file contents |
| `>>` | Append success output |
| `2>` | Write error output, replacing existing file contents |
| `2>>` | Append error output |
| `*>` | Redirect all PowerShell output streams |

## 3. The Pipe Operator (|)

A pipe sends the output of one command to another command as input.

The symbol is:

`|`

General structure:

```powershell
Command-A | Command-B
```

Command A produces output. Command B processes that output.

### Example 1: Find a Specific Process

```powershell
Get-Process | Where-Object { $_.ProcessName -like "*chrome*" }
```

How it works:
1. `Get-Process` retrieves running processes.
2. The pipe passes the process objects onward.
3. `Where-Object` filters the objects.
4. Only matching process names are returned.

The result depends on which processes are running.

### Example 2: Sort Files by Size

```powershell
Get-ChildItem -File | Sort-Object Length -Descending
```

This lists files and sorts them from largest to smallest.

### Example 3: Count Running Processes

```powershell
Get-Process | Measure-Object
```

This counts the process objects returned by `Get-Process`.

### Example 4: Find Services That Are Stopped

```powershell
Get-Service | Where-Object { $_.Status -eq "Stopped" }
```

This filters services to show those whose status is stopped. A stopped service is not automatically a problem; some services run only when needed.

## 4. The Unix Philosophy

The Unix philosophy encourages developers to build small tools that perform specific tasks and can be combined to solve larger problems.

Three key ideas are:

- Write programs that do one thing well.
- Design programs to work together.
- Use standard interfaces, including streams and pipes, to connect programs.

PowerShell follows a similar composable approach, although its pipeline usually passes structured .NET objects rather than plain text.

### Example: A Pipeline

```powershell
Get-Process |
    Sort-Object CPU -Descending |
    Select-Object -First 5
```

This pipeline:
1. Retrieves running processes.
2. Sorts them by the CPU property.
3. Selects the first five results.

Note: The CPU property is cumulative CPU time, not necessarily current CPU utilization.

## 5. Why Use Pipes Instead of Temporary Files?

Pipes are often convenient when the output of one command should immediately be processed by another.

### Efficiency

A pipeline can pass data directly between commands without requiring you to save intermediate results to disk.

However, performance depends on the commands and workload. A pipe is not always faster than writing and reading a file.

### Cleanliness

Pipes avoid creating temporary files that would otherwise need to be managed and cleaned up.

### Convenience

Pipelines make multi-step operations readable and easy to combine.

### Processing Behavior

PowerShell pipelines commonly process objects as they are produced, although some commands buffer data or must finish collecting results first.

### When Temporary Files Are Useful

Temporary files are still useful when you need to:
- Preserve results for later.
- Share output with another program.
- Keep a record of a command's results.
- Process data in a separate step.
- Avoid rerunning an expensive command.

Use a pipe when data needs to flow directly between commands. Use a file when the output needs to persist.

## 6. PowerShell Execution Policy

PowerShell execution policy is a safety feature that controls the conditions under which PowerShell loads and runs configuration files and scripts.

It helps prevent accidental execution of certain scripts, but it is not a complete security boundary.

### Common Execution Policies

| Policy | General Behavior |
|---|---|
| Restricted | Allows individual commands but blocks PowerShell script files |
| RemoteSigned | Allows local scripts; downloaded scripts generally need a trusted signature or must be appropriately unblocked |
| AllSigned | Requires scripts and configuration files to be signed by a trusted publisher |
| Unrestricted | Allows unsigned scripts, with warnings or prompts for certain downloaded scripts |
| Bypass | Nothing is blocked by the execution policy and no policy warnings or prompts are generated |
| Undefined | No policy is set at that scope; another scope or platform default may apply |

The effective policy depends on the platform, PowerShell version, and policy scopes.

Group Policy settings can take precedence over user-level settings.

### Check the Current Policy

```powershell
Get-ExecutionPolicy
```

This displays the effective execution policy.

To inspect policy settings at each scope:

```powershell
Get-ExecutionPolicy -List
```

### Execution Policy Scopes

Common scopes include:
- MachinePolicy
- UserPolicy
- Process
- CurrentUser
- LocalMachine

The effective policy is determined by precedence rules, not simply by whichever setting was changed most recently.

### Change Policy for the Current User

On systems where policy restrictions permit the change, this command sets RemoteSigned for the current user:

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

Follow your organization's rules before changing security settings.

### Temporary Process-Level Policy

A policy set at the Process scope applies to the current PowerShell process and its session.

For example:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned
```

This does not permanently change the policy for every user or computer. Higher-precedence policies may still override it.

### Security Warning

Do not use Bypass or Unrestricted simply to make an unfamiliar script run.

Execution policy does not guarantee that a script is safe. Malicious code can run through other mechanisms, and other security controls are still necessary.

Before running a script:
1. Read and understand its contents.
2. Verify where it came from.
3. Confirm that you are authorized to run it.
4. Follow organizational security policies.

## 7. Practical Lab

These exercises use simple commands to demonstrate streams and pipelines.

### Exercise 1: Save Process Information

```powershell
Get-Process > .\processes.txt
```

Open `processes.txt` to inspect the saved results.

### Exercise 2: Append a Timestamp

```powershell
Get-Date >> .\processes.txt
```

Inspect the end of the file to confirm that the timestamp was appended.

### Exercise 3: Filter Processes

```powershell
Get-Process | Where-Object { $_.WorkingSet64 -gt 100MB }
```

This displays processes whose reported working-set memory exceeds 100 MB.

### Exercise 4: Count Services

```powershell
Get-Service | Measure-Object
```

This counts the service objects returned by the command.

### Exercise 5: Inspect Execution Policy

```powershell
Get-ExecutionPolicy -List
```

Record the policy values displayed on your own computer. Do not change them unless necessary and authorized.

## 8. Practice Questions

### Question 1

Which standard stream is associated with normal output?

A. stdin  
B. stdout  
C. stderr  
D. Stream 0 only  

### Question 2

Which standard stream is associated with error output?

A. stdin  
B. stdout  
C. stderr  
D. Stream 1  

### Question 3

What does `>` generally do in PowerShell?

A. Appends success output to a file  
B. Writes success output to a file, replacing existing contents  
C. Sorts objects  
D. Changes execution policy  

### Question 4

What does `>>` do?

A. Appends success output to a file  
B. Deletes a file  
C. Filters processes  
D. Runs a script as administrator  

### Question 5

What is the purpose of the pipe operator (`|`)?

A. Encrypt data  
B. Pass output from one command to another  
C. Shut down a computer  
D. Change file permissions  

### Question 6

Which command filters pipeline objects?

A. Where-Object  
B. Get-Date  
C. Get-ExecutionPolicy  
D. Set-Location  

### Question 7

What is a key advantage of pipes?

A. They always make every command faster  
B. They can connect commands without intermediate files  
C. They guarantee that errors cannot occur  
D. They permanently save all output  

### Question 8

What does the Restricted execution policy generally do?

A. Allows every script to run  
B. Blocks PowerShell script files from running  
C. Automatically signs all scripts  
D. Disables every PowerShell command  

### Question 9

Which command displays the effective PowerShell execution policy?

A. Get-Process  
B. Get-ExecutionPolicy  
C. Get-ChildItem  
D. Get-Service  

### Question 10

Is PowerShell execution policy a complete security boundary?

A. Yes, it prevents all malicious scripts  
B. No, it is a safety feature rather than a complete security boundary  
C. Yes, it replaces antivirus software  
D. No, because PowerShell cannot run scripts  

## Answers and Explanations

1. B - stdout is the standard output stream.
2. C - stderr is the standard error stream.
3. B - `>` redirects success output and replaces existing file contents.
4. A - `>>` appends success output.
5. B - A pipe passes output to another command as input.
6. A - Where-Object filters objects based on a condition.
7. B - Pipes connect commands without requiring an intermediate file.
8. B - Restricted generally prevents PowerShell script files from running.
9. B - Get-ExecutionPolicy displays the effective policy.
10. B - Execution policy helps prevent accidental script execution but does not guarantee security.

## Revision Checklist

- [ ] Define stdin, stdout, and stderr.
- [ ] Explain PowerShell's numbered output streams.
- [ ] Distinguish `>` from `>>`.
- [ ] Explain error redirection with `2>`.
- [ ] Explain how a pipeline works.
- [ ] Describe the Unix philosophy.
- [ ] Compare pipes with temporary files.
- [ ] Identify common execution policies.
- [ ] Use Get-ExecutionPolicy and Get-ExecutionPolicy -List.
- [ ] Explain why execution policy is not a complete security boundary.

## Further Reading

- [CompTIA Tech+ Certification](https://www.comptia.org/certifications/tech)
- [Microsoft Learn: about_Redirection](https://learn.microsoft.com/powershell/module/microsoft.powershell.core/about/about_redirection)
- [Microsoft Learn: about_Pipelines](https://learn.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pipelines)
- [Microsoft Learn: about_Execution_Policies](https://learn.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies)

## PowerShell Execution Policy

Execution Policy controls the conditions under which PowerShell runs scripts. It is a safety feature, not a security boundary.

| Policy | Description |
|---|---|
| Restricted | Blocks script files from running. |
| RemoteSigned | Local scripts can run; downloaded scripts generally need a trusted signature. |
| AllSigned | All scripts must be signed by a trusted publisher. |
| Unrestricted | Allows scripts to run, with warnings in certain cases. |
| Bypass | Nothing is blocked and no execution-policy warnings or prompts appear. |

### Check Execution Policy

```powershell
Get-ExecutionPolicy
Get-ExecutionPolicy -List
```

### Set Execution Policy for the Current User

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

This normally does not require an elevated PowerShell session.

For a temporary policy limited to the current PowerShell process:

```powershell
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process
```

Use bypass only when appropriate for a trusted script and your organization's policies permit it.

**Exam tip:** Execution Policy and Administrator privileges are different. Changing Execution Policy does not automatically grant administrative rights.

## Administrator Privileges and UAC

An elevated PowerShell session runs with administrative privileges.

### Open PowerShell as Administrator

1. Open the Start menu.
2. Search for PowerShell.
3. Select **Run as administrator**.
4. Approve the User Account Control (UAC) prompt.

### Request an Elevated PowerShell Window

```powershell
Start-Process -FilePath "powershell.exe" -Verb RunAs
```

UAC may request approval or administrator credentials.

**Best practice:** Use a standard session for everyday tasks and elevate only when necessary.

## Building Blocks of a Script

| Concept | Purpose | Example |
|---|---|---|
| Input | Receives information | `Read-Host "Enter your name"` |
| Variables | Store information | `$name = "Alex"` |
| Conditions | Make decisions | `if ($number -gt 10) { ... }` |
| Loops | Repeat actions | `foreach ($item in $items) { ... }` |
| Output | Produces results | `Write-Output $name` |

### Example Script

```powershell
$name = Read-Host "Enter your name"

if ($name) {
    Write-Output "Hello, $name!"
}
```

## Windows Software Management with winget

`winget` is the Windows Package Manager command-line tool.

```powershell
winget search 7zip
winget install 7zip.7zip
winget list
winget upgrade
```

Review package details before installing software. Package identifiers and availability may vary.

## Environment Variables and PATH

Environment variables store configuration information used by Windows and applications.

```powershell
$env:PATH
$env:USERPROFILE
$env:TEMP
Get-ChildItem Env:
```

- `PATH` contains directories searched when locating executable commands.
- `USERPROFILE` identifies the current user's profile directory.
- `TEMP` identifies a temporary-files directory.

## How PowerShell Finds Commands

Use `Get-Command` to identify a command and its type:

```powershell
Get-Command notepad
Get-Command powershell
```

Use `where.exe` to search for matching executable files:

```powershell
where.exe notepad
where.exe powershell
```

**Exam tip:** `Get-Command` can identify cmdlets, aliases, functions, scripts, and applications. `where.exe` searches for files in the current directory and PATH directories.

