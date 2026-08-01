# 13 - Azure

## Overview

Azure PowerShell enables administrators to manage Azure resources directly from the command line. Using the **Az** PowerShell module, you can automate cloud administration, deploy resources, manage virtual machines, configure networking, and perform security-related tasks.

PowerShell is widely used in Azure environments for infrastructure automation, cloud governance, and security operations.

> **Key Takeaways**
>
> - Connect to Azure using PowerShell.
> - Manage Azure subscriptions.
> - Retrieve Azure resources.
> - Work with virtual machines and resource groups.
> - Apply Azure PowerShell to cloud administration and cybersecurity.

---

## Quick Reference

| Cmdlet | Purpose |
|---------|---------|
| `Connect-AzAccount` | Sign in to Azure |
| `Disconnect-AzAccount` | Sign out of Azure |
| `Get-AzSubscription` | List subscriptions |
| `Set-AzContext` | Select the active subscription |
| `Get-AzResourceGroup` | List resource groups |
| `Get-AzVM` | List virtual machines |
| `Get-AzResource` | List Azure resources |
| `Get-AzLocation` | List Azure regions |

---

## Prerequisites

Before continuing, you should:

- Complete **12 - Remoting**.
- Have an Azure subscription.
- Install the **Az** PowerShell module.
- Authenticate with an Azure account that has appropriate permissions.

---

## Common Cmdlets

### `Connect-AzAccount`

Authenticates to Azure.

```powershell
Connect-AzAccount
```

---

### `Get-AzSubscription`

Displays available Azure subscriptions.

```powershell
Get-AzSubscription
```

---

### `Set-AzContext`

Selects the active subscription.

```powershell
Set-AzContext -Subscription "Production"
```

---

### `Get-AzResourceGroup`

Lists resource groups.

```powershell
Get-AzResourceGroup
```

---

### `Get-AzVM`

Displays virtual machines.

```powershell
Get-AzVM
```

---

### `Get-AzResource`

Displays Azure resources.

```powershell
Get-AzResource
```

---

### `Get-AzLocation`

Displays Azure regions.

```powershell
Get-AzLocation
```

---

## Syntax

General syntax:

```powershell
Verb-Noun [-Parameter] <Value>
```

Example:

```powershell
Get-AzVM
```

---

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-Subscription` | Specifies the Azure subscription |
| `-ResourceGroupName` | Specifies a resource group |
| `-Name` | Specifies a resource name |
| `-Location` | Specifies an Azure region |
| `-Credential` | Uses alternate credentials |

---

## Examples

### Example 1

Sign in to Azure.

```powershell
Connect-AzAccount
```

---

### Example 2

Display subscriptions.

```powershell
Get-AzSubscription
```

---

### Example 3

Select a subscription.

```powershell
Set-AzContext -Subscription "Production"
```

---

### Example 4

Display resource groups.

```powershell
Get-AzResourceGroup
```

---

### Example 5

Display virtual machines.

```powershell
Get-AzVM
```

---

### Example 6

Display all Azure resources.

```powershell
Get-AzResource
```

---

## Expected Output

Example:

```text
Name              ResourceGroup     Location     PowerState
----              -------------     --------     ----------
WebServer01       Production-RG     East US      VM running
Database01        Production-RG     East US      VM running
```

---

## Cybersecurity Use Cases

Azure PowerShell is commonly used for:

- Auditing Azure resources.
- Reviewing virtual machine inventories.
- Verifying resource group configurations.
- Supporting cloud security assessments.
- Collecting cloud asset inventories.
- Automating governance tasks.
- Assisting with incident response.

Example:

```powershell
Get-AzVM |
Select-Object Name, ResourceGroupName, Location
```

---

## Did You Know?

> The **Az** PowerShell module replaced the older **AzureRM** module. New automation projects should always use the **Az** module.

---

## Try It Yourself

Complete the following exercises:

1. Sign in to Azure.
2. Display your subscriptions.
3. Select the active subscription.
4. List all resource groups.
5. Display your virtual machines.
6. Display all Azure regions.

---

## Common Mistakes

Common mistakes include:

- Working in the wrong subscription.
- Forgetting to authenticate before running commands.
- Using the deprecated AzureRM module.
- Assuming permissions are the same across subscriptions.
- Performing administrative actions without verifying the active context.

---

## Performance Tips

- Set the correct subscription before running scripts.
- Filter results whenever possible.
- Retrieve only the properties you need.
- Reuse authenticated sessions in automation workflows.

---

## Version Compatibility

| Feature | Windows PowerShell 5.1 | PowerShell 7+ |
|----------|:----------------------:|:-------------:|
| Az Module | ✅ | ✅ |
| Cross-platform support | Limited | ✅ |

---

## Related Commands

- `Connect-AzAccount`
- `Get-AzSubscription`
- `Set-AzContext`
- `Get-AzResourceGroup`
- `Get-AzVM`
- `Get-AzResource`
- `Get-AzLocation`

---

## Microsoft Learn

Recommended topics:

- Az PowerShell module
- Connect-AzAccount
- Get-AzSubscription
- Get-AzVM
- Azure Resource Manager (ARM)

---

## Summary

In this chapter you learned how to:

- Connect to Azure using PowerShell.
- Manage subscriptions and contexts.
- Retrieve Azure resources.
- Inventory virtual machines.
- Apply PowerShell to Azure administration and cloud security.

The next chapter introduces Microsoft 365 administration using PowerShell.
