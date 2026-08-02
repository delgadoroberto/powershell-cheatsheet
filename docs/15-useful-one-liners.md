# 15 - Useful One-Liners

## Overview

PowerShell one-liners are short commands that perform practical administrative, troubleshooting, and cybersecurity tasks without requiring a complete script.

They are useful for quickly collecting information, filtering results, troubleshooting systems, and performing repetitive tasks from the command line.

> **Key Takeaways**
>
> - Use PowerShell for quick administrative tasks.
> - Combine cmdlets with the pipeline.
> - Filter and transform command output.
> - Perform basic troubleshooting from the command line.
> - Apply PowerShell one-liners to cybersecurity workflows.

---

## Quick Reference

| Task | Command |
|------|---------|
| List running processes | `Get-Process` |
| List services | `Get-Service` |
| Display IP configuration | `Get-NetIPConfiguration` |
| Test connectivity | `Test-Connection` |
| Display listening ports | `Get-NetTCPConnection -State Listen` |
| Display logged-on users | `Get-CimInstance Win32_LoggedOnUser` |
| Display Windows version | `Get-ComputerInfo` |
| Display installed updates | `Get-HotFix` |
| Find failed logons | `Get-WinEvent` |
| Display firewall profiles | `Get-NetFirewallProfile` |

---

## Process Management

### List Running Processes

```powershell
Get-Process
```

---

### Find a Specific Process

```powershell
Get-Process -Name "chrome"
```

---

### Display the Top 10 Processes by CPU Usage

```powershell
Get-Process |
Sort-Object CPU -Descending |
Select-Object -First 10
```

---

### Display the Top 10 Processes by Memory Usage

```powershell
Get-Process |
Sort-Object WorkingSet64 -Descending |
Select-Object -First 10
```

---

### Stop a Process

```powershell
Stop-Process -Name "notepad"
```

> **Warning**
>
> Stopping a process can cause data loss or interrupt system services. Verify the target process before executing the command.

---

## Service Management

### List Running Services

```powershell
Get-Service |
Where-Object Status -eq "Running"
```

---

### Find a Specific Service

```powershell
Get-Service -Name "Spooler"
```

---

### Find Stopped Services

```powershell
Get-Service |
Where-Object Status -eq "Stopped"
```

---

### Find Services Configured for Automatic Startup

```powershell
Get-CimInstance Win32_Service |
Where-Object StartMode -eq "Auto" |
Select-Object Name,State,StartMode
```

---

## Networking

### Display IP Configuration

```powershell
Get-NetIPConfiguration
```

---

### Display Network Adapters

```powershell
Get-NetAdapter
```

---

### Test Connectivity

```powershell
Test-Connection 8.8.8.8
```

---

### Test a TCP Port

```powershell
Test-NetConnection example.com -Port 443
```

---

### Display Listening TCP Ports

```powershell
Get-NetTCPConnection -State Listen
```

---

### Display the Local IP Addresses

```powershell
Get-NetIPAddress |
Select-Object IPAddress,InterfaceAlias
```

---

## System Information

### Display Windows Information

```powershell
Get-ComputerInfo |
Select-Object WindowsProductName,WindowsVersion,OsBuildNumber
```

---

### Display Computer Name

```powershell
$env:COMPUTERNAME
```

---

### Display Current User

```powershell
$env:USERNAME
```

---

### Display System Uptime

```powershell
(Get-Date) - (Get-CimInstance Win32_OperatingSystem).LastBootUpTime
```

---

### Display Installed Updates

```powershell
Get-HotFix |
Sort-Object InstalledOn -Descending
```

---

## Files and Folders

### Find Large Files

```powershell
Get-ChildItem -Path C:\ -File -Recurse -ErrorAction SilentlyContinue |
Sort-Object Length -Descending |
Select-Object -First 10 FullName,Length
```

> **Note**
>
> Searching an entire drive recursively can take significant time and may generate access-denied errors.

---

