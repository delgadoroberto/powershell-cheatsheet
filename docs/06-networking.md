# 06 - Networking

## Overview

PowerShell provides a comprehensive set of networking cmdlets that simplify network configuration, troubleshooting, and diagnostics. Whether you need to verify connectivity, inspect IP configurations, resolve DNS names, or analyze TCP connections, PowerShell offers powerful built-in tools for network administration.

Understanding these cmdlets is essential for system administrators, DevOps engineers, and cybersecurity professionals responsible for maintaining secure and reliable network environments.

> **Key Takeaways**
>
> - Display network configuration information.
> - Test network connectivity.
> - Resolve DNS names.
> - Inspect active TCP connections.
> - Troubleshoot network-related issues using PowerShell.

---

## Quick Reference

| Cmdlet | Purpose |
|---------|---------|
| `Get-NetIPAddress` | Display IP address configuration |
| `Get-NetIPConfiguration` | Display network adapter configuration |
| `Get-NetAdapter` | Display network adapters |
| `Test-NetConnection` | Test network connectivity |
| `Resolve-DnsName` | Resolve DNS records |
| `Get-NetTCPConnection` | Display TCP connections |
| `Get-NetRoute` | Display routing table |
| `Get-NetFirewallProfile` | Display Windows Firewall profiles |

---

## Prerequisites

Before continuing, you should:

- Complete **01 - Getting Started**.
- Understand basic networking concepts (IP addresses, DNS, TCP/IP).
- Run PowerShell with administrative privileges when required.

---

## Common Cmdlets

### `Get-NetIPAddress`

Displays IP address information.

```powershell
Get-NetIPAddress
```

---

### `Get-NetIPConfiguration`

Displays network adapter configuration.

```powershell
Get-NetIPConfiguration
```

---

### `Get-NetAdapter`

Displays available network adapters.

```powershell
Get-NetAdapter
```

---

### `Test-NetConnection`

Tests network connectivity.

```powershell
Test-NetConnection google.com
```

---

### `Resolve-DnsName`

Resolves DNS records.

```powershell
Resolve-DnsName github.com
```

---

### `Get-NetTCPConnection`

Displays active TCP connections.

```powershell
Get-NetTCPConnection
```

---

### `Get-NetRoute`

Displays the routing table.

```powershell
Get-NetRoute
```

---

### `Get-NetFirewallProfile`

Displays Windows Firewall profile settings.

```powershell
Get-NetFirewallProfile
```

---

## Syntax

General syntax:

```powershell
Verb-Noun [-Parameter] <Value>
```

Example:

```powershell
Test-NetConnection github.com -Port 443
```

---

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-ComputerName` | Specifies the remote host |
| `-Port` | Specifies the destination port |
| `-InterfaceAlias` | Specifies a network adapter |
| `-AddressFamily` | Filters IPv4 or IPv6 |
| `-InformationLevel` | Controls the amount of information displayed |

---

## Examples

### Example 1

Display all IP addresses.

```powershell
Get-NetIPAddress
```

---

### Example 2

Display detailed network configuration.

```powershell
Get-NetIPConfiguration
```

---

### Example 3

Test HTTPS connectivity.

```powershell
Test-NetConnection github.com -Port 443
```

---

### Example 4

Resolve a DNS name.

```powershell
Resolve-DnsName microsoft.com
```

---

### Example 5

Display established TCP connections.

```powershell
Get-NetTCPConnection |
Where-Object State -eq Established
```

---

### Example 6

Display enabled network adapters.

```powershell
Get-NetAdapter |
Where-Object Status -eq Up
```

---

## Expected Output

Example:

```text
ComputerName     : github.com
RemoteAddress    : 140.82.xxx.xxx
RemotePort       : 443
InterfaceAlias   : Ethernet
TcpTestSucceeded : True
```

---

## Cybersecurity Use Cases

PowerShell networking cmdlets are useful for:

- Verifying connectivity during incident response.
- Identifying suspicious network connections.
- Auditing network interfaces.
- Investigating DNS resolution issues.
- Monitoring active TCP sessions.
- Reviewing firewall profiles.
- Supporting threat hunting activities.

Example:

```powershell
Get-NetTCPConnection |
Sort-Object LocalPort
```

---

## Did You Know?

> `Test-NetConnection` is often a better replacement for `ping` because it can test specific TCP ports, providing more meaningful diagnostics for modern network services.

---

## Try It Yourself

Complete the following exercises:

1. Display your IP configuration.
2. List all network adapters.
3. Test connectivity to `github.com`.
4. Test TCP port `443` on `microsoft.com`.
5. Display all established TCP connections.
6. Review your Windows Firewall profiles.

---

## Common Mistakes

Common mistakes include:

- Assuming ICMP is always enabled on remote systems.
- Ignoring firewall rules when troubleshooting connectivity.
- Confusing DNS resolution failures with connectivity issues.
- Running networking cmdlets without administrative privileges when required.

---

## Performance Tips

- Filter connection results before exporting them.
- Use `Test-NetConnection` instead of multiple separate commands.
- Verify DNS resolution before troubleshooting routing issues.
- Combine networking cmdlets with `Where-Object` for targeted analysis.

---

## Version Compatibility

| Feature | Windows PowerShell 5.1 | PowerShell 7+ |
|----------|:----------------------:|:-------------:|
| NetTCPIP module (Windows) | ✅ | ✅* |

> *The NetTCPIP module is available only on Windows.

---

## Related Commands

- `Get-NetIPAddress`
- `Get-NetIPConfiguration`
- `Get-NetAdapter`
- `Test-NetConnection`
- `Resolve-DnsName`
- `Get-NetTCPConnection`
- `Get-NetRoute`
- `Get-Process`

---

## Microsoft Learn

Recommended topics:

- Get-NetIPAddress
- Get-NetIPConfiguration
- Test-NetConnection
- Resolve-DnsName
- Get-NetTCPConnection
- NetTCPIP module

---

## Summary

In this chapter you learned how to:

- Display network configuration.
- Test network connectivity.
- Resolve DNS names.
- Monitor TCP connections.
- Troubleshoot common networking issues using PowerShell.

The next chapter introduces Windows Event Logs and log analysis using PowerShell.
