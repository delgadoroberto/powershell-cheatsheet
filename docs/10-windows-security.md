# 10 - Windows Security

## Overview

PowerShell provides powerful cmdlets and modules for managing Windows security. Administrators can inspect antivirus status, execution policies, firewall configuration, certificates, and security preferences directly from the command line.

Understanding these cmdlets is essential for securing Windows systems, performing security audits, and automating defensive tasks.

> **Key Takeaways**
>
> - View Microsoft Defender status.
> - Manage PowerShell execution policies.
> - Inspect Windows Firewall configuration.
> - Work with digital certificates.
> - Apply PowerShell to Windows security administration.

---

## Quick Reference

| Cmdlet | Purpose |
|---------|---------|
| `Get-MpComputerStatus` | Display Microsoft Defender status |
| `Get-MpPreference` | Display Defender preferences |
| `Set-MpPreference` | Modify Defender preferences |
| `Update-MpSignature` | Update Defender signatures |
| `Get-ExecutionPolicy` | Display PowerShell execution policy |
| `Set-ExecutionPolicy` | Configure execution policy |
| `Get-NetFirewallProfile` | Display firewall profiles |
| `Get-ChildItem Cert:` | Display certificates |

---

## Prerequisites

Before continuing, you should:

- Complete **06 - Networking**.
- Understand **09 - Active Directory**.
- Run PowerShell with administrative privileges.
- Use Microsoft Defender on supported Windows systems.

---

## Common Cmdlets

### `Get-MpComputerStatus`

Displays Microsoft Defender status.

```powershell
Get-MpComputerStatus
```

---

### `Get-MpPreference`

Displays Microsoft Defender preferences.

```powershell
Get-MpPreference
```

---

### `Set-MpPreference`

Modifies Microsoft Defender settings.

```powershell
Set-MpPreference -DisableRealtimeMonitoring $false
```

---

### `Update-MpSignature`

Updates Defender signatures.

```powershell
Update-MpSignature
```

---

### `Get-ExecutionPolicy`

Displays the current execution policy.

```powershell
Get-ExecutionPolicy
```

---

### `Set-ExecutionPolicy`

Changes the execution policy.

```powershell
Set-ExecutionPolicy RemoteSigned
```

---

### `Get-NetFirewallProfile`

Displays firewall profile configuration.

```powershell
Get-NetFirewallProfile
```

---

### `Get-ChildItem Cert:`

Lists installed certificates.

```powershell
Get-ChildItem Cert:\LocalMachine\My
```

---

## Syntax

General syntax:

```powershell
Verb-Noun [-Parameter] <Value>
```

Example:

```powershell
Get-MpComputerStatus
```

---

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-Scope` | Specifies the execution policy scope |
| `-DisableRealtimeMonitoring` | Enables or disables Defender real-time protection |
| `-ComputerName` | Specifies a remote computer |
| `-Force` | Suppresses confirmation prompts |
| `-WhatIf` | Simulates the operation |

---

## Examples

### Example 1

Display Defender status.

```powershell
Get-MpComputerStatus
```

---

### Example 2

Display Defender preferences.

```powershell
Get-MpPreference
```

---

### Example 3

Update malware definitions.

```powershell
Update-MpSignature
```

---

### Example 4

Display the current execution policy.

```powershell
Get-ExecutionPolicy -List
```

---

### Example 5

Display firewall profiles.

```powershell
Get-NetFirewallProfile
```

---

### Example 6

Display installed machine certificates.

```powershell
Get-ChildItem Cert:\LocalMachine\My
```

---

## Expected Output

Example:

```text
AMServiceEnabled          : True
AntivirusEnabled          : True
RealTimeProtectionEnabled : True
NISEnabled                : True
```

---

## Cybersecurity Use Cases

PowerShell Windows security cmdlets are commonly used for:

- Verifying Microsoft Defender status.
- Reviewing execution policies.
- Auditing firewall configuration.
- Inspecting installed certificates.
- Performing security assessments.
- Supporting incident response.
- Validating endpoint security posture.

Example:

```powershell
Get-MpComputerStatus |
Select-Object AntivirusEnabled, RealTimeProtectionEnabled
```

---

## Did You Know?

> PowerShell execution policies are **not a security boundary**. They help prevent accidental script execution, but they should not be relied upon as a primary security control.

---

## Try It Yourself

Complete the following exercises:

1. Display Microsoft Defender status.
2. Review Defender preferences.
3. Check your execution policies.
4. Display all firewall profiles.
5. List installed machine certificates.
6. Update Defender signatures.

---

## Common Mistakes

Common mistakes include:

- Disabling Microsoft Defender without an alternative solution.
- Setting the execution policy to `Unrestricted` unnecessarily.
- Assuming execution policies prevent malicious code execution.
- Ignoring expired certificates.
- Forgetting to verify firewall profile settings.

---

## Performance Tips

- Keep Defender signatures up to date.
- Use `Get-ExecutionPolicy -List` to understand policy precedence.
- Review firewall profiles periodically.
- Audit certificates regularly to identify expired or unnecessary certificates.

---

## Version Compatibility

| Feature | Windows PowerShell 5.1 | PowerShell 7+ |
|----------|:----------------------:|:-------------:|
| Defender module | ✅ | Windows only |
| Certificate provider | ✅ | ✅ |
| Execution Policy | ✅ | ✅ |

---

## Related Commands

- `Get-MpComputerStatus`
- `Get-MpPreference`
- `Update-MpSignature`
- `Get-ExecutionPolicy`
- `Set-ExecutionPolicy`
- `Get-NetFirewallProfile`
- `Get-WinEvent`

---

## Microsoft Learn

Recommended topics:

- Microsoft Defender PowerShell module
- Get-MpComputerStatus
- Set-MpPreference
- Execution Policies
- Certificate Provider

---

## Summary

In this chapter you learned how to:

- Review Microsoft Defender status.
- Manage execution policies.
- Inspect firewall profiles.
- Work with certificates.
- Apply PowerShell to Windows security administration.

The next chapter introduces system information and hardware inventory using PowerShell.
