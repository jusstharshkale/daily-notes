Date : 26-05=2026

# Topic - Metasploit Basics
## Objective

Understand Metasploit architecture, modules, payloads, Meterpreter sessions, staged vs stageless payloads, and basic framework-assisted exploitation workflow.

---

# 1. Metasploit Architecture & Modules

## What is Metasploit?

Metasploit is a penetration testing framework used for developing, testing, and executing exploits.

It helps automate exploitation and post-exploitation tasks.

---

## Core Architecture

Metasploit is built around modules.

### Main Module Types

#### 1. Exploit Modules

Used to exploit vulnerabilities in systems.

```text id="m1"
Example: exploit/windows/smb/ms17_010_eternalblue
```

#### 2. Payload Modules

Code executed on the target after exploitation.

```text id="m2"
Example: reverse shell, Meterpreter shell
```

#### 3. Auxiliary Modules

Used for scanning, enumeration, and fuzzing.

```text id="m3"
Example: port scanners, brute force tools
```

#### 4. Post Modules

Used after gaining access.

```text id="m4"
Example: privilege escalation, credential dumping
```

---

# 2. Payloads, Sessions & Meterpreter

## What is a Payload?

A payload is the code executed on the target after successful exploitation.

Common payloads:

* Reverse shell
* Bind shell
* Meterpreter

---

## Sessions

A session is an active connection between attacker and target after exploitation.

Check sessions:

```bash id="s1"
sessions
```

Interact with session:

```bash id="s2"
sessions -i 1
```

---

## Meterpreter Basics

Meterpreter is an advanced payload providing interactive control over the target.

### Features

* File system access
* Process control
* Command execution
* Credential dumping
* System enumeration

Example commands:

```bash id="m5"
sysinfo
getuid
pwd
ls
```

---

# 3. Staged vs Stageless Payloads

## Staged Payloads

A staged payload is delivered in multiple parts.

### Workflow

1. Small initial payload (stager) executes.
2. It downloads the full payload (stage).
3. Full functionality is loaded.

### Example

```text id="p1"
reverse_tcp (stager + stage)
```

### Pros

* Smaller initial size
* Better for limited buffer exploits

### Cons

* Requires stable connection
* More detectable in some cases

---

## Stageless Payloads

A stageless payload is delivered as a complete package in one go.

### Workflow

1. Full payload is sent at once.
2. Executes immediately.

### Example

```text id="p2"
reverse_tcp_stageless
```

### Pros

* More reliable
* Works in unstable networks

### Cons

* Larger size
* May be harder to inject in some exploits

---

## Key Difference

| Feature     | Staged                | Stageless      |
| ----------- | --------------------- | -------------- |
| Delivery    | Multiple parts        | Single payload |
| Size        | Smaller initial       | Larger         |
| Reliability | Depends on connection | More stable    |

---

# 4. Framework-Assisted Exploitation Methodology

## What is Framework-Assisted Exploitation?

Using tools like Metasploit to automate exploitation steps instead of manually crafting exploits.

---

## General Workflow

### Step 1: Reconnaissance

Identify target system and services.

### Step 2: Search Exploit

```bash id="e1"
search <service>
```

### Step 3: Select Exploit

```bash id="e2"
use exploit/...
```

### Step 4: Configure Options

```bash id="e3"
set RHOSTS <target-ip>
set RPORT <port>
set PAYLOAD <payload>
```

### Step 5: Run Exploit

```bash id="e4"
exploit
```

---

## Post-Exploitation

After gaining access:

* Check system info
* Dump credentials
* Escalate privileges
* Maintain access

---

## Why Use Metasploit?

* Faster exploitation
* Built-in payloads
* Automation of complex attacks
* Useful in labs and testing environments

---
