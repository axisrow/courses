---
title: "Keeping Your System Updated"
weight: 10
bookToc: true
---

# Keeping Your System Updated

## Why Updates Matter

ACFS is actively developed. Updates bring new features, security fixes, and improvements to your tools and agents.

### Updating ACFS

```bash
acfs update
```

This single command:
- Pulls the latest ACFS code
- Updates configuration files
- Refreshes tool versions
- Keeps your custom settings intact

### Checking System Health

```bash
acfs doctor
```

Run this periodically (like a health checkup). It verifies:
- All tools are installed and working
- Versions are current
- Configuration is correct
- No conflicts exist

### Updating Individual Tools

Most tools update themselves, but you can also update them manually:

```bash
# Update Bun (JavaScript runtime)
bun upgrade

# Update Rust
rustup update

# Update Python packages
uv self update
```

### Pinning Versions for Stability

For important projects, you might want to pin ACFS to a specific version:

```bash
# Install a specific tagged version
ACFS_REF=v0.5.0 curl -fsSL "..." | bash -s -- --yes --mode vibe
```

This ensures your setup doesn't change unexpectedly.

### Key Takeaway

Run `acfs update` to get the latest improvements. Run `acfs doctor` to check system health. For critical work, pin to a specific version with `ACFS_REF`.
