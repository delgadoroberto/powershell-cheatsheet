# Documentation Style Guide

This document defines the writing standards used throughout this repository.

The goal is to keep every chapter consistent, practical, and easy to read.

---

## General Principles

- Write for beginners without oversimplifying.
- Prefer practical explanations over theory.
- Keep paragraphs short and focused.
- Use clear and professional English.
- Avoid unnecessary jargon.
- Prioritize real-world examples.

---

## Standard Document Structure

Every document should follow this structure whenever applicable.

```text
Title

Overview

Prerequisites

Common Cmdlets

Syntax

Parameters

Examples

Expected Output

Cybersecurity Use Cases

Common Mistakes

Performance Tips

Version Compatibility

Related Commands

Microsoft Learn

Summary
```

---

## Headings

Use Markdown headings consistently.

```markdown
# Document Title

## Overview

### Example 1
```

Do not skip heading levels.

---

## Code Blocks

Always specify the language.

Correct:

```powershell
Get-Service
```

Incorrect:

```
Get-Service
```

---

## Cmdlets

Always write cmdlets using inline code.

Correct:

```markdown
`Get-Service`
```

Incorrect:

```markdown
Get-Service
```

---

## Parameters

Parameters should also use inline code.

Example:

```markdown
`-Name`

`-ComputerName`

`-Credential`
```

---

## File Names

Use inline code.

Example:

```markdown
`script.ps1`

`README.md`
```

---

## Examples

Examples should progress from simple to advanced.

Recommended order:

1. Basic example
2. Common administration task
3. Real-world scenario
4. Cybersecurity scenario

---

## Cybersecurity Use Cases

Whenever possible, include practical security-related examples.

Examples:

- Incident response
- Threat hunting
- Log analysis
- User auditing
- Privilege review
- System hardening
- Network investigation

---

## Screenshots

Only include screenshots when they add value.

Avoid screenshots that only duplicate command output.

---

## External References

Prefer official Microsoft documentation.

Additional references may include:

- Microsoft Learn
- Microsoft Docs
- PowerShell Gallery

Avoid linking to low-quality third-party websites.

---

## Version Compatibility

Indicate whether a command works with:

- Windows PowerShell 5.1
- PowerShell 7+

Mention any known differences when applicable.

---

## Writing Style

Preferred:

- Short sentences
- Active voice
- Clear explanations
- Consistent terminology

Avoid:

- Very long paragraphs
- Unnecessary repetition
- Informal language
- Slang

---

## Markdown Guidelines

- Use fenced code blocks.
- Leave one blank line between sections.
- Use tables only when they improve readability.
- Keep lists concise.
- Use inline code for commands, parameters, paths, and filenames.

---

## Summary

Following these guidelines ensures that every document in this repository remains consistent, professional, and easy to maintain.
