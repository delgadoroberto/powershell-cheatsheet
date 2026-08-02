# 16 - Troubleshooting

## Overview

PowerShell provides a comprehensive set of tools for diagnosing Windows systems, investigating errors, and identifying configuration problems.

Troubleshooting with PowerShell can help administrators quickly collect system information, inspect services and processes, analyze event logs, test network connectivity, and verify security configurations.

This chapter combines techniques introduced throughout this repository into practical troubleshooting workflows.

> **Key Takeaways**
>
> - Diagnose common Windows problems with PowerShell.
> - Troubleshoot processes and services.
> - Investigate networking issues.
> - Analyze Windows Event Logs.
> - Check system resources and updates.
> - Apply PowerShell to security and incident response troubleshooting.

---

## Quick Reference

| Cmdlet | Purpose |
|---------|---------|
| `Get-ComputerInfo` | Display system information |
| `Get-Process` | Inspect running processes |
| `Get-Service` | Inspect Windows services |
| `Get-WinEvent` | Analyze Windows Event Logs |
| `Get-NetIPConfiguration` | Display network configuration |
| `Test-NetConnection` | Test network connectivity |
| `Resolve-DnsName` | Test DNS resolution |
| `Get-NetTCPConnection` | Inspect TCP connections |
| `Get-HotFix` | Display installed Windows updates |
| `Get-MpComputerStatus` | Check Microsoft Defender status |

---

## Prerequisites

Before continuing, you should:

- Complete the previous chapters in this repository.
- Understand basic PowerShell syntax and pipelines.
- Have administrative privileges when troubleshooting protected system components.
- Use a Windows test environment when experimenting with administrative commands.

---

## General Troubleshooting Workflow

A structured troubleshooting process helps avoid making unnecessary changes.

A useful workflow is:

```text
Identify
   ↓
Collect Information
   ↓
Analyze
   ↓
Test
   ↓
Remediate
   ↓
Verify
   ↓
Document
```

Before changing a system, collect enough information to understand the problem.

---

## System Information

### Display General System Information

```powershell
Get-ComputerInfo
```

For a more focused result:

```powershell
Get-ComputerInfo |
Select-Object WindowsProductName,WindowsVersion,OsBuildNumber,CsName
```

---

### Display the Last Boot Time

```powershell
Get-CimInstance Win32_OperatingSystem |
Select-Object LastBootUpTime
```

---

### Check Installed Updates

```powershell
Get-HotFix |
Sort-Object InstalledOn -Descending
```

This can help determine whether the system is missing recent updates.

---

## Process Troubleshooting

### List Running Processes

```powershell
Get-Process
```

---

### Find Processes Using High CPU

```powershell
Get-Process |
Sort-Object CPU -Descending |
Select-Object -First 10 Name,Id,CPU
```

---

### Find Processes Using High Memory

```powershell
Get-Process |
Sort-Object WorkingSet64 -Descending |
Select-Object -First 10 Name,Id,WorkingSet64
```

---

### Find a Specific Process

```powershell
Get-Process -Name "chrome"
```

---

### Inspect a Process

```powershell
Get-Process -Name "chrome" |
Select-Object Name,Id,Path,StartTime
```

> **Note**
>
> Access to properties such as `Path` or `StartTime` may require elevated privileges depending on the process.

---

## Service Troubleshooting

### List Services

```powershell
Get-Service
```

---

### Find Stopped Services

```powershell
Get-Service |
Where-Object Status -eq "Stopped"
```

---

### Check a Specific Service

```powershell
Get-Service -Name "Spooler"
```

---

### Inspect Service Configuration

```powershell
Get-CimInstance Win32_Service -Filter "Name='Spooler'" |
Select-Object Name,State,StartMode,StartName,PathName
```

---

### Find Automatically Started Services That Are Not Running

```powershell
Get-CimInstance Win32_Service |
Where-Object {
    $_.StartMode -eq "Auto" -and $_.State -ne "Running"
} |
Select-Object Name,State,StartMode
```

