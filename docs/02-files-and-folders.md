# 02 - Files and Folders

## Overview

Managing files and directories is one of the most common tasks performed with PowerShell.

This chapter introduces the cmdlets used to navigate the file system, create, copy, move, rename, and delete files and folders. These commands are essential for system administration, automation, and cybersecurity tasks.

> **Key Takeaways**
>
> - Navigate the file system efficiently using PowerShell.
> - Manage files and directories with built-in cmdlets.
> - Search and filter files using different criteria.
> - Verify file and folder existence before performing operations.
> - Apply file management techniques in real-world administration and security scenarios.

---

## Quick Reference

| Cmdlet | Purpose |
|---------|---------|
| `Get-ChildItem` | List files and directories |
| `Set-Location` | Change the current directory |
| `Get-Location` | Display the current directory |
| `New-Item` | Create files or directories |
| `Copy-Item` | Copy files or directories |
| `Move-Item` | Move files or directories |
| `Rename-Item` | Rename files or directories |
| `Remove-Item` | Delete files or directories |
| `Test-Path` | Verify whether a path exists |

---

## Prerequisites

Before continuing, you should:

- Understand the basics covered in **01 - Getting Started**.
- Have PowerShell 5.1 or PowerShell 7 installed.
- Have permission to access the directories you want to manage.
- Run PowerShell as Administrator when required.

---

## Common Cmdlets

### `Get-ChildItem`

Lists files and directories.

```powershell
Get-ChildItem
```

---

### `Set-Location`

Changes the current directory.

```powershell
Set-Location C:\Windows
```

---

### `New-Item`

Creates a new file or directory.

```powershell
New-Item -ItemType Directory -Name Projects
```

---

### `Copy-Item`

Copies files or folders.

```powershell
Copy-Item report.txt -Destination C:\Backup\
```

---

### `Move-Item`

Moves files or folders.

```powershell
Move-Item report.txt C:\Archive\
```

---

### `Rename-Item`

Renames a file or folder.

```powershell
Rename-Item report.txt report-old.txt
```

---

### `Remove-Item`

Deletes files or folders.

```powershell
Remove-Item report-old.txt
```

---

### `Test-Path`

Checks whether a path exists.

```powershell
Test-Path C:\Backup
```

---

## Syntax

General syntax:

```powershell
Verb-Noun [-Parameter] <Value>
```

Example:

```powershell
Copy-Item -Path report.txt -Destination C:\Backup
```

---

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-Path` | Specifies the source path |
| `-Destination` | Specifies the destination path |
| `-Filter` | Filters results |
| `-Recurse` | Includes subdirectories |
| `-Force` | Includes hidden and system items |
| `-WhatIf` | Simulates the operation |
| `-Confirm` | Requests confirmation before executing |

---

## Examples

### Example 1

List the contents of the current directory.

```powershell
Get-ChildItem
```

---

### Example 2

Display only `.log` files.

```powershell
Get-ChildItem *.log
```

---

### Example 3

Search recursively for PowerShell scripts.

```powershell
Get-ChildItem -Path C:\ -Filter *.ps1 -Recurse
```

---

### Example 4

Create a directory.

```powershell
New-Item -ItemType Directory -Name Reports
```

---

### Example 5

Copy an entire directory.

```powershell
Copy-Item C:\Reports C:\Backup -Recurse
```

---

### Example 6

Verify whether a directory exists.

```powershell
Test-Path C:\Backup
```

---

## Expected Output

Example:

```text
    Directory: C:\Projects

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        07/29/2026                  Scripts
d-----        07/29/2026                  Reports
-a----        07/29/2026            5120 report.txt
```

---

## Cybersecurity Use Cases

PowerShell file management is commonly used to:

- Search for suspicious files.
- Locate scripts across a system.
- Collect forensic artifacts.
- Back up important evidence.
- Identify hidden files.
- Automate file inventory.
- Search for recently modified files.

Example:

```powershell
Get-ChildItem C:\Users -Recurse -Force
```

---

## Did You Know?

> `Get-ChildItem` has several aliases, including `dir`, `ls`, and `gci`.
>
> While aliases are convenient in an interactive shell, using the full cmdlet name in scripts improves readability and maintainability.

---

## Try It Yourself

Complete the following exercises:

1. Display the contents of your home directory.
2. Create a folder named `PowerShellLab`.
3. Create a file inside that folder.
4. Copy the file to another directory.
5. Rename the copied file.
6. Delete the original file.
7. Verify that the copied file exists using `Test-Path`.

---

## Common Mistakes

Common mistakes include:

- Forgetting to use `-Recurse` when copying folders.
- Deleting files without confirming the path.
- Running `Remove-Item` with elevated privileges unnecessarily.
- Assuming hidden files are displayed by default.
- Overwriting files unintentionally.

---

## Performance Tips

- Use `-Filter` whenever possible instead of filtering afterwards.
- Avoid recursive searches on the entire drive unless necessary.
- Use `Test-Path` before file operations.
- Use `-WhatIf` before destructive commands.
- Prefer native cmdlets over external utilities.

---

## Version Compatibility

| Feature | Windows PowerShell 5.1 | PowerShell 7+ |
|----------|:----------------------:|:-------------:|
| File management cmdlets | ✅ | ✅ |
| Cross-platform support | ❌ | ✅ |

---

## Related Commands

- `Get-ChildItem`
- `Get-Location`
- `Set-Location`
- `Copy-Item`
- `Move-Item`
- `Rename-Item`
- `Remove-Item`
- `Test-Path`

---

## Microsoft Learn

Recommended topics:

- Working with the File System Provider
- Get-ChildItem
- Copy-Item
- Move-Item
- Remove-Item
- Test-Path

---

## Summary

In this chapter you learned how to:

- Navigate the file system.
- Create, copy, move, rename, and delete files.
- Verify paths before performing operations.
- Search recursively for files.
- Apply PowerShell file management in administration and cybersecurity scenarios.

The next chapter introduces process management using PowerShell.
