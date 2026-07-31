# 09 - Active Directory

## Overview

Active Directory (AD) is Microsoft's directory service for managing users, groups, computers, and other resources in a Windows domain environment.

PowerShell provides the Active Directory module, allowing administrators to automate common administrative tasks, perform audits, and manage identities efficiently.

Understanding Active Directory cmdlets is essential for system administration, identity management, and enterprise cybersecurity.

> **Key Takeaways**
>
> - Query Active Directory objects.
> - Manage users, groups, and computers.
> - Search and filter directory objects.
> - Automate identity management tasks.
> - Apply Active Directory administration in cybersecurity scenarios.

---

## Quick Reference

| Cmdlet | Purpose |
|---------|---------|
| `Get-ADUser` | Retrieve Active Directory users |
| `New-ADUser` | Create a new user |
| `Set-ADUser` | Modify a user |
| `Remove-ADUser` | Delete a user |
| `Get-ADGroup` | Retrieve AD groups |
| `Add-ADGroupMember` | Add members to a group |
| `Remove-ADGroupMember` | Remove members from a group |
| `Get-ADComputer` | Retrieve computer accounts |
| `Search-ADAccount` | Search for accounts |

---

## Prerequisites

Before continuing, you should:

- Complete **05 - Users and Groups**.
- Be connected to an Active Directory domain.
- Install the **Active Directory** PowerShell module (RSAT).
- Have sufficient permissions to query or modify directory objects.

---

## Common Cmdlets

### `Get-ADUser`

Retrieves Active Directory users.

```powershell
Get-ADUser -Filter *
```

---

### `New-ADUser`

Creates a new Active Directory user.

```powershell
New-ADUser -Name "John Doe"
```

---

### `Set-ADUser`

Modifies user properties.

```powershell
Set-ADUser -Identity jdoe -Department IT
```

---

### `Remove-ADUser`

Deletes a user.

```powershell
Remove-ADUser -Identity jdoe
```

---

### `Get-ADGroup`

Retrieves Active Directory groups.

```powershell
Get-ADGroup -Filter *
```

---

### `Add-ADGroupMember`

Adds users to a group.

```powershell
Add-ADGroupMember "IT Admins" jdoe
```

---

### `Get-ADComputer`

Retrieves computer accounts.

```powershell
Get-ADComputer -Filter *
```

---

### `Search-ADAccount`

Searches for accounts matching specific criteria.

```powershell
Search-ADAccount -LockedOut
```

---

## Syntax

General syntax:

```powershell
Verb-Noun [-Parameter] <Value>
```

Example:

```powershell
Get-ADUser -Identity jdoe
```

---

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-Identity` | Specifies the target object |
| `-Filter` | Filters directory objects |
| `-SearchBase` | Limits the search scope |
| `-Properties` | Retrieves additional attributes |
| `-Server` | Specifies a domain controller |
| `-Credential` | Uses alternate credentials |

---

## Examples

### Example 1

Display all users.

```powershell
Get-ADUser -Filter *
```

---

### Example 2

Retrieve a specific user.

```powershell
Get-ADUser -Identity jdoe
```

---

### Example 3

Display disabled users.

```powershell
Search-ADAccount -AccountDisabled
```

---

### Example 4

Display locked accounts.

```powershell
Search-ADAccount -LockedOut
```

---

### Example 5

List all computers.

```powershell
Get-ADComputer -Filter *
```

---

### Example 6

Display members of a group.

```powershell
Get-ADGroupMember "Domain Admins"
```

---

## Expected Output

Example:

```text
Name          SamAccountName    Enabled
----          --------------    -------
John Doe      jdoe              True
Jane Smith    jsmith            True
```

---

## Cybersecurity Use Cases

PowerShell Active Directory cmdlets are commonly used for:

- Auditing privileged accounts.
- Reviewing group memberships.
- Detecting disabled or locked accounts.
- Finding inactive users.
- Performing identity reviews.
- Supporting incident response.
- Automating security audits.

Example:

```powershell
Search-ADAccount -LockedOut
```

---

## Did You Know?

> Most enterprise privilege escalation attacks target Active Directory rather than individual workstations. Regularly auditing privileged groups and inactive accounts significantly improves security.

---

## Try It Yourself

Complete the following exercises:

1. Display all Active Directory users.
2. Retrieve your own user account.
3. Display all computer accounts.
4. Find disabled accounts.
5. Find locked accounts.
6. Review the members of the Domain Admins group.

---

## Common Mistakes

Common mistakes include:

- Using broad filters in large environments.
- Assigning excessive privileges.
- Forgetting to review nested group memberships.
- Running administrative commands without verifying the target object.
- Deleting directory objects without confirmation.

---

## Performance Tips

- Use `-Filter` instead of retrieving every object.
- Request only the properties you need.
- Limit searches with `-SearchBase`.
- Avoid unnecessary domain-wide queries.

---

## Version Compatibility

| Feature | Windows PowerShell 5.1 | PowerShell 7+ |
|----------|:----------------------:|:-------------:|
| Active Directory module | ✅ | Windows compatibility only |

---

## Related Commands

- `Get-ADUser`
- `New-ADUser`
- `Set-ADUser`
- `Get-ADGroup`
- `Add-ADGroupMember`
- `Search-ADAccount`
- `Get-LocalUser`
- `Get-LocalGroup`

---

## Microsoft Learn

Recommended topics:

- Active Directory module
- Get-ADUser
- Get-ADGroup
- Search-ADAccount
- Get-ADComputer

---

## Summary

In this chapter you learned how to:

- Query Active Directory users and groups.
- Manage directory objects.
- Audit privileged and locked accounts.
- Automate identity management tasks.
- Apply Active Directory administration in enterprise and cybersecurity scenarios.

The next chapter introduces Windows security management using PowerShell.