This can be useful when investigating services that should normally start automatically.

---

## Event Log Troubleshooting

### Display Recent System Errors

```powershell
Get-WinEvent -FilterHashtable @{
    LogName = "System"
    Level = 2
} -MaxEvents 20
```

---

### Display Recent Application Errors

```powershell
Get-WinEvent -FilterHashtable @{
    LogName = "Application"
    Level = 2
} -MaxEvents 20
```

---

### Display Recent Security Events

```powershell
Get-WinEvent -LogName Security -MaxEvents 20
```

---

### Find Failed Logons

```powershell
Get-WinEvent -FilterHashtable @{
    LogName = "Security"
    Id = 4625
} -MaxEvents 20
```

---

### Display Event Details

```powershell
Get-WinEvent -FilterHashtable @{
    LogName = "System"
    Level = 2
} -MaxEvents 1 |
Format-List *
```

---

## Network Troubleshooting

### Display Network Configuration

```powershell
Get-NetIPConfiguration
```

---

### Display Network Adapters

```powershell
Get-NetAdapter
```

---

### Find Disabled Network Adapters

```powershell
Get-NetAdapter |
Where-Object Status -eq "Disabled"
```

---

### Test Basic Connectivity

```powershell
Test-Connection 8.8.8.8
```

---

### Test DNS Resolution

```powershell
Resolve-DnsName example.com
```

---

### Test TCP Connectivity

```powershell
Test-NetConnection example.com -Port 443
```

---

### Display Listening Ports

```powershell
Get-NetTCPConnection -State Listen
```

---

### Display Active TCP Connections

```powershell
Get-NetTCPConnection -State Established
```

---

## DNS Troubleshooting

### Display DNS Servers

```powershell
Get-DnsClientServerAddress
```

---

### Resolve a Hostname

```powershell
Resolve-DnsName example.com
```

---

### Query a Specific DNS Server

```powershell
Resolve-DnsName example.com -Server 8.8.8.8
```

---

## Disk and Storage Troubleshooting

### Display Volumes

```powershell
Get-Volume
```

---

### Display Available Disk Space

```powershell
Get-Volume |
Select-Object DriveLetter,FileSystemLabel,SizeRemaining,Size
```

---

### Find Low Disk Space

```powershell
Get-Volume |
Where-Object {
    $_.Size -gt 0 -and
    ($_.SizeRemaining / $_.Size) -lt 0.10
} |
Select-Object DriveLetter,SizeRemaining,Size
```

This example identifies volumes with less than approximately 10% free space.

---

## Windows Security Troubleshooting

### Check Microsoft Defender

```powershell
Get-MpComputerStatus |
Select-Object AntivirusEnabled,RealTimeProtectionEnabled,NISEnabled
```

---

### Update Defender Signatures

```powershell
Update-MpSignature
```

---

### Check Firewall Profiles

```powershell
Get-NetFirewallProfile |
Select-Object Name,Enabled,DefaultInboundAction,DefaultOutboundAction
```

---

### Check Execution Policies

```powershell
Get-ExecutionPolicy -List
```

---

## Remote Troubleshooting

### Test WinRM

```powershell
Test-WSMan Server01
```

---

### Collect Remote System Information

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {
    Get-ComputerInfo |
    Select-Object WindowsProductName,WindowsVersion,OsBuildNumber,CsName
}
```

---

### Check Remote Services

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {
    Get-Service |
    Where-Object Status -eq "Stopped"
}
```

---

