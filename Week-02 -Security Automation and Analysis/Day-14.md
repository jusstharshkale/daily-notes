Date : 07-05-2026

# Topic - Try Hack Me --> Simple CTF room
Room Overview :
The Simple CTF room on TryHackMe is a beginner-friendly Capture The Flag challenge focused on basic enumeration, web exploitation, and privilege escalation techniques.
Objective :
-Enumerate the target machine
-Gain initial access
-Escalate privileges
-Capture user and root flags

Reconnaissance : 
Started with an Nmap scan to identify open ports and running services.
command --> nmap -sC -sV <TARGET_IP>
Open Ports Discovered - 
21 → FTP
80 → HTTP
2222 → SSH
Web enumeration revealed a vulnerable CMS running on the target.

Enumeration : 
Used Gobuster to discover hidden directories.
command --> gobuster dir -u http://<TARGET_IP> -w /usr/share/wordlists/dirb/common.txt
Discovered:
/simple
The website was running CMS Made Simple.

Exploitation :
Searched for known vulnerabilities and found an SQL Injection exploit affecting the CMS version. Used the public exploit to extract credentials and crack the password hash.
Successfully logged in via SSH:
command --> ssh <username>@<TARGET_IP> -p 2222

Privilege Escalation :
Checked sudo permissions and discovered a binary with elevated privileges.
command --> sudo -l
Leveraged the allowed binary to gain root access.

Tools Used :
1.Nmap
2.Gobuster
3.Searchsploit
4.SSH

Key Learnings :
-Importance of service enumeration
-Identifying vulnerable CMS versions
-Basic SQL Injection exploitation
-Linux privilege escalation fundamentals

Conclusion :
Simple CTF is an excellent beginner room for practicing the complete penetration testing workflow — from enumeration to privilege escalation — in a controlled environment.
