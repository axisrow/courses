---
title: "Fuzzing with RAPTOR"
weight: 2
bookToc: true
---

## Fuzzing with RAPTOR

### What Is Fuzzing?

Fuzzing is the practice of feeding random or semi-random data to a program to see if it crashes. Crashes often indicate security vulnerabilities like buffer overflows or memory corruption.

### How RAPTOR Fuzzes

RAPTOR uses **AFL++** (American Fuzzy Lop), one of the most powerful fuzzers available. Here's how it works:

1. You provide a compiled binary
2. AFL++ generates thousands of mutated inputs
3. It monitors which inputs cause new code paths to execute
4. It saves inputs that cause crashes

### Running a Fuzz Session

```
/fuzz
```

RAPTOR will ask for:
- **Binary path** — The compiled program to test
- **Duration** — How long to fuzz (default: 1 hour)
- **Seed inputs** — Example inputs to start mutating from

### Understanding Fuzz Results

After fuzzing, RAPTOR reports:

- **Unique crashes** — Distinct ways the program can be made to crash
- **Code coverage** — What percentage of the program was tested
- **Crash analysis** — AI-powered explanation of what caused each crash

### The `/crash-analysis` Command

For deeper investigation of crashes (especially in complex software like FFmpeg):

```
/crash-analysis
```

This command generates a validated root-cause analysis of a crash.

### Tips for Effective Fuzzing

1. **Provide good seed inputs** — Give examples of valid inputs so AFL++ knows the expected format
2. **Fuzz longer** — More time = more coverage = more bugs found
3. **Compile with sanitizers** — Use AddressSanitizer (ASan) to catch memory errors

### Key Takeaway

Fuzzing finds bugs that static analysis cannot. RAPTOR's integration with AFL++ makes it easy to set up and run fuzz campaigns against your binaries.
