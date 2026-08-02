# PowerShell Cheat Sheet

> A practical PowerShell reference with real-world commands, administration examples, and cybersecurity use cases.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Who Is This Repository For?](#who-is-this-repository-for)
- [Documentation](#documentation)
- [Repository Structure](#repository-structure)
- [Scripts](#scripts)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [Author](#author)
- [License](#license)

---

## Overview

This repository provides a practical and organized reference for learning and using PowerShell in real-world environments.

Rather than focusing only on cmdlet syntax, it emphasizes practical examples, administration tasks, troubleshooting techniques, and cybersecurity-oriented use cases.

The documentation covers Windows administration, networking, event logs, Active Directory, Windows security, PowerShell Remoting, Azure, Microsoft 365, useful one-liners, and troubleshooting.

Whether you are learning PowerShell or looking for a quick reference, this repository is designed to be easy to navigate and useful in professional environments.

---

## Features

- Practical PowerShell commands and examples
- Real-world administration tasks
- Cybersecurity-focused use cases
- Windows PowerShell 5.1 and PowerShell 7 compatibility notes
- Reusable PowerShell snippets
- Troubleshooting workflows
- Cloud and Microsoft 365 administration examples
- Beginner-friendly explanations
- References to official Microsoft documentation
- GitHub Actions for repository quality and maintenance

---

## Who Is This Repository For?

This repository is intended for:

- System Administrators
- IT Support Engineers
- Cybersecurity Professionals
- DevSecOps Engineers
- Cloud Engineers
- Students learning PowerShell
- Anyone interested in Windows automation

---

## Documentation

| Chapter | Topic | Description |
|---------|-------|-------------|
| 01 | [Getting Started](docs/01-getting-started.md) | PowerShell fundamentals and essential concepts |
| 02 | [Files and Folders](docs/02-files-and-folders.md) | File system navigation and management |
| 03 | [Processes](docs/03-processes.md) | Working with running processes |
| 04 | [Services](docs/04-services.md) | Managing Windows services |
| 05 | [Users and Groups](docs/05-users-and-groups.md) | Local user and group administration |
| 06 | [Networking](docs/06-networking.md) | Network configuration and troubleshooting |
| 07 | [Event Logs](docs/07-event-logs.md) | Reading and filtering Windows Event Logs |
| 08 | [Registry](docs/08-registry.md) | Working with the Windows Registry |
| 09 | [Active Directory](docs/09-active-directory.md) | Active Directory administration |
| 10 | [Windows Security](docs/10-windows-security.md) | Security and hardening commands |
| 11 | [System Information](docs/11-system-information.md) | Collecting system information |
| 12 | [Remoting](docs/12-remoting.md) | PowerShell Remoting fundamentals |
| 13 | [Azure](docs/13-azure.md) | Azure administration with PowerShell |
| 14 | [Microsoft 365](docs/14-microsoft-365.md) | Microsoft 365 and Microsoft Graph administration |
| 15 | [Useful One-Liners](docs/15-useful-one-liners.md) | Frequently used commands and practical one-liners |
| 16 | [Troubleshooting](docs/16-troubleshooting.md) | System diagnostics and troubleshooting workflows |

---

## Repository Structure

```text
.
├── .github/
│   ├── workflows/
│   └── ISSUE_TEMPLATE/
│
├── docs/
│   ├── 01-getting-started.md
│   ├── 02-files-and-folders.md
│   ├── 03-processes.md
│   ├── 04-services.md
│   ├── 05-users-and-groups.md
│   ├── 06-networking.md
│   ├── 07-event-logs.md
│   ├── 08-registry.md
│   ├── 09-active-directory.md
│   ├── 10-windows-security.md
│   ├── 11-system-information.md
│   ├── 12-remoting.md
│   ├── 13-azure.md
│   ├── 14-microsoft-365.md
│   ├── 15-useful-one-liners.md
│   └── 16-troubleshooting.md
│
├── images/
│
├── scripts/
│   ├── examples/
│   └── snippets/
│
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
└── SECURITY.md
```

---

## Scripts

The repository includes two categories of PowerShell scripts.

### Examples

Complete scripts demonstrating practical administrative, automation, and security tasks.

Examples include:

- Export Windows services
- Audit local users
- Find large files
- List installed software

### Snippets

Small reusable PowerShell code blocks that can easily be copied into larger scripts.

Examples include:

- Check administrator privileges
- Test TCP ports
- Write log entries
- Retrieve operating system information

---

## Roadmap

The core documentation is complete.

Future improvements may include:

- Add screenshots and visual examples
- Add real-world scenarios to selected chapters
- Expand cybersecurity-focused examples
- Add PowerShell best practices
- Expand the collection of reusable automation scripts
- Add risk classifications to potentially destructive commands
- Improve cross-references between topics
- Review commands and modules periodically for compatibility with current PowerShell and Microsoft platforms

---

## Contributing

Contributions, corrections, and suggestions are welcome.

Please read the [`CONTRIBUTING.md`](CONTRIBUTING.md) guide before opening an Issue or submitting a Pull Request.

---

## Author

### Roberto Delgado

*Cybersecurity Engineer*

Cybersecurity professional focused on cloud and infrastructure security, DevSecOps, vulnerability management, and security automation.

This repository is part of my technical portfolio and demonstrates practical PowerShell knowledge applied to system administration, troubleshooting, cloud environments, and cybersecurity workflows.

> **Practical cybersecurity. Secure automation. Continuous learning.**

---

## License

This project is licensed under the MIT License. See the [`LICENSE`](LICENSE) file for more information.
