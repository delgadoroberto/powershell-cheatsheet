# 03 - Processes

## Overview

Processes represent running applications and background services on a system. PowerShell provides powerful cmdlets to monitor, filter, start, stop, and manage processes efficiently.

Understanding process management is essential for system administration, troubleshooting, performance analysis, and cybersecurity investigations.

> **Key Takeaways**
>
> - View running processes.
> - Filter and sort process information.
> - Start and stop processes safely.
> - Monitor CPU and memory usage.
> - Apply process management techniques in administration and security scenarios.

---

## Quick Reference

| Cmdlet | Purpose |
|---------|---------|
| `Get-Process` | List running processes |
| `Start-Process` | Start a new process |
| `Stop-Process` | Stop a running process |
| `Wait-Process` | Wait for a process to exit |
| `Debug-Process` | Debug a process (Windows only) |

---

## Prerequisites

Before continuing, you should:

- Complete **01 - Getting Started**.
- Understand basic PowerShell navigation.
- Have permission to manage local processes.
- Run PowerShell as Administrator when required.

---

## Common Cmdlets

### `Get-Process`

Displays running processes.

```powershell
Get-Process
```

---

### `Start-Process`

Starts an application or executable.

```powershell
Start-Process notepad.exe
```

---

### `Stop-Process`

Stops a running process.

```powershell
Stop-Process -Name notepad
```

---

### `Wait-Process`

Waits until a process exits.

```powershell
Wait-Process -Name notepad
```

---

### `Debug-Process`

Attaches the debugger to a process.

```powershell
Debug-Process -Id 1234
```

---

## Syntax

General syntax:

```powershell
Verb-Noun [-Parameter] <Value>
```

Example:

```powershell
Stop-Process -Name notepad
```

---

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-Name` | Specifies the process name |
| `-Id` | Specifies the process ID (PID) |
| `-Force` | Forces termination |
| `-PassThru` | Returns the affected process object |
| `-WhatIf` | Simulates the operation |
| `-Confirm` | Requests confirmation before executing |

---

## Examples

### Example 1

List all running processes.

```powershell
Get-Process
```

---

### Example 2

Find all Chrome processes.

```powershell
Get-Process chrome
```

---

### Example 3

Sort processes by CPU usage.

```powershell
Get-Process | Sort-Object CPU -Descending
```

---

### Example 4

Display the ten processes using the most memory.

```powershell
Get-Process |
Sort-Object WorkingSet -Descending |
Select-Object -First 10 Name, Id, WorkingSet
```

---

### Example 5

Start Notepad.

```powershell
Start-Process notepad.exe
```

---

### Example 6

Stop Notepad.

```powershell
Stop-Process -Name notepad
```

---

## Expected Output

Example:

```text
Handles  NPM(K)    PM(M)     CPU(s)      Id ProcessName
-------  ------    -----     ------      -- -----------
   521      45      87.4       8.42    4120 chrome
   197      18      21.8       0.95    1932 explorer
    96       8       5.3       0.02    6784 notepad
```

---

## Cybersecurity Use Cases

PowerShell process management is useful for:

- Detecting suspicious processes.
- Identifying resource-intensive applications.
- Investigating malware activity.
- Monitoring unauthorized software.
- Supporting incident response.
- Collecting forensic evidence.

Example:

```powershell
Get-Process |
Sort-Object CPU -Descending |
Select-Object -First 20
```

---

## Did You Know?

> Every running process has a unique Process ID (PID). While process names may repeat, the PID uniquely identifies a running instance and is often the safest way to target a specific process.

---

## Try It Yourself

Complete the following exercises:

1. List all running processes.
2. Find your web browser process.
3. Display the five processes using the most memory.
4. Open Notepad using PowerShell.
5. Close Notepad using `Stop-Process`.
6. List processes sorted by CPU usage.

---

## Common Mistakes

Common mistakes include:

- Terminating critical system processes.
- Using `-Force` without understanding the consequences.
- Confusing process names with executable file names.
- Forgetting that multiple instances of the same process may be running.
- Closing applications without saving user data.

---

## Performance Tips

- Filter results before exporting or sorting large process lists.
- Use `-Id` instead of `-Name` when targeting a specific process.
- Avoid stopping unknown processes without investigation.
- Combine `Where-Object` and `Sort-Object` to reduce unnecessary output.

---

## Version Compatibility

| Feature | Windows PowerShell 5.1 | PowerShell 7+ |
|----------|:----------------------:|:-------------:|
| Process management cmdlets | ✅ | ✅ |
| Cross-platform support | Limited | ✅ |

---

## Related Commands

- `Get-Process`
- `Start-Process`
- `Stop-Process`
- `Wait-Process`
- `Get-Service`
- `Get-CimInstance`

---

## Microsoft Learn

Recommended topics:

- Get-Process
- Start-Process
- Stop-Process
- Wait-Process
- about_Processes

---

## Summary

In this chapter you learned how to:

- View running processes.
- Start and stop applications.
- Sort and filter process information.
- Monitor resource usage.
- Apply process management techniques in administration and cybersecurity scenarios.

The next chapter introduces Windows service management using PowerShell.
