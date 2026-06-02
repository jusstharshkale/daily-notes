Date : 28-05-2026

# Topic - Full attack workflow
## Objective

Understand the full penetration testing workflow: reconnaissance, enumeration, exploitation, privilege escalation, and documentation/reporting.

---

# 1. Reconnaissance

## What is Reconnaissance?

Reconnaissance is the initial information-gathering phase where you collect data about a target without directly interacting too deeply with it.

---

## Types of Reconnaissance

### Passive Recon

No direct interaction with the target.

Examples:

* Public websites
* DNS records
* Job postings
* GitHub leaks
* Public documents

---

### Active Recon

Direct interaction with the target system.

Examples:

* Port scanning
* Service detection
* Ping sweeps

```bash id="r1"
nmap <target-ip>
```

---

## Goal of Recon

* Identify target surface
* Discover exposed services
* Gather initial attack vectors

---

# 2. Enumeration

## What is Enumeration?

Enumeration is the process of actively extracting detailed information from identified services.

It is more in-depth than reconnaissance.

---

## Common Enumeration Areas

### System Information

```bash id="e1"
uname -a
```

### Users & Groups

```bash id="e2"
cat /etc/passwd
id
groups
```

### Services

```bash id="e3"
ps aux
systemctl list-units
```

### Network Services

* HTTP
* SMB
* FTP
* SSH

---

## Goal of Enumeration

* Identify vulnerabilities
* Find misconfigurations
* Discover credentials or entry points

---

# 3. Exploitation

## What is Exploitation?

Exploitation is the process of using a vulnerability to gain access to a system or execute commands.

---

## Common Exploitation Methods

* Public exploits (CVE-based)
* Misconfigurations
* Weak credentials
* Web application vulnerabilities

---

## Example Flow

```text id="x1"
Find vulnerability → Match exploit → Execute → Gain shell
```

---

## Tools Often Used

* Metasploit
* Searchsploit
* Custom scripts
* Manual payloads

---

## Goal of Exploitation

* Gain initial access
* Obtain shell (reverse/bind)
* Establish foothold

---

# 4. Privilege Escalation

## What is Privilege Escalation?

Privilege escalation is the process of gaining higher-level access after initial compromise.

Example:

* User → Root (Linux)
* User → Administrator (Windows)

---

## Common Linux Escalation Paths

### Weak Sudo Permissions

```bash id="p1"
sudo -l
```

### SUID Binaries

```bash id="p2"
find / -perm -4000 2>/dev/null
```

### Cron Jobs

* Writable scripts
* Root scheduled tasks

### Writable Files

* Config files
* Service scripts

### Credentials Leakage

* .bash_history
* config files
* backups

---

## Goal of Privilege Escalation

* Gain full system control
* Access restricted files
* Maintain persistence

---

# 5. Documentation and Reporting

## What is Documentation?

Documentation is the process of recording every step, finding, and result during a penetration test.

---

## What to Document

### 1. Scope

* Target systems
* IP ranges
* Permissions

---

### 2. Methodology

* Recon steps
* Enumeration steps
* Exploitation process

---

### 3. Findings

Include:

* Vulnerability name
* Severity
* Evidence
* Exploit used
* Impact

---

### 4. Proof of Concept

* Screenshots
* Commands used
* Output results

---

### 5. Remediation

Suggestions like:

* Patch vulnerabilities
* Fix misconfigurations
* Improve permissions
* Restrict services

---

## Why Reporting Matters

* Communicates risk clearly
* Helps organizations fix issues
* Provides legal documentation
* Validates work done

---

# Full Attack Lifecycle

```text id="flow1"
Reconnaissance → Enumeration → Exploitation → Privilege Escalation → Reporting
```

---
