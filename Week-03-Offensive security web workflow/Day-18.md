Date : 12-05-2026

# Topic - Authentication attacks
Authentication Attack Notes

Introduction:
Authentication attacks are techniques used by attackers to bypass, break, or exploit authentication mechanisms in applications, systems, or networks.

Purpose of Authentication Attacks:
To gain unauthorized access to systems.
To steal user credentials.
To impersonate legitimate users.
To escalate privileges.
To compromise sensitive information.

Common Authentication Attacks:

Brute Force Attack:
An attacker tries multiple username and password combinations repeatedly until the correct credentials are found.

Characteristics:
Uses automated tools.
Targets weak passwords.
Can take significant time depending on password complexity.

Prevention:
Use strong passwords.
Implement account lockout mechanisms.
Enable multi factor authentication.
Rate limit login attempts.

Dictionary Attack:
An attacker uses a predefined list of common passwords and phrases.

Characteristics:
Faster than brute force attacks.
Targets users with weak passwords.

Prevention:
Enforce strong password policies.
Prevent use of common passwords.
Use MFA.

Credential Stuffing:
Attackers use leaked usernames and passwords from previous breaches to access accounts.

Characteristics:
Works because users reuse passwords.
Often automated with bots.

Prevention:
Use unique passwords.
Enable MFA.
Monitor suspicious login behavior.

Password Spraying:
Attackers try a few common passwords against many accounts.

Characteristics:
Avoids account lockout.
Common in enterprise attacks.

Prevention:
Detect unusual login patterns.
Use strong password requirements.
Enable account monitoring.

Phishing Attack:
Attackers trick users into revealing login credentials through fake emails or websites.

Characteristics:
Uses social engineering.
May include fake login pages.

Prevention:
User awareness training.
Verify URLs carefully.
Use email filtering.
Enable MFA.

Session Hijacking:
An attacker steals or predicts session tokens to impersonate users.

Characteristics:
Targets active sessions.
Can occur over insecure networks.

Prevention:
Use HTTPS everywhere.
Regenerate session IDs after login.
Set secure and HttpOnly cookie flags.

Man In The Middle Attack:
An attacker intercepts communication between a user and the authentication server.

Characteristics:
Can capture credentials.
Often performed on insecure WiFi networks.

Prevention:
Use TLS encryption.
Avoid public unsecured networks.
Use VPN services.

Replay Attack:
Attackers capture valid authentication data and resend it later.

Characteristics:
Exploits lack of nonce or timestamp validation.

Prevention:
Use timestamps and nonces.
Implement token expiration.

SQL Injection in Authentication:
Attackers inject malicious SQL queries into login forms.

Example:
' OR '1'='1

Prevention:
Use prepared statements.
Validate and sanitize inputs.
Use parameterized queries.

Broken Authentication:
Improper implementation of authentication mechanisms leading to vulnerabilities.

Examples:
Weak session management.
Exposed credentials.
Predictable tokens.

Prevention:
Follow secure authentication standards.
Use secure session handling.
Regular security testing.

Multi Factor Authentication Bypass:
Attackers exploit weaknesses in MFA implementations.

Examples:
SIM swapping.
Push notification fatigue.

Prevention:
Use hardware security keys.
Monitor MFA abuse.
Use number matching MFA.

Important Security Concepts:

Authentication:
Verifying the identity of a user.

Authorization:
Determining what resources a user can access.

Session Management:
Maintaining user state after successful authentication.

Token:
A piece of data used for authentication or session tracking.

Security Best Practices:
Use HTTPS.
Implement MFA.
Store passwords using strong hashing algorithms.
Use salted hashes.
Monitor login activity.
Conduct regular penetration testing.
Apply least privilege principle.
Keep authentication libraries updated.

Strong Password Guidelines:
Minimum length of 12 characters.
Use uppercase and lowercase letters.
Include numbers and symbols.
Avoid dictionary words.
Do not reuse passwords.

