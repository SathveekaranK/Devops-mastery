# Day 3 — Linux Filesystem & Navigation

**Status:** Completed  
**Score:** 9.5/10  
**Date:** 2026-08-27  
**Level:** Beginner

## Concepts Learned

Linux uses a single filesystem hierarchy starting at `/`, the root directory.

```text
/
├── home
├── etc
├── var
├── tmp
├── usr
├── dev
└── proc
```

### Root directory vs root user
```text
/      → root directory
root   → administrator/root user
```

### Paths
- **Absolute path:** starts from `/`, e.g. `/home/sathvee/projects`.
- **Relative path:** interpreted from the current working directory, e.g. `projects` when currently in `/home/sathvee`.

### Special path symbols
```text
/   → filesystem root
~   → current user's home directory
.   → current directory
..  → parent directory
```

`~` is not always `/home/user`; for the root user it is normally `/root`.

## Commands Practiced
```bash
pwd
ls
ls /
cd /tmp
cd ..
cd ~
mkdir devops
touch notes.txt
```

- `pwd` — prints the current working directory.
- `ls` — lists directory contents.
- `cd` — changes directory.
- `mkdir` — creates a directory.
- `touch` — creates an empty file when it does not exist and can update timestamps for an existing file.

## Hands-on Practice
The learner checked the current directory with `pwd`, listed `/` with `ls /`, navigated to `/tmp`, created a `devops` directory and file using `mkdir`, `cd`, and `touch`, and practiced moving through parent directories with `cd ..`.

Relative navigation exercises:

```text
/home/sathvee/projects/devops → /home/sathvee/projects
cd ..
```

```text
/home/sathvee/projects/devops → /home/sathvee
cd ../..
```

## Important Linux Directories
- `/home` — normal users' home directories.
- `/root` — root user's home directory.
- `/etc` — system and application configuration.
- `/var` — variable data such as logs under `/var/log`.
- `/tmp` — temporary files/data.
- `/usr` — user-space programs, libraries and related files.
- `/dev` — device-related filesystem entries.
- `/proc` — virtual filesystem exposing process and running-system information.

## Assessment
**Result: 9.5/10 — Passed ✅**

Strong understanding demonstrated in filesystem hierarchy, root directory vs root user, absolute/relative paths, `.`, `..`, `~`, `/`, basic navigation, and relative-path reasoning.

### Minor issue
One practical task used a slightly different directory/file structure than the exact requested target, but the intended `mkdir`, `cd`, and `touch` concepts were understood and the navigation exercises were completed correctly.

## Key Mental Model
```text
/
├── home/
│   └── user/
│       └── projects/
├── etc/
├── var/
│   └── log/
├── tmp/
├── usr/
├── dev/
└── proc/
```

## Next Step
**Day 4 — Linux Users, Groups & Permissions**

Topics: users and groups, ownership, `rwx` permissions, `chmod`, `chown`, root/least privilege, and why permissions matter for servers, SSH, Docker and infrastructure.
