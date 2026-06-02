Date : 16-05-2026

# Topic - Reverse Shells

# Reverse Shells, Bind Shells, Netcat & Linux Fundamentals

## Objective

Understand reverse shells, bind shells, listeners, shell stabilization, and basic Linux interaction commonly encountered in penetration testing labs and CTFs.

---

# 1. Reverse Shells

## What is a Reverse Shell?

A reverse shell is a connection where the **target (victim)** initiates a connection back to the **attacker**, providing remote command execution.

Instead of the attacker connecting to the target, the target "calls back" to the attacker.

### Reverse Shell Workflow

#### Step 1: Attacker Starts a Listener

```bash
nc -lvnp 4444
```

The attacker waits for incoming connections on port 4444.

#### Step 2: Victim Executes a Reverse Shell Payload

The payload creates a connection to the attacker's IP and port.

#### Step 3: Victim Connects Back

```text
Victim ---------> Attacker
```

The connection is outbound from the victim.

#### Step 4: Shell Is Established

The victim's shell is attached to the connection, allowing the attacker to run commands remotely.

### Why Reverse Shells Are Popular

* Often bypass inbound firewall restrictions.
* The target initiates the connection.
* Commonly used in real-world assessments and CTFs.

### Components of a Reverse Shell

* Listener
* Payload
* Network connection
* Command shell (bash, sh, zsh, etc.)

---

# 2. Bind Shells

## What is a Bind Shell?

A bind shell opens a listening port on the target system. The attacker connects directly to that port to gain shell access.

### Bind Shell Workflow

#### Step 1: Victim Opens a Listening Port

```bash
nc -lvnp 4444 -e /bin/bash
```

#### Step 2: Attacker Connects

```bash
nc <victim-ip> 4444
```

#### Step 3: Shell Is Established

Commands entered by the attacker execute on the victim system.

```text
Attacker ---------> Victim
```

### Advantages

* Simple setup.
* Easy to understand.

### Disadvantages

* Requires an open inbound port.
* Often blocked by firewalls.
* Easier to detect through scanning.

---

# 3. Reverse Shell vs Bind Shell

| Feature                      | Reverse Shell | Bind Shell |
| ---------------------------- | ------------- | ---------- |
| Connection Initiated By      | Victim        | Attacker   |
| Listener Location            | Attacker      | Victim     |
| Firewall Evasion             | Better        | Worse      |
| Common in Labs               | Very Common   | Common     |
| Requires Open Port on Victim | No            | Yes        |

### Quick Memory Trick

**Reverse Shell:** Target calls attacker.

**Bind Shell:** Attacker calls target.

---

# 4. Netcat (nc)

## What is Netcat?

Netcat is a networking utility often called the "Swiss Army Knife of Networking."

Common uses:

* Port listening
* Client connections
* File transfers
* Banner grabbing
* Reverse shells
* Bind shells

### Creating a Listener

```bash
nc -lvnp 4444
```

Options:

* `-l` → Listen mode
* `-v` → Verbose output
* `-n` → No DNS resolution
* `-p` → Specify port

### Why Learn Netcat?

Many shell connections in labs and CTFs are established using Netcat.

---

# 5. Shell Stabilization

## Why Stabilize a Shell?

Basic reverse shells are often limited and may lack:

* Tab completion
* Command history
* Interactive program support
* Proper terminal handling

```bash
python3 -c 'import pty; pty.spawn("/bin/bash")'
```

### Additional Stabilization

```text
Ctrl + Z
```

```bash
stty raw -echo
fg
```

This improves terminal responsiveness and shell interaction.

---

# 6. Linux Shell Interaction

## What is a Shell?

A shell is a command interpreter that allows users to communicate with the operating system.

Common shells:

* Bash
* Sh
* Zsh
* Fish

Bash is the most commonly encountered shell in Linux environments.

---

# 7. Essential Linux Commands

## whoami

Displays the current user.

```bash
whoami
```

Useful for determining privilege level.

---

## pwd

Displays the current working directory.

```bash
pwd
```

Example:

```text
/home/user
```

---

## ls

Lists files and directories.

```bash
ls
```

Useful options:

```bash
ls -l
```

Detailed view.

```bash
ls -la
```

Include hidden files.

---

## cat

Displays file contents.

```bash
cat file.txt
```

Commonly used to read:

* Configuration files
* Scripts
* Notes
* Logs

---

## find

Searches for files and directories.

```bash
find . -name "*.txt"
```

Example:

```bash
find / -name id_rsa 2>/dev/null
```

Useful during enumeration to locate:

* Credentials
* Keys
* Config files
* Logs

---