Common Tools Used in Authentication Testing:
Burp Suite.
Hydra.
John the Ripper.
Hashcat.
Medusa.
Ncrack.

Legal and Ethical Reminder:
Authentication testing should only be performed on systems with proper authorization.
Unauthorized attacks are illegal and unethical.

Conclusion:
Authentication attacks remain one of the most common security threats. Proper implementation of authentication mechanisms, strong password practices, and layered security controls significantly reduce the risk of compromise.

# Topic - Using hydra for authentication attacks
What is Hydra?
**Hydra** is a fast and popular password-cracking tool used in cybersecurity for performing:

* Brute-force attacks
* Dictionary attacks
* Login credential testing

It is mainly used during:

* Penetration testing
* Red team assessments
* Security audits
* CTFs and labs

Hydra supports many protocols like:

* SSH
* FTP
* HTTP/HTTPS
* SMB
* RDP
* Telnet
* MySQL
* VNC
* SMTP
* POP3
* and many more

Basic Hydra Syntax :

```bash
hydra -l username -P passwordlist.txt <target> <protocol>
```

Meaning of Common Options :

| Option | Meaning                           |
| ------ | --------------------------------- |
| `-l`   | Single username                   |
| `-L`   | Username list file                |
| `-p`   | Single password                   |
| `-P`   | Password list file                |
| `-t`   | Number of parallel threads        |
| `-V`   | Verbose mode (shows attempts)     |
| `-f`   | Stop after first valid credential |
| `-s`   | Specify custom port               |
| `-o`   | Save output to file               |



Common Hydra Commands :

1. SSH Brute Force

```bash
hydra -l admin -P rockyou.txt ssh://192.168.1.10
```
Explanation :

* Username: `admin`
* Password list: `rockyou.txt`
* Target service: SSH
* Target IP: `192.168.1.10`

---

2. FTP Login Attack

```bash
hydra -L users.txt -P passwords.txt ftp://192.168.1.20
```

Explanation :

* Uses multiple usernames and passwords
* Targets FTP service

---

3. HTTP POST Form Attack

```bash
hydra -l admin -P rockyou.txt 192.168.1.15 http-post-form "/login.php:username=^USER^&password=^PASS^:F=incorrect"
```

Explanation :

* Used for web login forms
* `^USER^` and `^PASS^` are placeholders
* `F=incorrect` means login failed if page contains the word `incorrect`

---

4. RDP Brute Force

```bash
hydra -L users.txt -P passwords.txt rdp://192.168.1.25
```

Explanation :

* Targets Remote Desktop Protocol (RDP)
* Useful during Windows security assessments

---

5. SMB Attack

```bash
hydra -l administrator -P passwords.txt smb://192.168.1.30
```

Explanation : 

* Targets SMB shares on Windows systems
* Often used in internal network pentesting labs

Hydra may fail because of:

* Account lockout policies
* Rate limiting
* CAPTCHA protection
* Multi-factor authentication (MFA)
* Firewall rules
* Incorrect failure message detection



Quick Cheat Sheet :

| Task            | Command                                   |
| --------------- | ----------------------------------------- |
| SSH attack      | `hydra -l user -P pass.txt ssh://IP`      |
| FTP attack      | `hydra -L users.txt -P pass.txt ftp://IP` |
| RDP attack      | `hydra -L users.txt -P pass.txt rdp://IP` |
| SMB attack      | `hydra -l admin -P pass.txt smb://IP`     |
| Verbose mode    | `-V`                                      |
| Stop on success | `-f`                                      |
| Custom port     | `-s PORT`                                 |
| Save output     | `-o file.txt`                             |


Conclusion :

Hydra is one of the most important tools for credential attacks and password auditing in cybersecurity. Learning Hydra helps in understanding:

* Authentication weaknesses
* Password security
* Brute-force detection
* Account protection mechanisms

It is heavily used in real-world pentesting labs and red team exercises.
