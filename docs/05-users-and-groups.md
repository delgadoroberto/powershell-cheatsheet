# 05 - Users and Groups

## Overview

Managing users and groups is a fundamental administrative task in Windows environments. PowerShell provides cmdlets for creating, modifying, removing, and auditing local users and groups, making identity management more efficient and consistent.

Understanding how users and groups work is essential for system administration, access control, and cybersecurity.

> **Key Takeaways**
>
> - View local users and groups.
> - Create and manage user accounts.
> - Manage group membership.
> - Understand the principle of least privilege.
> - Apply identity management in administration and security scenarios.

---

## Quick Reference

| Cmdlet | Purpose |
|---------|---------|
| `Get-LocalUser` | List local users |
| `New-LocalUser` | Create a local user |
| `Set-LocalUser` | Modify a local user |
| `Remove-LocalUser` | Delete a local user |
| `Get-LocalGroup` | List local groups |
| `New-LocalGroup` | Create a local group |
| `Add-LocalGroupMember` | Add members to a group |
| `Remove-LocalGroupMember` | Remove members from a group |
| `Get-LocalGroupMember` | Display group members |

---

## Prerequisites

Before continuing, you should:

- Complete **01 - Getting Started**.
- Understand basic Windows administration.
- Run PowerShell with administrative privileges for management tasks.

---

## Common Cmdlets

### `Get-LocalUser`

Displays local user accounts.

```powershell
Get-LocalUser
```

---

### `New-LocalUser`

Creates a new local user.

```powershell
New-LocalUser -Name "LabUser"
```

---

### `Set-LocalUser`

Modifies a local user.

```powershell
Set-LocalUser -Name "LabUser" -Description "PowerShell Lab User"
```

---

### `Remove-LocalUser`

Deletes a local user.

```powershell
Remove-LocalUser -Name "LabUser"
```

---

### `Get-LocalGroup`

Lists local groups.

```powershell
Get-LocalGroup
```

---

### `Add-LocalGroupMember`

Adds a user to a local group.

```powershell
Add-LocalGroupMember -Group "Administrators" -Member "LabUser"
```

---

### `Get-LocalGroupMember`

Displays the members of a local group.

```powershell
Get-LocalGroupMember -Group "Administrators"
```

---

## Syntax

General syntax:

```powershell
Verb-Noun [-Parameter] <Value>
```

Example:

```powershell
Get-LocalUser
```

---

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-Name` | Specifies the user or group name |
| `-Group` | Specifies the target group |
| `-Member` | Specifies the user or group member |
| `-Description` | Sets a description |
| `-WhatIf` | Simulates the operation |
| `-Confirm` | Requests confirmation before executing |

---

## Examples

### Example 1

List all local users.

```powershell
Get-LocalUser
```

---

### Example 2

List all local groups.

```powershell
Get-LocalGroup
```

---

### Example 3

Display members of the Administrators group.

```powershell
Get-LocalGroupMember -Group Administrators
```

---

### Example 4

Create a new local user.

```powershell
New-LocalUser -Name "SecurityLab"
```

---

### Example 5

Add the user to the Remote Desktop Users group.

```powershell
Add-LocalGroupMember -Group "Remote Desktop Users" -Member "SecurityLab"
```

---

### Example 6

Remove the test user.

```powershell
Remove-LocalUser -Name "SecurityLab"
```

---

## Expected Output

Example:

```text
Name          Enabled Description
----          ------- -----------
Administrator True    Built-in account
Guest         False   Built-in account
SecurityLab   True    Local test account
```

---

## Cybersecurity Use Cases

PowerShell user and group management is commonly used to:

- Audit privileged accounts.
- Identify unauthorized local administrators.
- Review Remote Desktop access.
- Verify account status.
- Detect inactive or unused accounts.
- Support security assessments and incident response.

Example:

```powershell
Get-LocalGroupMember -Group Administrators
```

---

## Did You Know?

> Membership in the **Administrators** group grants extensive privileges on the local computer.
>
> Regularly reviewing privileged group membership is an important security best practice.

---

## Try It Yourself

Complete the following exercises:

1. List all local users.
2. Display all local groups.
3. Review the members of the Administrators group.
4. Create a temporary local user.
5. Add the user to a non-administrative group.
6. Remove the temporary user after testing.

---

## Common Mistakes

Common mistakes include:

- Granting administrative privileges unnecessarily.
- Forgetting to remove temporary accounts.
- Using local accounts instead of centralized identity management where appropriate.
- Deleting accounts without verifying ownership.
- Ignoring group membership during security reviews.

---

## Performance Tips

- Audit privileged groups regularly.
- Apply the principle of least privilege.
- Remove unused accounts promptly.
- Use descriptive account names for lab environments.
- Automate periodic account reviews with PowerShell.

---

## Version Compatibility

| Feature | Windows PowerShell 5.1 | PowerShell 7+ |
|----------|:----------------------:|:-------------:|
| LocalAccounts module (Windows) | ✅ | ✅* |

> *The `Microsoft.PowerShell.LocalAccounts` module is available only on Windows.

---

## Related Commands

- `Get-LocalUser`
- `New-LocalUser`
- `Set-LocalUser`
- `Remove-LocalUser`
- `Get-LocalGroup`
- `Add-LocalGroupMember`
- `Remove-LocalGroupMember`
- `Get-LocalGroupMember`

---

## Microsoft Learn

Recommended topics:

- Get-LocalUser
- New-LocalUser
- Get-LocalGroup
- Add-LocalGroupMember
- Remove-LocalGroupMember
- Microsoft.PowerShell.LocalAccounts module

---

## Summary

In this chapter you learned how to:

- Manage local users.
- Manage local groups.
- Review group membership.
- Apply the principle of least privilege.
- Perform identity management tasks using PowerShell.

The next chapter introduces networking administration and troubleshooting with PowerShell.
