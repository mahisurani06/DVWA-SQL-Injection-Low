# SQL Injection on DVWA (Low Security)

## Project Overview

This project demonstrates a SQL Injection vulnerability using the Damn Vulnerable Web Application (DVWA) configured at the **Low** security level.

The objective is to understand how SQL Injection attacks work in a controlled and legal environment and to learn secure coding practices that prevent this vulnerability.

> **Note:** This project was performed only in a local DVWA lab environment for educational purposes.

---

# Objective

- Install and configure DVWA.
- Configure DVWA Security Level to Low.
- Demonstrate SQL Injection.
- Understand how insecure SQL queries can expose database information.
- Learn secure mitigation techniques.

---

# Tools Used

- Windows 11
- XAMPP
- Apache
- MySQL
- PHP
- DVWA (Damn Vulnerable Web Application)
- Google Chrome

---

# Environment

| Component | Version |
|-----------|----------|
| Operating System | Windows 11 |
| XAMPP | 8.2.x |
| Apache | Included with XAMPP |
| MySQL | Included with XAMPP |
| PHP | 8.2.x |
| DVWA | Latest GitHub Version |

---

# Installation Steps

1. Installed XAMPP.
2. Started Apache and MySQL.
3. Downloaded DVWA from GitHub.
4. Copied DVWA into:

```
C:\xampp\htdocs\dvwa
```

5. Renamed:

```
config.inc.php.dist
```

to

```
config.inc.php
```

6. Updated database configuration:

```php
$_DVWA['db_user'] = 'root';
$_DVWA['db_password'] = '';
```

7. Opened:

```
http://localhost/dvwa/setup.php
```

8. Created the database.

9. Logged into DVWA using:

```
Username: admin
Password: password
```

---

# SQL Injection Demonstration

## Step 1

Security Level:

```
Low
```

---

## Step 2

Normal Input

```
1
```

Result:

Only one user record is displayed.

---

## Step 3

SQL Injection Payload

```sql
1' OR '1'='1
```

Result:

Multiple user records are returned because the injected condition evaluates to TRUE for every row in the database.

---

# Why the Attack Works

The application directly inserts user input into an SQL query without validation or parameterized statements.

Instead of searching only for User ID 1, the injected condition:

```sql
OR '1'='1'
```

always evaluates to TRUE.

As a result, the database returns every record.

---

# Security Risks

SQL Injection can allow an attacker to:

- Read confidential data
- Modify records
- Delete information
- Bypass authentication
- Execute administrative database operations

---

# Prevention Techniques

- Use Prepared Statements
- Parameterized Queries
- Input Validation
- Stored Procedures
- Principle of Least Privilege
- Web Application Firewall (WAF)

---

# Screenshots

### Security Level

```
screenshots/01_security_low.png
```

### Normal Query

```
screenshots/02_normal_query.png
```

### SQL Injection

```
screenshots/03_sql_injection.png
```

---

# Learning Outcomes

Through this project I learned:

- How SQL Injection vulnerabilities occur.
- Why direct SQL queries are dangerous.
- How attackers manipulate SQL queries.
- How secure coding practices prevent SQL Injection.
- How DVWA can be used for cybersecurity learning.

---

# Disclaimer

This project was performed only in a local DVWA laboratory environment for educational and ethical learning purposes.

No unauthorized systems or third-party applications were targeted.