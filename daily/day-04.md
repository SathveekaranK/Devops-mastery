# Day 4 — Linux Users, Groups & Permissions

## Status
- Completed
- Score: 9.5/10
- Confidence: 9.5/10

## What I Learned

### 1. Linux Users
Linux uses users to control access to files, directories, processes, services, and system resources.

Every process runs under a user.

`root` is the superuser account. It has broad privileges and can access protected files, change system configuration, manage software/services, and manage users.

Important principle: **least privilege** — use only the privileges required for the task. Avoid doing everyday work as root because mistakes can cause large system damage.

> `/root` is the root user's home directory, while `root` is also the name of the superuser account. `/` is the filesystem root directory. These are different concepts.

### 2. Groups
A group is a collection of users. Permissions can be granted to a group so multiple users can share access without configuring each user individually.

### 3. Linux Permission Structure
Example:

```text
-rw-r--r-- 1 root root ... test.txt
```

The first character indicates the file type. The next nine characters contain permissions in three groups:

```text
rw- r-- r--
│   │   └── others
│   └────── group
└────────── owner
```

For files:
- `r` = read contents
- `w` = modify contents
- `x` = execute

### 4. Ownership
After the permission bits, `ls -l` shows the owner and group.

```text
-rw-r--r-- 1 root root ...
              │    └── group
              └────── owner
```

The owner does not have to be root; any appropriate user can own a file.

### 5. chmod
`chmod` changes file or directory permissions.

Example:

```bash
chmod u+x script.sh
```

This adds execute permission for the owner.

#### Numeric permissions

```text
r = 4
w = 2
x = 1
```

Therefore:

```text
7 = rwx = 4+2+1
5 = r-x = 4+1
0 = ---
```

Example:

```bash
chmod 755 script.sh
```

means:

```text
owner  = 7 = rwx
group  = 5 = r-x
others = 5 = r-x
```

Result:

```text
-rwxr-xr-x
```

### 6. chown
`chown` changes ownership.

Example:

```bash
chown alice:developers file.txt
```

This changes the owner to `alice` and group to `developers`.

### 7. Directory Permissions — Important
`r`, `w`, and `x` behave differently for directories.

For a directory:

- `r` → list the directory's entries
- `w` → create/delete/rename entries, subject to other restrictions
- `x` → enter/traverse the directory

Important distinction: directory `w` does **not** directly mean modifying the contents of a file inside it. File permissions control file contents.

## Hands-on Lab

```bash
cd /tmp
mkdir permissions-lab
cd permissions-lab
touch secret.txt
ls -l
chmod 600 secret.txt
ls -l
chmod 644 secret.txt
ls -l
touch script.sh
chmod 755 script.sh
ls -l
```

Expected examples:

```text
chmod 600 secret.txt → -rw-------
chmod 644 secret.txt → -rw-r--r--
chmod 755 script.sh  → -rwxr-xr-x
```

## Assessment

1. **Normal user vs root:** Normal users have limited privileges; root has broad system privileges. Root is the superuser, not simply the default Linux user.
2. **Groups:** Groups organize users and allow permissions to be assigned to multiple users efficiently.
3. **`-rwxr-x---`:** Owner has read/write/execute; group has read/execute; others have no permissions. The owner does not necessarily have to be root.
4. **Permissions:** `r` = read, `w` = write, `x` = execute.
5. **755:** `7 = 4+2+1 = rwx`, `5 = 4+1 = r-x`, `5 = 4+1 = r-x`.
6. **chmod vs chown:** `chmod` changes permissions; `chown` changes ownership.
7. **Why not always root:** Root has powerful privileges, so accidental commands can damage the system or protected data.
8. **Directory permissions:** `r` lists entries, `w` allows entry creation/deletion/renaming, and `x` allows entering/traversing.
9. **chmod 600:** Owner gets read/write; group and others get no permissions.

## Weak Areas / Refinements
- Clarified that `root` is the superuser account, not necessarily the default user.
- Clarified that the file owner is not necessarily root.
- Refined the exact meaning of `r`, `w`, and `x` on directories.

## Next Step
Day 5 — Linux Processes & Services: background processes, signals, `kill`, `systemd`, services, and how applications stay running on servers.
