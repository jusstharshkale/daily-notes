Date : 17-05-2026

# Topic - Linux Enumeration
## Objective

Understand SUID binaries, writable files, PATH hijacking, environment variables, and basic Linux enumeration techniques used during privilege escalation.

---

# 1. SUID Binaries

## What is SUID?

SUID (Set User ID) is a special permission that allows a file to run with the privileges of its owner instead of the user executing it.

If a binary is owned by `root` and has the SUID bit set, it runs with root privileges.

### Why SUID Exists

Some programs require elevated privileges to perform specific tasks.

Example:

```text id="1"
/usr/bin/passwd
```

Regular users can change their passwords because `passwd` runs with root privileges.

### Finding SUID Binaries

```bash id="2"
find / -perm -4000 2>/dev/null
```

Example output:

```text id="3"
/usr/bin/passwd
/usr/bin/sudo
/usr/bin/find
```

### Why SUID Matters

Misconfigured SUID binaries can allow privilege escalation if they execute commands or provide shell access.

### Permission Example

```text id="4"
-rwsr-xr-x
```

The `s` in the user permission field indicates the SUID bit is set.

---

# 2. Writable Files & Dangerous Permissions

## Why Writable Files Matter

Files that can be modified by low-privileged users may allow:

* Configuration manipulation
* Script modification
* Privilege escalation
* Persistence

### Finding Writable Files

```bash id="5"
find / -writable 2>/dev/null
```

### World-Writable Files

```bash id="6"
find / -perm -002 2>/dev/null
```

### World-Writable Directories

```bash id="7"
find / -type d -perm -002 2>/dev/null
```

### Dangerous Permissions

| Permission     | Meaning                               |
| -------------- | ------------------------------------- |
| 777            | Everyone can read, write, and execute |
| 666            | Everyone can read and write           |
| World-writable | Any user can modify                   |

### Why They Are Dangerous

If a privileged process uses a writable file, an attacker may be able to modify it and execute code with higher privileges.

---

# 3. PATH Hijacking

## What is PATH?

PATH is an environment variable that tells Linux where to search for executables.

View it using:

```bash id="8"
echo $PATH
```

Example:

```text id="9"
/usr/local/bin:/usr/bin:/bin
```

When a command is executed, Linux searches these directories from left to right.

---

## What is PATH Hijacking?

PATH hijacking occurs when a privileged program calls another command without specifying its full path.

Example:

```bash id="10"
system("backup")
```

Instead of:

```bash id="11"
/usr/bin/backup
```

Linux searches the PATH variable for `backup`.

If an attacker controls a directory searched before the legitimate binary, their malicious executable may run instead.

### Simplified Workflow

1. Privileged program executes a command.
2. Command path is not fully specified.
3. Linux searches PATH directories.
4. Malicious executable is found first.
5. Attacker's code executes with elevated privileges.

---

# 4. Environment Variables

## What are Environment Variables?

Environment variables store information used by processes and applications.

View all variables:

```bash id="12"
env
```

Common variables:

| Variable | Purpose                 |
| -------- | ----------------------- |
| PATH     | Executable search paths |
| HOME     | User home directory     |
| USER     | Current username        |
| SHELL    | Current shell           |
| PWD      | Current directory       |

### Display a Variable

```bash id="13"
echo $USER
```

### Why Environment Variables Matter

Applications and scripts often depend on them.

Misconfigured environment variables can contribute to:

* PATH hijacking
* Program manipulation
* Privilege escalation opportunities

---

# 5. Linux Enumeration

## What is Enumeration?

Enumeration is the process of gathering information about a system after gaining access.

The goal is to identify privilege escalation opportunities.

---

# Enumerating Users

Display current user:

```bash id="14"
whoami
```

Display logged-in users:

```bash id="15"
who
```

View local accounts:

```bash id="16"
cat /etc/passwd
```

Important users:

```text id="17"
root
www-data
mysql
```

---

# Enumerating Groups

Display current user's groups:

```bash id="18"
groups
```

Alternative:

```bash id="19"
id
```

Example:

```text id="20"
uid=1000(user) gid=1000(user) groups=1000(user),27(sudo)
```

Membership in privileged groups may provide escalation paths.

---

# Enumerating Services

View running services:

```bash id="21"
systemctl list-units --type=service
```

View running processes:

```bash id="22"
ps aux
```

Look for:

* Custom services
* Services running as root
* Misconfigured applications

---

# Enumerating Cron Jobs

## What is Cron?

Cron is a scheduler that executes tasks automatically.

### View System Cron Jobs

```bash id="23"
cat /etc/crontab
```

### Cron Directories

```text id="24"
/etc/cron.d/
/etc/cron.daily/
/etc/cron.hourly/
/etc/cron.weekly/
```

### Why Cron Matters

If a scheduled script is writable, an attacker may modify it and execute code with elevated privileges.

---

# Enumerating Permissions

Check file permissions:

```bash id="25"
ls -la
```

Check ownership:

```bash id="26"
ls -l
```

Find SUID files:

```bash id="27"
find / -perm -4000 2>/dev/null
```

Find writable files:

```bash id="28"
find / -writable 2>/dev/null
```

Understanding permissions is critical because many privilege escalation paths originate from improper access controls.

---

# Enumeration Checklist

After obtaining a shell, commonly check:

* Current user
* User groups
* SUID binaries
* Writable files
* Running services
* Cron jobs
* Installed software
* Environment variables
* Sensitive configuration files
* File and directory permissions

---

