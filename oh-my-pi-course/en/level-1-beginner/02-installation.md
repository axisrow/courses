---
title: "Installation"
level: 1
lesson: 2
lang: en
tags: [installation, bun, npm]
---

# Installing Oh My Pi

## Introduction

There are several ways to install OMP. The recommended method is via Bun.

## Method 1: Via Bun (recommended)

Requires [Bun](https://bun.sh) >= 1.3.7.

```bash
# Install Bun (if not already installed)
curl -fsSL https://bun.sh/install | bash

# Install OMP
bun install -g @oh-my-pi/pi-coding-agent
```

## Method 2: Installer Script

**Linux / macOS:**

```bash
curl -fsSL https://raw.githubusercontent.com/can1357/oh-my-pi/main/scripts/install.sh | sh
```

**Windows (PowerShell):**

```powershell
irm https://raw.githubusercontent.com/can1357/oh-my-pi/main/scripts/install.ps1 | iex
```

## Method 3: Via mise

```bash
mise use -g github:can1357/oh-my-pi
```

## Method 4: Manual Download

Download from [GitHub Releases](https://github.com/can1357/oh-my-pi/releases/latest).

## Verify Installation

```bash
omp --version
```

## Additional Options

```bash
# Install a specific version
curl -fsSL https://raw.githubusercontent.com/can1357/oh-my-pi/main/scripts/install.sh | sh -s -- --binary --ref v3.20.1

# Install from source (main branch)
curl -fsSL https://raw.githubusercontent.com/can1357/oh-my-pi/main/scripts/install.sh | sh -s -- --source --ref main
```

Set a custom install directory with `PI_INSTALL_DIR`.

## Summary

OMP can be installed via Bun, script, mise, or manually. Bun is recommended — fast and simple.
