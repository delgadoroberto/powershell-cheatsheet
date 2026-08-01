# 12 - Remoting

## Overview

PowerShell Remoting enables administrators to securely execute commands and scripts on remote computers. Built on the Windows Remote Management (WinRM) service, it allows centralized administration, automation, and large-scale system management.

PowerShell Remoting is widely used in enterprise environments for configuration management, software deployment, incident response, and security auditing.

> **Key Takeaways**
>
> - Understand how PowerShell Remoting works.
> - Configure WinRM for remote management.
> - Execute commands on remote computers.
> - Create interactive remote sessions.
> - Apply remoting techniques for administration and cybersecurity.

---

## Quick Reference

| Cmdlet | Purpose |
|---------|---------|
| `Enable-PSRemoting` | Enable PowerShell Remoting |
| `Disable-PSRemoting` | Disable PowerShell Remoting |
| `Test-WSMan` | Test WinRM connectivity |
| `Enter-PSSession` | Start an interactive remote session |
| `Exit-PSSession` | Exit an interactive session |
| `Invoke-Command` | Execute commands remotely |
| `New-PSSession` | Create a persistent remote session |
| `Remove-PSSession` | Remove a remote session |
| `Get-PSSession` | List remote sessions |

---

## Prerequisites

Before continuing, you should:

- Complete **11 - System Information**.
- Have PowerShell Remoting enabled on the target computer.
- Ensure WinRM is running.
- Have appropriate administrative credentials.
- Verify that firewall rules allow WinRM traffic.

---

## Common Cmdlets

### `Enable-PSRemoting`

Enables PowerShell Remoting.

```powershell
Enable-PSRemoting -Force
```

---

### `Test-WSMan`

Tests WinRM connectivity.

```powershell
Test-WSMan Server01
```

---

### `Enter-PSSession`

Starts an interactive remote session.

```powershell
Enter-PSSession Server01
```

---

### `Invoke-Command`

Executes a command remotely.

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {
    Get-Service
}
```

---

### `New-PSSession`

Creates a persistent remote session.

```powershell
New-PSSession -ComputerName Server01
```

---

### `Get-PSSession`

Displays active remote sessions.

```powershell
Get-PSSession
```

---

### `Remove-PSSession`

Closes a remote session.

```powershell
Remove-PSSession -Id 1
```

---

## Syntax

General syntax:

```powershell
Verb-Noun [-Parameter] <Value>
```

Example:

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock { Get-Process }
```

---

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-ComputerName` | Specifies the target computer |
| `-Credential` | Uses alternate credentials |
| `-ScriptBlock` | Specifies the commands to execute |
| `-Session` | Uses an existing remote session |
| `-Authentication` | Specifies the authentication method |

---

## Examples

### Example 1

Verify WinRM connectivity.

```powershell
Test-WSMan Server01
```

---

### Example 2

Retrieve running services from a remote computer.

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {
    Get-Service
}
```

---

### Example 3

Retrieve operating system information remotely.

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {
    Get-ComputerInfo
}
```

---

### Example 4

Start an interactive remote session.

```powershell
Enter-PSSession Server01
```

---

### Example 5

Create a persistent session.

```powershell
$Session = New-PSSession -ComputerName Server01
```

---

### Example 6

Execute multiple commands using an existing session.

```powershell
Invoke-Command -Session $Session -ScriptBlock {
    Get-Process
    Get-Service
}
```

---

## Expected Output

Example:

```text
ComputerName : Server01

Status       Name
------       ----
Running      WinRM
Running      Spooler
Running      W32Time
```

---

## Cybersecurity Use Cases

PowerShell Remoting is commonly used for:

- Remote incident response.
- Security auditing across multiple systems.
- Collecting forensic artifacts.
- Verifying security configurations.
- Deploying security updates.
- Automating administrative tasks.
- Performing enterprise-wide compliance checks.

Example:

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {
    Get-MpComputerStatus
}
```

---

## Did You Know?

> PowerShell Remoting uses **WinRM**, which is based on the WS-Management protocol. In enterprise environments, it is commonly configured to use Kerberos authentication within Active Directory domains.

---

## Try It Yourself

Complete the following exercises:

1. Verify WinRM connectivity.
2. Enable PowerShell Remoting on a lab machine.
3. Start an interactive remote session.
4. Execute `Get-Service` remotely.
5. Retrieve operating system information from a remote computer.
6. Create and remove a persistent PowerShell session.

---

## Common Mistakes

Common mistakes include:

- Forgetting to enable PowerShell Remoting.
- Blocking WinRM traffic with firewall rules.
- Using insufficient privileges.
- Leaving unused remote sessions open.
- Running remote commands without verifying the target computer.

---

## Performance Tips

- Reuse persistent sessions for multiple commands.
- Minimize the amount of data returned from remote systems.
- Execute filtering remotely whenever possible.
- Close unused sessions after completing administrative tasks.

---

## Version Compatibility

| Feature | Windows PowerShell 5.1 | PowerShell 7+ |
|----------|:----------------------:|:-------------:|
| WinRM Remoting | ✅ | ✅ |
| SSH-based Remoting | ❌ | ✅ |

---

## Related Commands

- `Enable-PSRemoting`
- `Test-WSMan`
- `Invoke-Command`
- `Enter-PSSession`
- `New-PSSession`
- `Get-PSSession`
- `Remove-PSSession`

---

## Microsoft Learn

Recommended topics:

- PowerShell Remoting
- WinRM
- Enable-PSRemoting
- Invoke-Command
- Enter-PSSession
- New-PSSession

---

## Summary

In this chapter you learned how to:

- Configure PowerShell Remoting.
- Test WinRM connectivity.
- Execute commands remotely.
- Manage persistent remote sessions.
- Apply remoting techniques for administration and cybersecurity.

The next chapter introduces Azure administration with PowerShell.
