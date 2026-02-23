---
title: "Quick Start"
weight: 3
bookToc: true
---

# Quick Start

## Introduction

Now that everything is installed, let's launch Shannon and learn the basic commands.

## Preparing a Repository

Shannon analyzes your application's source code. Place it in the `./repos/` directory:

```bash
git clone https://github.com/your-org/your-app.git ./repos/your-app
```

For multi-repo applications (frontend + backend):

```bash
mkdir ./repos/my-app
cd ./repos/my-app
git clone https://github.com/your-org/frontend.git
git clone https://github.com/your-org/backend.git
```

## Running a Pentest

One command and Shannon gets to work:

```bash
./shannon start URL=https://your-app.com REPO=your-app
```

- `URL` — address of your running application
- `REPO` — folder name inside `./repos/`

Shannon will build containers, start the workflow, and return a session ID. The test runs in the background.

## Monitoring Progress

```bash
# Real-time logs
./shannon logs

# Query a specific workflow
./shannon query ID=shannon-1234567890

# Temporal Web UI for detailed monitoring
open http://localhost:8233
```

## Stopping Shannon

```bash
# Stop containers (preserves data)
./shannon stop

# Full cleanup (removes all data)
./shannon stop CLEAN=true
```

## Testing Local Applications

Docker containers can't reach your machine's `localhost`. Use the special address:

```bash
./shannon start URL=http://host.docker.internal:3000 REPO=my-app
```

## Summary

- You learned how to prepare a repository for analysis
- Know the main command `./shannon start`
- Can track progress through logs and the web UI
- Know how to test local applications
