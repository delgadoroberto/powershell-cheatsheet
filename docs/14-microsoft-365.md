# 14 - Microsoft 365

## Overview

Microsoft 365 provides cloud-based productivity, collaboration, identity, and security services. PowerShell enables administrators to automate and manage many Microsoft 365 tasks through dedicated modules and APIs.

PowerShell is commonly used to manage users, groups, licenses, Exchange Online, Microsoft Teams, and Microsoft Entra ID in enterprise environments.

> **Key Takeaways**
>
> - Connect to Microsoft 365 using PowerShell.
> - Manage Microsoft 365 users and groups.
> - Review user and license information.
> - Understand Microsoft Graph PowerShell.
> - Apply PowerShell to Microsoft 365 administration and security.

---

## Quick Reference

| Cmdlet | Purpose |
|---------|---------|
| `Connect-MgGraph` | Connect to Microsoft Graph |
| `Get-MgContext` | Display the current Graph connection context |
| `Get-MgUser` | Retrieve Microsoft Entra ID users |
| `Get-MgGroup` | Retrieve Microsoft Entra ID groups |
| `Get-MgUserMemberOf` | Display groups and directory objects associated with a user |
| `Get-MgSubscribedSku` | Retrieve available Microsoft 365 licenses |
| `Get-MgOrganization` | Retrieve organization information |
| `Disconnect-MgGraph` | Disconnect from Microsoft Graph |

---

## Prerequisites

Before continuing, you should:

- Complete **09 - Active Directory**.
- Complete **13 - Azure**.
- Have access to a Microsoft 365 tenant.
- Have appropriate permissions to perform administrative tasks.
- Install the **Microsoft Graph PowerShell** module.

For installation instructions, see the official Microsoft Graph PowerShell documentation.

---

## Microsoft Graph PowerShell

Microsoft Graph PowerShell provides PowerShell cmdlets for interacting with Microsoft Graph, Microsoft's unified API for accessing Microsoft 365, Microsoft Entra ID, and other Microsoft cloud services.

The module can be installed with:

```powershell
Install-Module Microsoft.Graph -Scope CurrentUser
```

Verify the installation:

```powershell
Get-InstalledModule Microsoft.Graph
```

---

## Common Cmdlets

### `Connect-MgGraph`

Connects to Microsoft Graph.

```powershell
Connect-MgGraph
```

You can request specific permissions when required:

```powershell
Connect-MgGraph -Scopes "User.Read.All"
```

> **Note**
>
> The permissions required depend on the operation being performed. Administrative operations may require additional Microsoft Graph permissions and appropriate tenant roles.

---

### `Get-MgContext`

Displays the current Microsoft Graph session.

```powershell
Get-MgContext
```

This can be useful for verifying:

- Connected account.
- Tenant ID.
- Granted scopes.
- Authentication context.

---

### `Get-MgUser`

Retrieves Microsoft Entra ID users.

```powershell
Get-MgUser
```

---

### `Get-MgGroup`

Retrieves Microsoft Entra ID groups.

```powershell
Get-MgGroup
```

---

### `Get-MgUserMemberOf`

Displays directory objects associated with a user.

```powershell
Get-MgUserMemberOf -UserId "user@example.com"
```

---

### `Get-MgSubscribedSku`

Displays Microsoft 365 license information.

```powershell
Get-MgSubscribedSku
```

---

### `Get-MgOrganization`

Retrieves organization information.

```powershell
Get-MgOrganization
```

---

### `Disconnect-MgGraph`

Disconnects the current Microsoft Graph session.

```powershell
Disconnect-MgGraph
```

---

## Syntax

General syntax:

```powershell
Verb-Noun [-Parameter] <Value>
```

Example:

```powershell
Get-MgUser -UserId "user@example.com"
```

---

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-UserId` | Specifies a Microsoft Entra ID user |
| `-GroupId` | Specifies a Microsoft Entra ID group |
| `-Filter` | Filters returned objects |
| `-Property` | Specifies properties to retrieve |
| `-All` | Retrieves all available results |
| `-Top` | Limits the number of returned objects |
| `-Scopes` | Specifies Microsoft Graph permissions requested during authentication |

---

## Examples

### Example 1

Connect to Microsoft Graph.

```powershell
Connect-MgGraph
```

---

### Example 2

Display the current Microsoft Graph context.

```powershell
Get-MgContext
```

---

### Example 3

List Microsoft Entra ID users.

```powershell
Get-MgUser -All
```

---

### Example 4

Retrieve a specific user.

```powershell
Get-MgUser -UserId "user@example.com"
```

---

### Example 5

Display Microsoft Entra ID groups.

```powershell
Get-MgGroup -All
```

---

### Example 6

Display the groups associated with a user.

```powershell
Get-MgUserMemberOf -UserId "user@example.com"
```

---

### Example 7

Display available Microsoft 365 licenses.

```powershell
Get-MgSubscribedSku
```

---

### Example 8

Display organization information.

```powershell
Get-MgOrganization
```

---

### Example 9

Retrieve selected user properties.

```powershell
Get-MgUser -All -Property DisplayName,UserPrincipalName,AccountEnabled |
Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

