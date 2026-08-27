# Day 2 — Operating Systems & Linux Fundamentals

**Status:** Completed  
**Score:** 9/10  
**Date:** 2026-08-27  
**Level:** Beginner

## Objectives
- Understand what an operating system is
- Understand the kernel and its role
- Understand programs vs processes
- Understand what happens when a program runs
- Understand why Linux is important in DevOps
- Practice basic Linux commands and observe processes

## Concepts Learned

### 1. Operating System
An operating system is software that manages hardware resources and provides services/interfaces for applications and users.

```text
User / Applications
        ↓
       OS
        ↓
Hardware
```

### 2. Kernel
The kernel is the core component of an operating system. It manages important resources and provides core system functionality, including:
- CPU/process management
- Memory management
- Device management
- Filesystems
- Networking

The kernel is **not the entire operating system**.

### 3. Program vs Process
A **program** is code/instructions stored on disk.

A **process** is a running instance of a program, with resources such as memory and CPU time.

```text
app.py
  ↓ execute
PROCESS
  ↓
RAM + CPU + resources
```

The kernel manages processes; a process is not "inside" the kernel.

### 4. What Happens When Running a Program
For a command such as:

```bash
python app.py
```

a simplified flow is:

```text
Command entered in shell
        ↓
Shell asks OS to execute
        ↓
OS/kernel creates and manages a process
        ↓
Resources are provided
        ↓
Python executes app.py
        ↓
Process finishes
```

### 5. Why Linux Matters in DevOps
Linux is widely used for cloud servers, web servers, containers, Kubernetes, CI/CD systems and infrastructure. Linux is also well suited to remote administration and automation.

A graphical interface is not required for most server administration; engineers can work remotely through tools such as SSH and the terminal.

## Hands-on Practice
Basic Linux/WSL commands practiced:

```bash
whoami
pwd
ls
uname -a
ps
ps aux
```

### Observations
- `whoami` showed the current user (`root` in the learner's WSL environment).
- `pwd` showed the current working directory.
- `ls` listed the contents of the current directory.
- `uname -a` displayed Linux/kernel and system information.
- `ps` displayed processes associated with the current terminal/session.
- `ps aux` displayed a broader process listing.

### Process Experiment
Running:

```bash
sleep 60
```

created a running `sleep` process. From another terminal, `ps aux` showed the running `sleep 60` process.

An important observation was that `ps` itself is also a program. When `ps` is executed, the kernel creates a short-lived `ps` process. That process can appear in the process listing while it is collecting and displaying the snapshot. Because it finishes very quickly, its appearance can vary between runs.

```text
sleep command
      ↓
sleep process
      ↓
runs for 60 seconds
      ↓
terminates
```

## Assessment
**Result: 9/10 — Passed**

The learner demonstrated strong understanding of:
- Operating systems
- Kernel basics
- Program vs process
- Program execution flow
- Linux's role in DevOps
- Basic Linux commands
- Process observation using `ps`/`ps aux`

### Corrections / Refinements
- The kernel does more than schedule processes; it also manages memory, devices, filesystems and networking.
- A process is a running instance of a program; it is not an implementation of instructions "inside the kernel." The kernel manages the process.
- Linux's DevOps importance is broader than not requiring animations/GUI; its ecosystem, server usage, automation, tooling and infrastructure adoption are key reasons.
- Everyday work should generally not be performed as `root`; users and permissions will be covered later.

## Key Mental Model

```text
              COMPUTER
                  │
                  ▼
           Operating System
                  │
               Kernel
                  │
        ┌─────────┼─────────┐
        ↓         ↓         ↓
       CPU       RAM       Disk
        │
        ▼
     Processes
        │
   ┌────┼────┐
   ↓    ↓    ↓
Chrome Python VS Code
```

## Next Step
**Day 3 — Linux Filesystem & Navigation**

Planned concepts:
- Linux filesystem hierarchy
- `/`, `/home`, `/etc`, `/var`
- Absolute vs relative paths
- `cd`, `ls`, `mkdir`, `touch`
- Files and directories
- Navigating Linux confidently
