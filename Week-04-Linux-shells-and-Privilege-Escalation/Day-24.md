Date : 22-05-2026

# Topic - Automated Enumeration

## Objective

Understand how to use LinPEAS for privilege escalation enumeration, interpret findings correctly, compare manual and automated investigation methods, and prioritize potential escalation vectors.

---

# 1. What is LinPEAS?

## Overview

LinPEAS (Linux Privilege Escalation Awesome Script) is an enumeration tool designed to identify potential privilege escalation opportunities on Linux systems.

Its purpose is to automate common checks that security professionals would normally perform manually.

LinPEAS does **not** exploit vulnerabilities automatically. It only highlights potential findings that require further investigation.

---

## Why Use LinPEAS?

Manual enumeration can be time-consuming and easy to overlook.

LinPEAS helps identify:

* SUID binaries
* Writable files
* Cron jobs
* Running services
* Sensitive credentials
* Interesting permissions
* Kernel information
* Environment variables
* Misconfigurations

### Typical Workflow

1. Gain initial shell access.
2. Transfer or execute LinPEAS.
3. Review findings.
4. Validate findings manually.
5. Prioritize likely escalation paths.

---

# 2. Running LinPEAS

## Basic Execution

After transferring the script:

```bash id="1"
chmod +x linpeas.sh
./linpeas.sh
```

Or:

```bash id="2"
bash linpeas.sh
```

The script performs hundreds of checks and categorizes findings.

---

## Understanding Output

LinPEAS uses color coding to highlight potentially interesting results.

Important rule:

> A highlighted result is not automatically a privilege escalation vulnerability.

Every finding must be verified manually.

---

# 3. Interpreting Findings

## Why Interpretation Matters

Automation identifies possibilities, not guarantees.

Example:

LinPEAS reports:

```text id="3"
Writable file found
```

Questions to ask:

* Is the file actually used by a privileged process?
* Can I modify it?
* Will modifications affect execution?
* Does it lead to code execution?

Without answering these questions, the finding may be useless.

---

## Example: SUID Binary

LinPEAS discovers:

```text id="4"
/usr/bin/find
```

Do not immediately assume exploitation is possible.

Instead investigate:

```bash id="5"
ls -l /usr/bin/find
```

Determine:

* Is SUID enabled?
* Is the binary vulnerable?
* Can it be abused?

The finding is only valuable if it creates a practical escalation path.

---

## Example: Writable Script

LinPEAS discovers:

```text id="6"
/opt/backup.sh
```

Next steps:

```bash id="7"
ls -l /opt/backup.sh
```

Questions:

* Who owns the script?
* Is it executed automatically?
* Is it referenced by a cron job?
* Does root execute it?

Only then can you determine its significance.

---

# 4. Manual vs Automated Enumeration

## Automated Enumeration

Tools:

* LinPEAS
* LinEnum
* Linux Exploit Suggester

### Advantages

* Fast
* Comprehensive
* Reduces human error
* Identifies common misconfigurations

### Disadvantages

* Produces large amounts of data
* Can generate false positives
* Requires interpretation
* May miss context-specific issues

---

## Manual Enumeration

Performed using Linux commands.

Examples:

```bash id="8"
id
```

```bash id="9"
find / -perm -4000 2>/dev/null
```

```bash id="10"
cat /etc/crontab
```

### Advantages

* Better understanding of the system
* More accurate context analysis
* Improved troubleshooting
* Builds stronger enumeration skills

### Disadvantages

* Slower
* Easier to miss findings
* Requires experience

---

## Best Practice

Use both approaches together.

```text id="11"
Manual Enumeration
        +
Automated Enumeration
        =
Best Coverage
```

Automation finds candidates.

Manual investigation confirms them.

---

# 5. Prioritizing Findings

## Why Prioritization Matters

LinPEAS may generate hundreds of findings.

Not all findings deserve equal attention.

Focus on items most likely to provide privilege escalation.

---

## High-Priority Findings

### SUID Binaries

Check:

```bash id="12"
find / -perm -4000 2>/dev/null
```

Reason:

* Frequently abused
* Direct escalation opportunities

---

### Writable Scripts Executed by Root

Examples:

* Backup scripts
* Cron scripts
* Maintenance scripts

Reason:

* Code may execute with elevated privileges

---

### Misconfigured Cron Jobs

Check:

```bash id="13"
cat /etc/crontab
```

Reason:

* Scheduled execution can provide escalation paths

---

### Dangerous Permissions

Examples:

```text id="14"
777 permissions
World-writable files
World-writable directories
```

Reason:

* May allow modification of privileged resources

---

### Sensitive Credentials

Look for:

```text id="15"
Passwords
SSH Keys
Database Credentials
API Tokens
```

Reason:

* Can lead to lateral movement or privilege escalation

---

# 6. Validating Findings

## What is Validation?

Validation is the process of confirming that a finding is actually exploitable.

A finding is not useful until it has been verified.

---

## Validation Process

### Step 1

Identify the finding.

Example:

```text id="16"
Writable backup script
```

### Step 2

Confirm permissions.

```bash id="17"
ls -l backup.sh
```

### Step 3

Determine execution context.

Questions:

* Who executes it?
* When is it executed?
* Does it run as root?

### Step 4

Assess impact.

Questions:

* Can commands be injected?
* Can files be modified?
* Does execution lead to elevated privileges?

Only after these steps should the finding be considered a valid escalation vector.

---

# Common Beginner Mistakes

### Mistake 1

Trusting every LinPEAS finding.

### Mistake 2

Ignoring manual verification.

### Mistake 3

Focusing on low-value findings.

### Mistake 4

Running tools without understanding the output.

### Mistake 5

Looking for exploits before performing proper enumeration.

---



---
 simply running tools.
