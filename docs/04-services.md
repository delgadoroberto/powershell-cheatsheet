# 04 - Services

## Overview

Windows services are background processes that perform essential operating system and application tasks. Unlike interactive applications, services can start automatically during system boot and continue running without user intervention.

PowerShell provides a comprehensive set of cmdlets for viewing, starting, stopping, restarting, and configuring services, making it an essential tool for system administration and troubleshooting.

> **Key Takeaways**
>
> - List and inspect Windows services.
> - Start, stop, and restart services safely.
> - Understand service startup types.
> - Identify service dependencies.
> - Apply service management techniques in administration and cybersecurity scenarios.

---

## Quick Reference

| Cmdlet | Purpose |
|---------|---------|
| `Get-Service` | List Windows services |
| `Start-Service` | Start a service |
| `Stop-Service` | Stop a service |
| `Restart-Service` | Restart a service |
| `Suspend-Service` | Suspend a service |
| `Resume-Service` | Resume a suspended service |
| `Set-Service` | Modify service properties |
| `New-Service` | Create a new service |

---

## Prerequisites

Before continuing, you should:

- Complete **01 - Getting Started**.
- Understand the basics of **03 - Processes**.
- Have administrative privileges when managing system services.

---

## Common Cmdlets

### `Get-Service`

Displays Windows services.

```powershell
Get-Service
```

---

### `Start-Service`

Starts a stopped service.

```powershell
Start-Service -Name Spooler
```

---

### `Stop-Service`

Stops a running service.

```powershell
Stop-Service -Name Spooler
```

---

### `Restart-Service`

Restarts a service.

```powershell
Restart-Service -Name Spooler
```

---

### `Set-Service`

Modifies service settings.

```powershell
Set-Service -Name Spooler -StartupType Automatic
```

---

### `New-Service`

Creates a new Windows service.

```powershell
New-Service -Name DemoService -BinaryPathName "C:\Demo\demo.exe"
```

---

## Syntax

General syntax:

```powershell
Verb-Noun [-Parameter] <Value>
```

Example:

```powershell
Restart-Service -Name Spooler
```

---

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-Name` | Specifies the service name |
| `-DisplayName` | Specifies the service display name |
| `-StartupType` | Defines how the service starts |
| `-Status` | Filters services by status |
| `-PassThru` | Returns the affected service |
| `-WhatIf` | Simulates the operation |
| `-Confirm` | Requests confirmation |

---

## Examples

### Example 1

List all services.

```powershell
Get-Service
```

---

### Example 2

Display only running services.

```powershell
Get-Service |
Where-Object Status -eq Running
```

---

### Example 3

Display stopped services.

```powershell
Get-Service |
Where-Object Status -eq Stopped
```

---

### Example 4

Restart the Print Spooler service.

```powershell
Restart-Service -Name Spooler
```

---

### Example 5

Display services sorted by status.

```powershell
Get-Service |
Sort-Object Status, DisplayName
```

---

### Example 6

Display information about a specific service.

```powershell
Get-Service WinDefend
```

---

## Expected Output

Example:

```text
Status   Name          DisplayName
------   ----          -----------
Running  Spooler       Print Spooler
Running  WinDefend     Microsoft Defender Antivirus Service
Stopped  WSearch       Windows Search
```

---

## Cybersecurity Use Cases

PowerShell service management is useful for:

- Verifying that security services are running.
- Identifying unauthorized services.
- Investigating persistence mechanisms.
- Monitoring antivirus services.
- Auditing service configurations.
- Supporting incident response.

Example:

```powershell
Get-Service |
Where-Object Status -eq Running
```

---

## Did You Know?

> Every Windows service has both a **Service Name** and a **Display Name**.
>
> Most PowerShell cmdlets use the **Service Name**, which is usually shorter and does not contain spaces.

---

## Try It Yourself

Complete the following exercises:

1. List all Windows services.
2. Display only stopped services.
3. Find the Print Spooler service.
4. Display the Windows Defender service.
5. Restart a non-critical service in a test environment.
6. Sort services alphabetically by display name.

---

## Common Mistakes

Common mistakes include:

- Stopping critical Windows services.
- Confusing the service name with the display name.
- Restarting production services without impact analysis.
- Changing startup types without understanding service dependencies.
- Forgetting that some services require administrative privileges.

---

## Performance Tips

- Filter services before sorting large outputs.
- Restart services only when necessary.
- Verify service status before attempting to start or stop it.
- Use service names instead of display names in automation scripts.

---

## Version Compatibility

| Feature | Windows PowerShell 5.1 | PowerShell 7+ |
|----------|:----------------------:|:-------------:|
| Service management cmdlets | ✅ | ✅ |
| Windows services | ✅ | Limited (platform dependent) |

---

## Related Commands

- `Get-Service`
- `Start-Service`
- `Stop-Service`
- `Restart-Service`
- `Set-Service`
- `Get-Process`
- `Get-CimInstance`

---

## Microsoft Learn

Recommended topics:

- Get-Service
- Start-Service
- Stop-Service
- Restart-Service
- Set-Service
- New-Service

---

## Summary

In this chapter you learned how to:

- List Windows services.
- Start, stop, and restart services.
- Understand startup types.
- Inspect service status.
- Apply service management in administration and cybersecurity scenarios.

The next chapter introduces local user and group management using PowerShell.