---

### Example 10

Find enabled users.

```powershell
Get-MgUser -All -Property DisplayName,UserPrincipalName,AccountEnabled |
Where-Object AccountEnabled -eq $true
```

---

## Expected Output

Example:

```text
DisplayName       UserPrincipalName       AccountEnabled
-----------       -----------------       --------------
John Doe          john.doe@example.com    True
Jane Smith        jane.smith@example.com  True
```

---

## Cybersecurity Use Cases

Microsoft 365 PowerShell is commonly used for:

- Auditing cloud identities.
- Reviewing enabled and disabled accounts.
- Auditing group membership.
- Reviewing license assignments.
- Supporting identity security assessments.
- Automating Microsoft 365 security checks.
- Investigating suspicious accounts.
- Supporting incident response.

Example:

```powershell
Get-MgUser -All -Property DisplayName,UserPrincipalName,AccountEnabled |
Where-Object AccountEnabled -eq $false |
Select-Object DisplayName,UserPrincipalName
```

This can help identify disabled accounts that may require additional review or cleanup.

---

## Identity and Access Management

Microsoft 365 administration is closely connected to identity management.

Important concepts include:

- Microsoft Entra ID.
- Authentication.
- Authorization.
- Role-Based Access Control (RBAC).
- Conditional Access.
- Multi-Factor Authentication (MFA).
- Least privilege.
- Privileged Identity Management (PIM).

PowerShell can help administrators automate identity-related tasks while maintaining consistent processes across large environments.

---

## Microsoft Graph Permissions

Microsoft Graph operations are controlled through permissions.

For example:

```powershell
Connect-MgGraph -Scopes "User.Read.All"
```

The requested permissions determine which Microsoft Graph operations can be performed.

> **Security Note**
>
> Request only the permissions required for the task. Excessive permissions increase the potential impact of compromised administrative credentials or automation accounts.

---

## Did You Know?

> Microsoft Graph is Microsoft's unified API for accessing data and services across Microsoft 365, Microsoft Entra ID, and other Microsoft cloud services.

Microsoft Graph PowerShell provides a PowerShell interface to that API.

---

## Try It Yourself

Complete the following exercises:

1. Install the Microsoft Graph PowerShell module.
2. Connect to Microsoft Graph.
3. Display the current Graph context.
4. List Microsoft Entra ID users.
5. Retrieve a specific user.
6. List Microsoft Entra ID groups.
7. Review available Microsoft 365 licenses.
8. Disconnect from Microsoft Graph.

---

## Common Mistakes

Common mistakes include:

- Requesting excessive Microsoft Graph permissions.
- Running commands against the wrong tenant.
- Assuming Azure and Microsoft 365 permissions are identical.
- Forgetting to verify the current authentication context.
- Using legacy Microsoft 365 PowerShell modules when Microsoft Graph provides the required functionality.
- Hardcoding credentials in scripts.

---

## Performance Tips

- Use `-Filter` when querying large directories.
- Request only the properties required by the script.
- Use `-All` deliberately when retrieving large datasets.
- Avoid unnecessary API calls.
- Reuse authentication sessions when appropriate.
- Export relevant results for auditing and reporting.

---

## Security Best Practices

When using PowerShell to administer Microsoft 365:

1. Follow the principle of least privilege.
2. Request only required Microsoft Graph scopes.
3. Use MFA where supported.
4. Avoid storing credentials in scripts.
5. Use managed identities or secure authentication mechanisms for automation where appropriate.
6. Review administrative roles regularly.
7. Monitor privileged account activity.
8. Protect automation credentials and secrets.

---

## Version Compatibility

| Feature | Windows PowerShell 5.1 | PowerShell 7+ |
|----------|:----------------------:|:-------------:|
| Microsoft Graph PowerShell | ✅ | ✅ |
| Microsoft 365 administration | ✅ | ✅ |
| Cross-platform support | Limited | ✅ |

---

## Related Commands

- `Connect-MgGraph`
- `Disconnect-MgGraph`
- `Get-MgContext`
- `Get-MgUser`
- `Get-MgGroup`
- `Get-MgUserMemberOf`
- `Get-MgSubscribedSku`
- `Get-MgOrganization`

---

## Microsoft Learn

Recommended topics:

- Microsoft Graph PowerShell
- Microsoft Graph
- Microsoft Entra ID
- Microsoft 365 administration
- Microsoft Graph permissions
- Microsoft Graph PowerShell authentication

---

## Summary

In this chapter you learned how to:

- Connect to Microsoft Graph using PowerShell.
- Retrieve Microsoft Entra ID users and groups.
- Review Microsoft 365 license information.
- Inspect the current Graph authentication context.
- Understand Microsoft Graph permissions.
- Apply PowerShell to Microsoft 365 administration and security.

The next chapter introduces practical PowerShell one-liners for common administrative, troubleshooting, and cybersecurity tasks.
