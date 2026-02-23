---
title: "Sandbox"
weight: 3
bookToc: true
---

# Sandbox

## Introduction

The **sandbox** is an isolated environment where DeerFlow executes code. It's like a separate computer inside your computer where the agent can experiment without risking damage to your files or system.

## Why a Sandbox?

- **Security**: code runs in an isolated environment
- **Cleanliness**: each session starts fresh
- **Reproducibility**: results don't depend on your system state
- **Auditability**: all agent actions are recorded and visible

## Sandbox Types

### Local Sandbox

Code runs directly on your machine in isolated directories.

```yaml
sandbox:
  use: src.sandbox.local:LocalSandboxProvider
```

**Pros**: fast, simple setup | **Cons**: less isolation

### Docker Sandbox

Code runs in a Docker container — fully isolated.

```yaml
sandbox:
  use: src.community.aio_sandbox:AioSandboxProvider
```

**Pros**: full isolation, security | **Cons**: requires Docker, slightly slower

### Kubernetes Sandbox

For production — each sandbox runs in a separate Kubernetes pod.

```yaml
sandbox:
  use: src.community.aio_sandbox:AioSandboxProvider
  provisioner_url: http://provisioner:8002
```

## Virtual Paths

The agent sees the file system through **virtual paths**:

| Virtual Path | Physical Location | Description |
|-------------|-------------------|-------------|
| `/mnt/user-data/workspace/` | `threads/{id}/user-data/workspace/` | Working directory |
| `/mnt/user-data/uploads/` | `threads/{id}/user-data/uploads/` | Uploaded files |
| `/mnt/user-data/outputs/` | `threads/{id}/user-data/outputs/` | Results |
| `/mnt/skills/` | `deer-flow/skills/` | Skills |

## Sandbox Tools

| Tool | Description |
|------|-------------|
| `bash` | Execute commands |
| `ls` | List files (tree format, max 2 levels) |
| `read_file` | Read file contents |
| `write_file` | Write/append to files |
| `str_replace` | String replacement |

## Sandbox Lifecycle

1. **Acquire**: sandbox is created at session start
2. **Use**: agent works in the sandbox
3. **Release**: resources are freed at session end

Managed automatically via **SandboxMiddleware**.

## Practical Example

Try:

```
Install matplotlib in the sandbox,
create a sine wave plot and save it as PNG.
Show me the result.
```

## Summary

- The sandbox ensures safe code execution
- Three types: local, Docker, Kubernetes
- The agent works with virtual paths
- Lifecycle is managed automatically
- Docker sandbox is recommended for production
