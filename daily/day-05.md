# Day 5 — Linux Processes & Services

## 🎯 Goal
Understand how Linux runs, controls, and manages long-running applications on servers.

## 1. Foreground vs Background Processes

A foreground process occupies the terminal until it finishes.

```bash
sleep 60
```

A background process runs without making the terminal wait:

```bash
sleep 60 &
```

`&` starts the command in the background.

The shell may show:

```text
[1] 1234
```

- `[1]` = job number
- `1234` = PID

## 2. PID — Process ID

Every running process has a Process ID (PID), a unique number identifying that running process.

Commands to inspect processes:

```bash
ps
ps aux
```

A PID can be used to send signals to and manage a process.

## 3. Signals

A signal is a message sent to a process asking it to perform an action.

### SIGTERM — 15

```bash
kill 1234
```

Normally sends SIGTERM. It requests graceful termination and gives the application an opportunity to clean up.

### SIGKILL — 9

```bash
kill -9 1234
```

Forcefully terminates the process. The process does not get a normal opportunity to clean up.

### SIGINT — 2

Usually produced by `Ctrl+C` in the terminal and asks a foreground process to interrupt.

General rule: try normal termination first; use SIGKILL only when necessary.

## 4. Hands-on Process Lab

```bash
sleep 300 &
ps aux | grep sleep
kill PID
ps aux | grep sleep
```

Replace `PID` with the actual process ID found in the process list.

## 5. Why Services Exist

Manually running:

```bash
python app.py
```

is not ideal for a production application. We need applications to survive terminal logout, start after server reboot, restart when needed, and be centrally managed.

A service is a managed long-running application/process that performs a function in the background.

Examples include SSH servers, web servers, databases, Docker, and monitoring agents.

## 6. systemd

`systemd` is the system and service manager used by many modern Linux distributions.

Conceptually:

```text
systemd
   ├── nginx
   ├── ssh
   ├── docker
   └── postgresql
```

It can start, stop, restart, and monitor services, and configure services to start automatically during boot.

## 7. systemctl

`systemctl` is the main command used to interact with systemd-managed services.

Check status:

```bash
systemctl status ssh
```

Start now:

```bash
sudo systemctl start ssh
```

Stop now:

```bash
sudo systemctl stop ssh
```

Restart:

```bash
sudo systemctl restart ssh
```

Enable at boot:

```bash
sudo systemctl enable ssh
```

Key distinction:

```text
start   → start the service now
stop    → stop the service now
restart → stop and start again
enable  → configure it to start automatically at boot
status  → inspect its current state
```

## 8. Process vs Service

### Process

A currently running instance of a program.

```text
python app.py
    ↓
PID 1234
```

### Service

A managed long-running application/process, commonly controlled by systemd.

```text
systemd
   ↓
web service
   ↓
process
   ↓
PID
```

A service may involve one or more processes depending on its implementation.

## 🔥 Production Scenario

For a production application, systemd can manage the application so that it can start automatically at boot and be controlled/restarted as a service. Its status can also be inspected with `systemctl status`.

## 🧠 Assessment

1. Difference between `sleep 300` and `sleep 300 &`.
2. What is a PID?
3. What does `kill 1234` do?
4. Difference between SIGTERM and SIGKILL.
5. Why do we need services if we can run `python app.py`?
6. What is systemd?
7. Difference between `systemctl start nginx` and `systemctl enable nginx`.
8. For a production web server, what should manage the application and why?

## 📊 Assessment Result

**Score: 9.5/10 — PASSED**

Strong understanding of foreground/background processes, PIDs, signals, services, systemd, and `systemctl`.

## 🔧 Refinements / Weak Areas

- A PID identifies a running process and is used to target it with signals/manage it; it is not an access mechanism itself.
- systemd is a service/system manager, not simply a database containing all process information.

## 🛠️ Hands-on Done

- Started a background `sleep` process.
- Inspected it using `ps aux | grep sleep`.
- Identified its PID.
- Terminated it with `kill PID`.

## ➡️ Next Step

**Day 6 — Bash & Shell Scripting:** variables, command substitution, conditions, loops, scripts, and DevOps automation.
