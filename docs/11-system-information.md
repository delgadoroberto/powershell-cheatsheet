# 11 - System Information

## Overview

PowerShell provides powerful cmdlets for collecting detailed information about the operating system, hardware, storage, BIOS, memory, and computer configuration.

These cmdlets are widely used for inventory management, troubleshooting, automation, compliance, and cybersecurity assessments.

> **Key Takeaways**
>
> - Retrieve operating system information.
> - Display hardware details.
> - Inspect BIOS and firmware information.
> - Review storage and memory configuration.
> - Collect system information for administration and security purposes.

---

## Quick Reference

| Cmdlet | Purpose |
|---------|---------|
| `Get-ComputerInfo` | Display comprehensive system information |
| `Get-CimInstance` | Retrieve CIM/WMI information |
| `Get-ComputerInfo` | Display Windows configuration |
| `Get-Volume` | Display storage volumes |
| `Get-Disk` | Display physical disks |
| `Get-Partition` | Display partitions |
| `Get-PhysicalDisk` | Display physical storage devices |
| `Get-HotFix` | Display installed Windows updates |

---

## Prerequisites

Before continuing, you should:

- Complete **01 - Getting Started**.
- Have PowerShell 5.1 or PowerShell 7 installed.
- Run PowerShell with administrative privileges for complete hardware information.

---

## Common Cmdlets

### `Get-ComputerInfo`

Displays detailed computer information.

```powershell
Get-ComputerInfo
```

---

### `Get-CimInstance`

Retrieves operating system information.

```powershell
Get-CimInstance Win32_OperatingSystem
```

---

### `Get-Disk`

Displays physical disks.

```powershell
Get-Disk
```

---

### `Get-Volume`

Displays storage volumes.

```powershell
Get-Volume
```

---

### `Get-Partition`

Displays partitions.

```powershell
Get-Partition
```

---

### `Get-PhysicalDisk`

Displays physical storage devices.

```powershell
Get-PhysicalDisk
```

---

### `Get-HotFix`

Displays installed Windows updates.

```powershell
Get-HotFix
```

---

## Syntax

General syntax:

```powershell
Verb-Noun [-Parameter] <Value>
```

Example:

```powershell
Get-CimInstance Win32_BIOS
```

---

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-ClassName` | Specifies the CIM class |
| `-ComputerName` | Queries a remote computer |
| `-Property` | Selects specific properties |
| `-Filter` | Filters returned objects |
| `-Credential` | Uses alternate credentials |

---

## Examples

### Example 1

Display operating system information.

```powershell
Get-CimInstance Win32_OperatingSystem
```

---

### Example 2

Display BIOS information.

```powershell
Get-CimInstance Win32_BIOS
```

---

### Example 3

Display processor information.

```powershell
Get-CimInstance Win32_Processor
```

---

### Example 4

Display physical memory.

```powershell
Get-CimInstance Win32_PhysicalMemory
```

---

### Example 5

Display installed updates.

```powershell
Get-HotFix
```

---

### Example 6

Display storage volumes.

```powershell
Get-Volume
```

---

## Expected Output

Example:

```text
WindowsProductName : Windows 11 Pro
WindowsVersion     : 24H2
CsName             : WORKSTATION01
CsManufacturer     : Dell Inc.
CsModel            : Latitude 7450
BiosVersion        : Dell 1.15.0
```

---

## Cybersecurity Use Cases

PowerShell system information cmdlets are commonly used for:

- Building hardware inventories.
- Verifying operating system versions.
- Identifying missing security updates.
- Auditing BIOS versions.
- Reviewing disk encryption readiness.
- Supporting vulnerability assessments.
- Performing incident response.

Example:

```powershell
Get-HotFix |
Sort-Object InstalledOn -Descending
```

---

## Did You Know?

> `Get-CimInstance` is the recommended replacement for the older `Get-WmiObject` cmdlet because it uses the CIM standard and supports modern management technologies.

---

## Try It Yourself

Complete the following exercises:

1. Display your computer information.
2. Display the operating system version.
3. Review your BIOS information.
4. List installed Windows updates.
5. Display your storage volumes.
6. Identify the processor model.

---

## Common Mistakes

Common mistakes include:

- Using deprecated WMI cmdlets instead of CIM cmdlets.
- Collecting unnecessary information in automation scripts.
- Ignoring missing security updates.
- Running inventory scripts without appropriate permissions.
- Forgetting to verify hardware compatibility.

---

## Performance Tips

- Retrieve only the properties you need.
- Prefer `Get-CimInstance` over legacy WMI cmdlets.
- Avoid collecting full system inventories repeatedly.
- Export inventory results for future comparison.

---

## Version Compatibility

| Feature | Windows PowerShell 5.1 | PowerShell 7+ |
|----------|:----------------------:|:-------------:|
| Get-ComputerInfo | ✅ | ✅ |
| CIM cmdlets | ✅ | ✅ |
| Storage module | ✅ | Windows only |

---

## Related Commands

- `Get-ComputerInfo`
- `Get-CimInstance`
- `Get-Disk`
- `Get-Volume`
- `Get-Partition`
- `Get-PhysicalDisk`
- `Get-HotFix`

---

## Microsoft Learn

Recommended topics:

- Get-ComputerInfo
- Get-CimInstance
- CIM Cmdlets
- Get-Disk
- Get-Volume
- Get-HotFix

---

## Summary

In this chapter you learned how to:

- Retrieve operating system information.
- Collect hardware inventory.
- Inspect BIOS and storage configuration.
- Review installed Windows updates.
- Use PowerShell for system inventory and security assessments.

The next chapter introduces PowerShell Remoting for remote administration.
