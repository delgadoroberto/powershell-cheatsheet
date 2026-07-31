# 07 - Event Logs

## Overview

Windows Event Logs record system, security, and application events that help administrators monitor system health, troubleshoot issues, and investigate security incidents.

PowerShell provides powerful cmdlets to query, filter, and analyze event logs efficiently, making it an essential tool for system administration and cybersecurity.

> **Key Takeaways**
>
> - View Windows Event Logs.
> - Filter events by log, ID, level, or date.
> - Search for security-related events.
> - Export event log data for analysis.
> - Apply event log analysis in administration and cybersecurity scenarios.

---

## Quick Reference

| Cmdlet | Purpose |
|---------|---------|
| `Get-WinEvent` | Retrieve Windows Event Logs |
| `Get-EventLog` | Retrieve classic Windows Event Logs (legacy) |
| `Clear-EventLog` | Clear classic event logs |
| `Limit-EventLog` | Configure classic event logs |
| `New-EventLog` | Create a new classic event log |
| `Write-EventLog` | Write an event to a classic event log |

---

## Prerequisites

Before continuing, you should:

- Complete **01 - Getting Started**.
- Understand basic Windows administration.
- Run PowerShell with administrative privileges when accessing protected logs.

---

## Common Cmdlets

### `Get-WinEvent`

Retrieves events from Windows Event Logs.

```powershell
Get-WinEvent -LogName System
```

---

### `Get-EventLog`

Retrieves events from classic Windows Event Logs.

```powershell
Get-EventLog -LogName System
```

> **Note**
>
> `Get-WinEvent` is the recommended cmdlet for modern Windows systems.

---

### `Clear-EventLog`

Clears a classic event log.

```powershell
Clear-EventLog -LogName Application
```

---

### `Limit-EventLog`

Configures the maximum size and retention policy of a classic event log.

```powershell
Limit-EventLog -LogName Application -MaximumSize 32MB
```

---

### `Write-EventLog`

Writes a custom event to a classic event log.

```powershell
Write-EventLog -LogName Application -Source "PowerShell" -EventId 1000 -EntryType Information -Message "Test event"
```

---

## Syntax

General syntax:

```powershell
Verb-Noun [-Parameter] <Value>
```

Example:

```powershell
Get-WinEvent -LogName Security
```

---

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-LogName` | Specifies the event log |
| `-FilterHashtable` | Filters events efficiently |
| `-MaxEvents` | Limits the number of returned events |
| `-ComputerName` | Queries a remote computer |
| `-Oldest` | Returns the oldest events first |

---

## Examples

### Example 1

Display recent System events.

```powershell
Get-WinEvent -LogName System -MaxEvents 20
```

---

### Example 2

Display recent Security events.

```powershell
Get-WinEvent -LogName Security -MaxEvents 20
```

---

### Example 3

Display failed logon events.

```powershell
Get-WinEvent -FilterHashtable @{
    LogName = 'Security'
    Id = 4625
}
```

---

### Example 4

Display successful logon events.

```powershell
Get-WinEvent -FilterHashtable @{
    LogName = 'Security'
    Id = 4624
}
```

---

### Example 5

Display the latest application errors.

```powershell
Get-WinEvent -FilterHashtable @{
    LogName = 'Application'
    Level = 2
}
```

---

### Example 6

Export recent System events.

```powershell
Get-WinEvent -LogName System -MaxEvents 100 |
Export-Csv SystemEvents.csv -NoTypeInformation
```

---

## Expected Output

Example:

```text
TimeCreated          Id    LevelDisplayName    ProviderName
-----------          --    ----------------    ------------
07/31/2026 18:30     4624  Information         Microsoft-Windows-Security-Auditing
07/31/2026 18:15     4625  Failure Audit       Microsoft-Windows-Security-Auditing
07/31/2026 17:42     6005  Information         EventLog
```

---

## Cybersecurity Use Cases

PowerShell event log analysis is commonly used for:

- Reviewing authentication events.
- Detecting failed logon attempts.
- Investigating privilege escalation.
- Monitoring service installations.
- Supporting digital forensics.
- Performing incident response.
- Identifying suspicious system activity.

Example:

```powershell
Get-WinEvent -FilterHashtable @{
    LogName = 'Security'
    Id = 4625
} |
Select-Object TimeCreated, Id, MachineName
```

---

## Did You Know?

> Event ID **4624** represents a successful logon, while **4625** indicates a failed logon attempt. These are among the most commonly reviewed security events during incident investigations.

---

## Try It Yourself

Complete the following exercises:

1. Display the latest 20 System events.
2. Display the latest 20 Security events.
3. Find all failed logon events.
4. Find all successful logon events.
5. Export the latest 100 System events to a CSV file.
6. Identify the provider that generated the most recent event.

---

## Common Mistakes

Common mistakes include:

- Using `Get-EventLog` instead of `Get-WinEvent` on modern systems.
- Retrieving entire logs without filtering.
- Ignoring event timestamps during investigations.
- Clearing event logs without proper authorization.
- Failing to export logs before analysis.

---

## Performance Tips

- Use `-FilterHashtable` whenever possible for better performance.
- Limit results with `-MaxEvents`.
- Export relevant events instead of entire logs.
- Query specific logs instead of searching all available logs.

---

## Version Compatibility

| Feature | Windows PowerShell 5.1 | PowerShell 7+ |
|----------|:----------------------:|:-------------:|
| `Get-WinEvent` | ✅ | ✅ |
| `Get-EventLog` | ✅ | Windows compatibility only |

---

## Related Commands

- `Get-WinEvent`
- `Get-EventLog`
- `Export-Csv`
- `Select-Object`
- `Where-Object`
- `Get-Service`
- `Get-Process`

---

## Microsoft Learn

Recommended topics:

- Get-WinEvent
- Get-EventLog
- Windows Event Log
- Security Auditing
- Event IDs

---

## Summary

In this chapter you learned how to:

- Query Windows Event Logs.
- Filter events efficiently.
- Review security-related events.
- Export logs for analysis.
- Use PowerShell for troubleshooting and cybersecurity investigations.

The next chapter introduces Windows Registry management using PowerShell.