### Find Files Modified Recently

```powershell
Get-ChildItem -Path C:\Users -File -Recurse -ErrorAction SilentlyContinue |
Where-Object LastWriteTime -gt (Get-Date).AddDays(-1)
```

---

### Count Files in a Directory

```powershell
(Get-ChildItem -File).Count
```

---

### Calculate Directory Size

```powershell
(Get-ChildItem -File -Recurse -ErrorAction SilentlyContinue |
Measure-Object Length -Sum).Sum
```

---

## Event Logs

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
}
```

---

### Find Successful Logons

```powershell
Get-WinEvent -FilterHashtable @{
    LogName = "Security"
    Id = 4624
}
```

---

### Display Recent System Errors

```powershell
Get-WinEvent -FilterHashtable @{
    LogName = "System"
    Level = 2
} -MaxEvents 20
```

---

## Windows Security

### Display Microsoft Defender Status

```powershell
Get-MpComputerStatus |
Select-Object AntivirusEnabled,RealTimeProtectionEnabled
```

---

### Update Microsoft Defender Signatures

```powershell
Update-MpSignature
```

---

### Display Windows Firewall Profiles

```powershell
Get-NetFirewallProfile |
Select-Object Name,Enabled,DefaultInboundAction,DefaultOutboundAction
```

---

### Display PowerShell Execution Policies

```powershell
Get-ExecutionPolicy -List
```

---

## Users and Groups

### Display Local Users

```powershell
Get-LocalUser
```

---

### Display Local Administrators

```powershell
Get-LocalGroupMember -Group "Administrators"
```

---

### Find Disabled Local Users

```powershell
Get-LocalUser |
Where-Object Enabled -eq $false
```

---

### Display the Current User's Groups

```powershell
whoami /groups
```

---

## Active Directory

### Find Disabled AD Accounts

```powershell
Search-ADAccount -AccountDisabled
```

---

### Find Locked AD Accounts

```powershell
Search-ADAccount -LockedOut
```

---

### List Domain Admins

```powershell
Get-ADGroupMember -Identity "Domain Admins"
```

> **Security Note**
>
> Membership in privileged groups should be reviewed regularly and follow the principle of least privilege.

---

## Registry

### Check Common Startup Entries

```powershell
Get-ItemProperty "HKLM:\Software\Microsoft\Windows\CurrentVersion\Run"
```

---

### Check Current User Startup Entries

```powershell
Get-ItemProperty "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run"
```

---

## Remote Administration

### Test WinRM Connectivity

```powershell
Test-WSMan Server01
```

---

### Run a Command Remotely

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {
    Get-ComputerInfo
}
```

---

