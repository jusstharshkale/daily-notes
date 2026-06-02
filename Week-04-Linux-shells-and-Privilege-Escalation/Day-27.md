Date : 27-05-2026

# Topic - Exploit Research
## Objective

Understand CVEs, version-based vulnerabilities, Searchsploit usage, exploit compatibility, and why available exploits may not always work in real scenarios.

---

# 1. CVEs and Version-Based Vulnerabilities

## What is a CVE?

A CVE (Common Vulnerabilities and Exposures) is a publicly documented security vulnerability in software or hardware.

Format:

```text id="c1"
CVE-YYYY-NNNN
```

Example:

```text id="c2"
CVE-2017-0144 (EternalBlue)
```

---

## Version-Based Vulnerabilities

Many exploits depend on specific software versions.

If a service version is vulnerable, it may allow:

* Remote code execution
* Privilege escalation
* Information disclosure

### Example Flow

1. Identify service version
2. Match with known CVE
3. Check exploit availability
4. Validate applicability

---

## Identifying Versions

```bash id="c3"
nmap -sV <target-ip>
```

or:

```bash id="c4"
service --version
```

---

# 2. Searchsploit Usage

## What is Searchsploit?

Searchsploit is a local database tool for searching exploit code from Exploit-DB.

---

## Basic Usage

### Search by Keyword

```bash id="s1"
searchsploit apache 2.4
```

### Search by CVE

```bash id="s2"
searchsploit CVE-2017-0144
```

---

## Viewing Exploit Code

```bash id="s3"
searchsploit -x <exploit-path>
```

---

## Copy Exploit Locally

```bash id="s4"
searchsploit -m <exploit-path>
```

---

## Why Searchsploit is Useful

* Offline exploit database
* Fast searching
* CVE and software-based lookup
* Helps during initial enumeration

---

# 3. Exploit Matching and Compatibility

## What is Exploit Matching?

Matching involves checking whether a known exploit actually applies to the target system.

---

## Key Matching Factors

### 1. Version Match

Exploit must match exact or compatible software version.

Example:

```text id="m1"
Apache 2.4.49 vulnerability
```

If target runs 2.4.50, exploit may fail.

---

### 2. OS Compatibility

Some exploits are OS-specific:

* Linux
* Windows
* Unix variants

---

### 3. Architecture

Check system architecture:

* x86
* x64

---

### 4. Configuration Dependency

Even correct versions may be patched or hardened.

---

### 5. Service Behavior

Custom builds or modified services may break exploit assumptions.

---

# 4. Why Exploit Availability Does NOT Guarantee Success

## Common Misconception

Just because an exploit exists does not mean it will work.

---

## Reasons Exploits Fail

### 1. Patched Systems

The vulnerability may already be fixed.

---

### 2. Incorrect Version Detection

Service banners may be:

* Hidden
* Misleading
* Customized

---

### 3. Misconfiguration Differences

Exploit assumes default configuration, but real systems differ.

---

### 4. Environment Constraints

* Firewalls
* SELinux/AppArmor
* Limited permissions
* Network restrictions

---

### 5. Exploit Instability

Some exploits:

* Crash services
* Require timing conditions
* Depend on specific inputs

---

### 6. Incomplete Exploits

Some public exploits are:

* Proof-of-concept only
* Outdated
* Not production-ready

---

# Exploitation Workflow (Realistic Approach)

### Step 1: Enumeration

Identify services and versions.

```bash id="w1"
nmap -sV <target>
```

---

### Step 2: Research

Search for CVEs and exploits.

```bash id="w2"
searchsploit <service>
```

---

### Step 3: Validate

Check:

* Version accuracy
* Exploit requirements
* System conditions

---

### Step 4: Test Carefully

Run exploit in controlled way.

---

### Step 5: Adjust

Modify exploit if needed or find alternative path.

---
