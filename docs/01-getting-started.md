# 01 - Getting Started

## Overview

PowerShell is a cross-platform command-line shell and scripting language developed by Microsoft. It is designed for task automation, system administration, configuration management, and application deployment.

Unlike traditional command-line interfaces, PowerShell works with **objects** instead of plain text, making it a powerful tool for automating administrative tasks and building reusable scripts.

This chapter introduces the core concepts you need before exploring the rest of this repository.

> **Key Takeaways**
>
> - PowerShell is both a command-line shell and a scripting language.
> - Cmdlets follow a `Verb-Noun` naming convention.
> - PowerShell pipelines pass objects between commands.
> - `Get-Help`, `Get-Command`, and `Get-Member` are essential learning tools.
> - Understanding these fundamentals will make the remaining chapters easier to follow.

---

## What Is PowerShell?

PowerShell combines a command-line interface with a powerful scripting language built on the .NET platform.

It enables administrators and developers to:

- Automate repetitive tasks
- Manage Windows systems
- Administer cloud environments
- Query system information
- Manage Active Directory
- Configure Microsoft 365 and Azure
- Build reusable automation scripts

Today, PowerShell is widely used by:

- System Administrators
- IT Support Engineers
- DevOps Engineers
- Cloud Engineers
- Cybersecurity Professionals

---

## Windows PowerShell vs PowerShell

| Feature | Windows PowerShell | PowerShell |
|----------|-------------------|------------|
| Latest Version | 5.1 | 7.x |
| Platform | Windows only | Windows, Linux, macOS |
| .NET Version | .NET Framework | .NET |
| Open Source | No | Yes |
| Active Development | No | Yes |

For new projects, Microsoft recommends using **PowerShell 7** whenever possible.

Windows PowerShell 5.1 is still required for some legacy Windows modules.

---

## Prerequisites

Before starting, you should have:

- Basic Windows knowledge
- PowerShell 5.1 or PowerShell 7 installed
- Permission to open PowerShell
- Administrator privileges for some commands

---

## Opening PowerShell

Common ways to start PowerShell:

- Start Menu → PowerShell
- Windows Terminal
- Run dialog (`Win + R`) → `powershell`
- Search for "PowerShell"

To check your PowerShell version:

```powershell
$PSVersionTable
```

---

## Understanding Cmdlets

PowerShell commands are called **cmdlets**.

Most cmdlets follow the pattern:

```text
Verb-Noun
```

Examples:

| Cmdlet | Description |
|---------|-------------|
| `Get-Service` | Lists services |
| `Get-Process` | Lists running processes |
| `Get-ChildItem` | Lists files and folders |
| `Start-Service` | Starts a service |
| `Stop-Process` | Stops a process |

---

## Getting Help

PowerShell includes built-in documentation.

Display help for a command:

```powershell
Get-Help Get-Service
```

Show detailed help:

```powershell
Get-Help Get-Service -Detailed
```

Show examples:

```powershell
Get-Help Get-Service -Examples
```

Open the online documentation:

```powershell
Get-Help Get-Service -Online
```

---

## Discovering Commands

List all available cmdlets:

```powershell
Get-Command
```

Find networking commands:

```powershell
Get-Command *Net*
```

Find service-related commands:

```powershell
Get-Command *Service*
```

---

## Understanding the Pipeline

One of PowerShell's most powerful features is the pipeline (`|`).

Instead of passing plain text, PowerShell passes objects between commands.

Example:

```powershell
Get-Service | Sort-Object Status
```

Example with filtering:

```powershell
Get-Process | Where-Object CPU -gt 100
```

---

## Execution Policy

Execution policies help prevent accidental script execution.

Check the current policy:

```powershell
Get-ExecutionPolicy
```

Display all policies:

```powershell
Get-ExecutionPolicy -List
```

Example:

```powershell
Set-ExecutionPolicy RemoteSigned
```

> **Note**
>
> Always understand your organization's security policies before modifying the execution policy.

---

## Your First Commands

Current date and time:

```powershell
Get-Date
```

Current directory:

```powershell
Get-Location
```

List files:

```powershell
Get-ChildItem
```

List running processes:

```powershell
Get-Process
```

List Windows services:

```powershell
Get-Service
```

---

## Examples

Example 1:

```powershell
Get-Service
```

Example 2:

```powershell
Get-Process | Sort-Object CPU -Descending
```

Example 3:

```powershell
Get-ChildItem -Recurse
```

---

## Expected Output

Depending on the command executed, PowerShell returns structured objects that can be displayed, filtered, sorted, or exported.

Example:

```text
Status   Name               DisplayName
------   ----               -----------
Running  Spooler            Print Spooler
Running  WinDefend          Microsoft Defender Antivirus Service
Stopped  WSearch            Windows Search
```

---

## Cybersecurity Use Cases

PowerShell is widely used in cybersecurity for:

- Security auditing
- Incident response
- Threat hunting
- Log analysis
- User auditing
- System inventory
- Security automation
- Defensive scripting

Understanding PowerShell fundamentals is essential before exploring these advanced scenarios.

---

## Common Mistakes

Common beginner mistakes include:

- Running PowerShell without sufficient privileges.
- Confusing Windows PowerShell with PowerShell 7.
- Ignoring the built-in help system.
- Copying commands without understanding their purpose.
- Changing the execution policy without understanding the security implications.

---

## Performance Tips

- Use filtering cmdlets instead of processing unnecessary data.
- Prefer native PowerShell cmdlets over external executables.
- Learn to use the pipeline effectively.
- Use `Get-Command` and `Get-Help` instead of relying only on internet searches.

---

## Version Compatibility

| Feature | Windows PowerShell 5.1 | PowerShell 7+ |
|----------|:----------------------:|:-------------:|
| Supported | ✅ | ✅ |
| Cross-platform | ❌ | ✅ |
| Active Development | ❌ | ✅ |

---

## Related Commands

- `Get-Help`
- `Get-Command`
- `Get-Member`
- `Get-Alias`
- `Get-Module`

---

## Microsoft Learn

Recommended official resources:

- PowerShell Documentation
- About Cmdlets
- About Pipelines
- About Execution Policies

---

## Summary

You should now understand:

- What PowerShell is
- The difference between Windows PowerShell and PowerShell 7
- How cmdlets are structured
- How to discover commands
- How to use built-in help
- How the pipeline works
- How execution policies affect script execution

The next chapter introduces file and directory management using PowerShell.
