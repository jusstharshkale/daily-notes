Date : 25-05-2026

# Topic - Misconfiguration Exploiation
## Objective

Understand weak sudo permissions, cron job exploitation, insecure service configurations, and privilege escalation opportunities caused by poor operational security.

---

# 1. Weak Sudo Permissions

## What is Sudo?

`sudo` allows users to execute commands as another user, usually `root`.

Check sudo permissions:

```bash
sudo -l
```

### Dangerous Configurations

* `NOPASSWD: ALL`
* Running commands as root without restrictions
* Access to dangerous binaries

### Common Dangerous Binaries

```text
bash
sh
vim
nano
less
find
python
perl
tar
```

If these can be run with sudo, they may provide a path to root access.

---

# 2. Cron Job Exploitation

## What is Cron?

Cron is a scheduler that automatically runs tasks at specific times.

Check cron jobs:

```bash
cat /etc/crontab
```

### Cron Exploitation Workflow

1. Identify a cron job.
2. Check the executed script.
3. Verify if it is writable.
4. Modify the script.
5. Wait for cron to execute it.

### Common Weaknesses

* Writable scripts
* Writable cron directories
* Scripts running as root
* Insecure PATH usage

---

# 3. Insecure Service Configurations

## What is a Service?

A service is a background process that performs system functions.

View running services:

```bash
systemctl list-units --type=service
```

View running processes:

```bash
ps aux
```

### Common Misconfigurations

* Services running as root
* Writable service files
* Writable executables
* Hardcoded credentials in configs

### Things to Check

```text
/etc/systemd/system/
/opt/
/etc/
```

---

# 4. Privilege Escalation Through Poor Operational Security

## What is Poor OpSec?

Poor operational security often exposes sensitive information that can assist in privilege escalation.

### Common Examples

* Passwords stored in files
* SSH private keys
* Sensitive backups
* Configuration files
* Command history

### Useful Files

```text
.bash_history
.env
config.php
backup.zip
database.sql
```

### Searching for Passwords

```bash
grep -Ri "password" / 2>/dev/null
```

---

# Quick Enumeration Checklist

### Sudo Permissions

```bash
sudo -l
```

### Cron Jobs

```bash
cat /etc/crontab
```

### Running Processes

```bash
ps aux
```

### Users & Groups

```bash
id
```

### Writable Files

```bash
find / -writable 2>/dev/null
```

---