### Check Remote Event Logs

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {
    Get-WinEvent -FilterHashtable @{
        LogName = "System"
        Level = 2
    } -MaxEvents 20
}
```

---

## File Troubleshooting

### Find Recently Modified Files

```powershell
Get-ChildItem C:\Users -File -Recurse -ErrorAction SilentlyContinue |
Sort-Object LastWriteTime -Descending |
Select-Object -First 20 FullName,LastWriteTime
```

---

### Find Large Files

```powershell
Get-ChildItem C:\Users -File -Recurse -ErrorAction SilentlyContinue |
Sort-Object Length -Descending |
Select-Object -First 20 FullName,Length
```

---

### Calculate a File Hash

```powershell
Get-FileHash .\file.exe -Algorithm SHA256
```

File hashes can help determine whether a file has changed or matches a known trusted reference.

---

## User and Account Troubleshooting

### Display Local Users

```powershell
Get-LocalUser
```

---

### Find Disabled Local Users

```powershell
Get-LocalUser |
Where-Object Enabled -eq $false
```

---

### Display Local Administrators

```powershell
Get-LocalGroupMember -Group "Administrators"
```

---

### Check the Current Identity

```powershell
whoami
```

---

### Display Current User Groups

```powershell
whoami /groups
```

---

## Active Directory Troubleshooting

### Find Locked Accounts

```powershell
Search-ADAccount -LockedOut
```

---

### Find Disabled Accounts

```powershell
Search-ADAccount -AccountDisabled
```

---

### Find Expired Accounts

```powershell
Search-ADAccount -AccountExpired
```

---

### Test Domain Controller Connectivity

```powershell
Test-ComputerSecureChannel
```

---

### Repair the Computer Secure Channel

```powershell
Test-ComputerSecureChannel -Repair
```

> **Warning**
>
> Use repair operations only when you have confirmed that the computer secure channel is actually the problem.

---

## PowerShell Troubleshooting

### Display PowerShell Version

```powershell
$PSVersionTable
```

---

### Display Command Information

```powershell
Get-Command Get-Process
```

---

### Display Command Help

```powershell
Get-Help Get-Process
```

---

### Find Available Parameters

```powershell
Get-Help Get-Process -Full
```

---

### Review Previous Commands

```powershell
Get-History
```

---

## Error Handling

PowerShell provides several mechanisms for identifying and handling errors.

### Display the Last Error

```powershell
$Error[0]
```

---

### Display Detailed Error Information

```powershell
$Error[0] | Format-List *
```

---

### Continue on Non-Terminating Errors

```powershell
Get-ChildItem C:\Restricted -ErrorAction SilentlyContinue
```

---

### Stop on Errors

```powershell
Get-ChildItem C:\Restricted -ErrorAction Stop
```

---

### Use `try/catch`

```powershell
try {
    Get-ChildItem C:\Restricted -ErrorAction Stop
}
catch {
    Write-Host "An error occurred: $($_.Exception.Message)"
}
```

---

## Troubleshooting Workflow Example

Suppose a Windows server is reported as slow.

A basic investigation could begin with:

### Step 1 - Check system information

```powershell
Get-ComputerInfo |
Select-Object WindowsProductName,WindowsVersion,OsBuildNumber,CsName
```

### Step 2 - Check CPU usage

```powershell
Get-Process |
Sort-Object CPU -Descending |
Select-Object -First 10 Name,Id,CPU
```

### Step 3 - Check memory usage

```powershell
Get-Process |
Sort-Object WorkingSet64 -Descending |
Select-Object -First 10 Name,Id,WorkingSet64
```

### Step 4 - Check services

```powershell
Get-Service |
Where-Object Status -eq "Stopped"
```

### Step 5 - Check system errors

```powershell
Get-WinEvent -FilterHashtable @{
    LogName = "System"
    Level = 2
} -MaxEvents 20
```

### Step 6 - Check disk space

```powershell
Get-Volume |
Select-Object DriveLetter,SizeRemaining,Size
```

### Step 7 - Check network connectivity

```powershell
Test-NetConnection example.com -Port 443
```

This workflow does not automatically identify the root cause, but it provides a structured starting point for investigation.

---

## Cybersecurity Troubleshooting

PowerShell can also support security investigations.

For example, when investigating suspicious activity:

### Check recent failed logons

```powershell
Get-WinEvent -FilterHashtable @{
    LogName = "Security"
    Id = 4625
} -MaxEvents 50
```

### Check listening ports

```powershell
Get-NetTCPConnection -State Listen
```

### Identify associated processes

```powershell
Get-NetTCPConnection -State Listen |
ForEach-Object {
    $Process = Get-Process -Id $_.OwningProcess -ErrorAction SilentlyContinue

    [PSCustomObject]@{
        LocalAddress = $_.LocalAddress
        LocalPort    = $_.LocalPort
        ProcessId    = $_.OwningProcess
        ProcessName  = $Process.ProcessName
    }
}
```

### Check Microsoft Defender

```powershell
Get-MpComputerStatus |
Select-Object AntivirusEnabled,RealTimeProtectionEnabled,NISEnabled
```

### Check common startup entries

```powershell
Get-ItemProperty "HKLM:\Software\Microsoft\Windows\CurrentVersion\Run"
```

These commands can help collect evidence during an initial investigation.

> **Security Note**
>
> Troubleshooting commands should be used to collect and analyze evidence before making changes to the system. During incident response, preserve relevant evidence and follow your organization's incident response procedures.

---

## Expected Output

Example:

```text
WindowsProductName : Windows 11 Pro
WindowsVersion     : 24H2
CsName             : WORKSTATION01