### Check Remote Services

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {
    Get-Service
}
```

---

## Data Filtering and Formatting

### Select Specific Properties

```powershell
Get-Process |
Select-Object Name,Id,CPU
```

---

### Sort Results

```powershell
Get-Process |
Sort-Object CPU -Descending
```

---

### Filter Results

```powershell
Get-Service |
Where-Object Status -eq "Running"
```

---

### Count Results

```powershell
Get-Service |
Where-Object Status -eq "Running" |
Measure-Object
```

---

### Export Results to CSV

```powershell
Get-Process |
Select-Object Name,Id,CPU |
Export-Csv processes.csv -NoTypeInformation
```

---

## Cybersecurity One-Liners

### Find Listening Ports

```powershell
Get-NetTCPConnection -State Listen |
Select-Object LocalAddress,LocalPort,OwningProcess
```

---

### Map Listening Ports to Processes

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

---

### Find Recently Created Processes

```powershell
Get-CimInstance Win32_Process |
Select-Object ProcessId,Name,CreationDate |
Sort-Object CreationDate -Descending |
Select-Object -First 20
```

---

### Check PowerShell History

```powershell
Get-History
```

---

### Display the PowerShell History File

```powershell
(Get-PSReadLineOption).HistorySavePath
```

---

### Calculate a File Hash

```powershell
Get-FileHash .\file.exe -Algorithm SHA256
```

---

### Compare a File Hash

```powershell
Get-FileHash .\file.exe -Algorithm SHA256
```

Compare the resulting hash with a trusted reference.

---

## Troubleshooting One-Liners

### Check DNS Resolution

```powershell
Resolve-DnsName example.com
```

---

### Test HTTPS Connectivity

```powershell
Test-NetConnection example.com -Port 443
```

---

### Display Current Routes

```powershell
Get-NetRoute
```

---

### Display DNS Client Configuration

```powershell
Get-DnsClientServerAddress
```

---

### Display Disk Space

```powershell
Get-Volume |
Select-Object DriveLetter,FileSystemLabel,SizeRemaining,Size
```

---

### Find Recently Modified Files

```powershell
Get-ChildItem C:\Users -File -Recurse -ErrorAction SilentlyContinue |
Sort-Object LastWriteTime -Descending |
Select-Object -First 20 FullName,LastWriteTime
```

---

## One-Liner Patterns

PowerShell becomes especially powerful when multiple cmdlets are combined through the pipeline.

### Filter → Sort → Select

```powershell
Get-Process |
Where-Object CPU -gt 100 |
Sort-Object CPU -Descending |
Select-Object -First 10 Name,Id,CPU
```

---

### Query → Filter → Export

```powershell
Get-Service |
Where-Object Status -eq "Running" |
Export-Csv running-services.csv -NoTypeInformation
```

---

### Query → Select → Format

```powershell
Get-NetAdapter |
Select-Object Name,Status,LinkSpeed |
Format-Table
```

---

## Expected Output

Example:

```text
Name        Id     CPU
----        --     ---
chrome      4212   152.3
powershell  8356   104.7
svchost     1024    87.2
```

Actual output depends on the system and current activity.

---

## Common Mistakes

Common mistakes include:

- Running destructive commands without verifying the target.
- Using `-Recurse` against large directories unnecessarily.
- Executing commands with administrative privileges when they are not required.
- Assuming command output is identical across Windows versions.
- Forgetting to handle errors in automation.
- Copying one-liners without understanding what each pipeline stage does.

---

## Performance Tips

- Filter data as early as possible.
- Avoid unnecessary `Format-*` cmdlets when processing data.
- Use `Select-Object` to retrieve only required properties.
- Avoid recursive searches across entire drives unless necessary.
- Prefer native filtering parameters when available.

For example, this is generally preferable:

```powershell
Get-WinEvent -FilterHashtable @{
    LogName = "Security"
    Id = 4625
}
```

instead of retrieving a large number of events and filtering them afterward.

---

## Security Considerations

One-liners can be powerful administrative and security tools, but they can also perform destructive actions.

Before executing an unfamiliar command:

1. Understand every cmdlet involved.
2. Verify the target system or object.
3. Check whether administrative privileges are required.
4. Test commands in a lab environment when possible.
5. Use `-WhatIf` when supported.
6. Avoid copying commands blindly from untrusted sources.

---

## Try It Yourself

Complete the following exercises:

1. Find the top five processes by memory usage.
2. List all stopped services.
3. Display listening TCP ports.
4. Find failed Windows logons.
5. Display installed Windows updates.
6. Calculate the SHA-256 hash of a file.
7. Find the largest files in a test directory.
8. Export running services to CSV.
9. Test connectivity to a remote host on port 443.
10. Retrieve system information from a remote computer.

---

## Related Chapters

- [02 - Files and Folders](02-files-and-folders.md)
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

---

## Summary

In this chapter you learned how to:

- Use PowerShell one-liners for administration.
- Filter, sort, and transform command output.
- Perform common networking and troubleshooting tasks.
- Collect security-related information.
- Combine multiple cmdlets through the pipeline.
- Apply PowerShell one-liners to cybersecurity workflows.

The next chapter covers troubleshooting techniques and practical diagnostic workflows.
