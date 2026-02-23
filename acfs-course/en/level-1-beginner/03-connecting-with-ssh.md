---
title: "Connecting to Your VPS with SSH"
weight: 3
bookToc: true
---

# Connecting to Your VPS with SSH

## What Is SSH?

**SSH** (Secure Shell) is like a secure phone line between your laptop and your VPS. It lets you type commands on the cloud computer as if you were sitting in front of it.

### Before You Start

You need:
- Your VPS **IP address** (looks like `123.45.67.89`)
- Your VPS **password** (from the provider)
- A **terminal** program on your laptop

### Getting a Terminal

- **Mac**: Open the built-in app called "Terminal"
- **Windows**: Install [Windows Terminal](https://aka.ms/terminal) from the Microsoft Store
- **Linux**: You already have one!

### Connecting

Type this in your terminal (replace with your real IP):

```bash
ssh root@123.45.67.89
```

It will ask for your password. Type it (you won't see the characters — that's normal) and press Enter.

### You're In!

If you see something like `root@server:~#`, congratulations — you're now controlling your cloud computer.

### SSH Keys (More Secure)

Passwords can be guessed. SSH keys are much safer — they work like a digital lock and key pair.

ACFS will set up SSH keys for you during installation. After that, you won't need a password anymore.

### Key Takeaway

SSH lets you control your VPS from your laptop. You connect by typing `ssh root@YOUR_IP` in a terminal. ACFS will later set up key-based access for better security.