Name        Status
----        ------
Spooler     Running
W32Time     Running

LocalPort   ProcessId   ProcessName
---------   ----------   -----------
443         4120        nginx
3389        980         svchost
```

Actual output depends on the system being investigated.

---

## Common Mistakes

Common troubleshooting mistakes include:

- Changing configuration before collecting evidence.
- Running commands without understanding their impact.
- Ignoring Event Logs.
- Focusing on a single symptom instead of the complete system.
- Assuming that a stopped service is automatically the root cause.
- Running destructive commands during an investigation.
- Failing to document findings and changes.
- Ignoring security implications during troubleshooting.

---

## Performance Tips

- Collect only the information required for the investigation.
- Filter results as early as possible.
- Use `-MaxEvents` when querying Event Logs.
- Avoid recursive searches across entire drives unless necessary.
- Use remote execution when investigating multiple systems.
- Export relevant findings for later analysis.

---

## Troubleshooting Checklist

Use this checklist as a starting point when investigating a Windows issue:

```text
[ ] Identify the affected system
[ ] Identify the affected user
[ ] Determine when the problem started
[ ] Check system information
[ ] Check running processes
[ ] Check services
[ ] Check Event Logs
[ ] Check network connectivity
[ ] Check disk space
[ ] Check installed updates
[ ] Check security controls
[ ] Collect relevant evidence
[ ] Apply remediation
[ ] Verify the result
[ ] Document the resolution
```

---

## Try It Yourself

Complete the following exercises:

1. Identify your Windows version and build.
2. Find the top five processes by CPU usage.
3. Find stopped services.
4. Check available disk space.
5. Test DNS resolution.
6. Test TCP connectivity to port 443.
7. Find recent System errors.
8. Find failed logon events.
9. Check Microsoft Defender status.
10. Test WinRM connectivity to a lab computer.
11. Identify listening TCP ports.
12. Calculate the SHA-256 hash of a test file.

---

## Related Chapters

- [03 - Processes](03-processes.md)
- [04 - Services](04-services.md)
- [05 - Users and Groups](05-users-and-groups.md)
- [06 - Networking](06-networking.md)
- [07 - Event Logs](07-event-logs.md)
- [08 - Registry](08-registry.md)
- [09 - Active Directory](09-active-directory.md)
- [10 - Windows Security](10-windows-security.md)
- [11 - System Information](11-system-information.md)
- [12 - Remoting](12-remoting.md)
- [15 - Useful One-Liners](15-useful-one-liners.md)

---

## Summary

In this chapter you learned how to:

- Troubleshoot Windows systems using PowerShell.
- Investigate processes and services.
- Diagnose networking and DNS problems.
- Analyze Windows Event Logs.
- Check system resources and updates.
- Review Windows security controls.
- Troubleshoot remote systems.
- Apply structured troubleshooting workflows.
- Support initial cybersecurity investigations.

This chapter completes the core PowerShell command reference in this repository.
