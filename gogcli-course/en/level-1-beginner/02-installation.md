---
title: "Installing gogcli"
weight: 2
bookToc: true
---

# Installing gogcli

## Choose Your Method

There are three ways to install gogcli. Pick the one that fits your system.

### Option 1: Homebrew (macOS and Linux)

If you have Homebrew installed, this is the easiest way:

```bash
brew install steipete/tap/gogcli
```

After installation, verify it works:

```bash
gog --version
```

### Option 2: Arch Linux (AUR)

If you use Arch Linux:

```bash
yay -S gogcli
```

### Option 3: Build from Source

This works on any system with Go installed:

```bash
git clone https://github.com/steipete/gogcli.git
cd gogcli
make
```

The binary will be at `./bin/gog`. You can move it to a directory in your PATH:

```bash
sudo cp ./bin/gog /usr/local/bin/
```

## Verify the Installation

Run this command to confirm everything is set up:

```bash
gog --help
```

You should see a list of available commands like `gmail`, `calendar`, `drive`, and others.

## Getting Help

gogcli has built-in help for every command:

```bash
# Top-level help
gog --help

# Help for a specific service
gog gmail --help

# Help for a specific action
gog gmail search --help

# Full expanded command list
GOG_HELP=full gog --help
```

## Shell Completions (Optional)

To get tab-completion for commands, set up shell completions:

**Bash:**
```bash
source <(gog completion bash)
```

**Zsh:**
```zsh
echo 'eval "$(gog completion zsh)"' >> ~/.zshrc
```

**Fish:**
```fish
gog completion fish > ~/.config/fish/completions/gog.fish
```

## Next Steps

In the next lesson, you'll set up authentication so gogcli can access your Google account.
