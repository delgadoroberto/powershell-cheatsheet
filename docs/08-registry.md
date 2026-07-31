# 08 - Registry

## Overview

The Windows Registry is a hierarchical database that stores configuration settings for the operating system, hardware, software, and user profiles.

PowerShell allows administrators to navigate, query, create, modify, and remove registry keys and values using built-in cmdlets, making registry management safer and more efficient than manual editing.

Understanding how to work with the Windows Registry is essential for system administration, troubleshooting, automation, and cybersecurity.

> **Key Takeaways**
>
> - Navigate the Windows Registry using PowerShell.
> - Create, modify, and remove registry keys and values.
> - Query registry information efficiently.
> - Understand registry providers and PSDrives.
> - Apply registry management in administration and cybersecurity scenarios.

---

## Quick Reference

| Cmdlet | Purpose |
|---------|---------|
| `Get-Item` | Display registry key information |
| `Get-ItemProperty` | Display registry values |
| `Set-ItemProperty` | Modify registry values |
| `New-Item` | Create registry keys |
| `New-ItemProperty` | Create registry values |
| `Remove-Item` | Delete registry keys |
| `Remove-ItemProperty` | Delete registry values |
| `Test-Path` | Verify registry paths |

---

## Prerequisites

Before continuing, you should:

- Complete **01 - Getting Started**.
- Understand basic Windows administration.
- Run PowerShell as Administrator when modifying protected registry keys.

---

## Common Cmdlets

### `Get-Item`

Displays information about a registry key.

```powershell
Get-Item HKLM:\SOFTWARE
```

---

### `Get-ItemProperty`

Displays registry values.

```powershell
Get-ItemProperty HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

---

### `Set-ItemProperty`

Modifies an existing registry value.

```powershell
Set-ItemProperty -Path HKCU:\Software\Test -Name Setting -Value Enabled
```

---

### `New-Item`

Creates a new registry key.

```powershell
New-Item -Path HKCU:\Software -Name DemoKey
```

---

### `New-ItemProperty`

Creates a registry value.

```powershell
New-ItemProperty -Path HKCU:\Software\DemoKey -Name Version -Value 1 -PropertyType String
```

---

### `Remove-Item`

Deletes a registry key.

```powershell
Remove-Item HKCU:\Software\DemoKey
```

---

### `Remove-ItemProperty`

Deletes a registry value.

```powershell
Remove-ItemProperty -Path HKCU:\Software\Test -Name Setting
```

---

## Syntax

General syntax:

```powershell
Verb-Noun [-Parameter] <Value>
```

Example:

```powershell
Get-ItemProperty HKLM:\SOFTWARE\Microsoft
```

---

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-Path` | Specifies the registry path |
| `-Name` | Specifies the registry value |
| `-Value` | Specifies the data to write |
| `-PropertyType` | Defines the registry value type |
| `-Force` | Overwrites existing items |
| `-WhatIf` | Simulates the operation |
| `-Confirm` | Requests confirmation before executing |

---

## Examples

### Example 1

Display installed software information.

```powershell
Get-ItemProperty HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

---

### Example 2

Create a registry key.

```powershell
New-Item HKCU:\Software\TestKey
```

---

### Example 3

Create a registry value.

```powershell
New-ItemProperty -Path HKCU:\Software\TestKey -Name Enabled -Value 1 -PropertyType DWord
```

---

### Example 4

Modify a registry value.

```powershell
Set-ItemProperty -Path HKCU:\Software\TestKey -Name Enabled -Value 0
```

---

### Example 5

Verify that a registry key exists.

```powershell
Test-Path HKCU:\Software\TestKey
```

---

### Example 6

Remove a registry key.

```powershell
Remove-Item HKCU:\Software\TestKey -Recurse
```

---

## Expected Output

Example:

```text
Hive: HKEY_CURRENT_USER

Name       Property
----       --------
TestKey    Enabled : 1
           Version : 1.0
```

---

## Cybersecurity Use Cases

PowerShell registry management is commonly used for:

- Auditing security settings.
- Identifying persistence mechanisms.
- Reviewing startup entries.
- Detecting unauthorized configuration changes.
- Verifying hardening settings.
- Supporting digital forensic investigations.

Example:

```powershell
Get-ItemProperty "HKLM:\Software\Microsoft\Windows\CurrentVersion\Run"
```

---

## Did You Know?

> Many forms of malware establish persistence by creating entries in registry locations such as **Run** and **RunOnce**. Regularly auditing these locations can help identify unauthorized startup programs.

---

## Try It Yourself

Complete the following exercises:

1. Display the contents of `HKCU:\Software`.
2. Create a test registry key.
3. Add a string value to the key.
4. Modify the value.
5. Verify the changes.
6. Remove the test key after completing the exercise.

---

## Common Mistakes

Common mistakes include:

- Editing the wrong registry hive.
- Deleting keys without creating a backup.
- Running destructive commands without testing.
- Confusing registry keys with registry values.
- Modifying system settings without administrative privileges.

---

## Performance Tips

- Use `Test-Path` before modifying registry keys.
- Export important registry settings before making changes.
- Use PowerShell cmdlets instead of manually editing the registry whenever possible.
- Limit registry queries to the required paths.

---

## Version Compatibility

| Feature | Windows PowerShell 5.1 | PowerShell 7+ |
|----------|:----------------------:|:-------------:|
| Registry Provider | ✅ | ✅ (Windows only) |

---

## Related Commands

- `Get-Item`
- `Get-ItemProperty`
- `Set-ItemProperty`
- `New-Item`
- `New-ItemProperty`
- `Remove-Item`
- `Remove-ItemProperty`
- `Test-Path`

---

## Microsoft Learn

Recommended topics:

- Registry Provider
- Get-ItemProperty
- Set-ItemProperty
- New-ItemProperty
- Remove-ItemProperty

---

## Summary

In this chapter you learned how to:

- Navigate the Windows Registry.
- Create and modify registry keys and values.
- Verify registry paths.
- Apply registry management in administration and cybersecurity scenarios.
- Use PowerShell to automate registry-related tasks safely.

The next chapter introduces Active Directory administration using PowerShell.
