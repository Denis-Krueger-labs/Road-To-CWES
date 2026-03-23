# Day 05  SQL Injection Fundamentals

## What I studied today

Today I focused on:

* SQL Injection basics (SQLi)
* how databases and DBMS work
* SQL syntax and common queries
* authentication bypass via SQL injection
* different types of SQL injection

---

## Summary of concepts

SQL Injection (SQLi) happens when user input is inserted into a database query without proper validation, allowing an attacker to change the logic of that query.

Instead of being treated as data, the input is interpreted as SQL code.

This can lead to:

* bypassing authentication
* retrieving sensitive data
* modifying database content
* potentially gaining control over the system

A key idea:

> SQLi is not about “breaking the app”, but about **changing the query logic**

Example:

Original query:

```sql
SELECT * FROM users WHERE username = 'tom' AND password = '1234';
```

Injected input:

```sql
tom' OR '1'='1
```

Modified query:

```sql
SELECT * FROM users WHERE username = 'tom' OR '1'='1' AND password = '1234';
```

Since `'1'='1'` is always true, the query may return valid results and allow login.

---

## Deeper understanding (optional but recommended)

### What actually happens during SQL Injection

1. The application builds a query using user input
2. The input is inserted directly into the query string
3. If not sanitized, special characters like `'` break the structure
4. The attacker injects new logic into the query
5. The database executes the modified query

 The database does exactly what it is told — it does not know what is “intended”

---

## What I actually did (important)

### Interacting with a MySQL database

* created and managed tables:

```sql
CREATE TABLE logins ...
```

* listed databases:

```sql
SHOW DATABASES;
```

* selected a database:

```sql
USE users;
```

* inspected table structure:

```sql
DESCRIBE logins;
```

* inserted data:

```sql
INSERT INTO table_name VALUES (...);
```

* retrieved data:

```sql
SELECT * FROM table_name;
SELECT column1, column2 FROM table_name;
```

* modified tables:

```sql
ALTER TABLE logins ADD newColumn INT;
```

* updated entries:

```sql
UPDATE table_name SET column=value WHERE condition;
```

---

### Practicing queries

Example:

```sql
SELECT * FROM employees 
WHERE first_name LIKE 'Bar%' 
AND hire_date = '1990-01-01';
```

 Learned how filtering works using `LIKE` and conditions

---

### SQL Injection authentication bypass

* tested login bypass using:

```
username: tom' OR '1'='1
password: anything
```

 successfully bypassed authentication

---

### ID-based injection

* used:

```
' OR id='5')--
```

 learned how:

* parameters like `id` are often directly used in queries
* comments (`--`) can ignore the rest of the query

---

## Additional practical work

Outside the main SQLi session, I also completed an easy boot-to-root machine.

Key takeaways:
- identified a vulnerable SPIP instance
- used a public CVE path to gain initial access
- pivoted from a containerized web context to a host user
- escalated via a SUID misconfiguration

This was useful because it reinforced how version disclosure, public exploit research, local enumeration, and privilege escalation chains connect in practice.

## Additional university self-study

I also reviewed cryptography basics for university.

Topics reviewed:
- security goals: confidentiality, integrity, authenticity, non-repudiation
- what a cryptosystem is
- Caesar / shift cipher as a basic model
- XOR and the difference between XOR and a true one-time pad
- Kerckhoffs’ principle
- stream ciphers vs block ciphers

Main takeaway:
Encryption does not automatically provide every security property at once. Different goals require different mechanisms, and correctness is not the same thing as security.

---

## What went well

* understanding how SQL queries are structured
* seeing how small input changes affect full queries
* successfully performing authentication bypass
* connecting theory to actual behavior

---

## What was confusing

* confusion between `-p` (password) and `-P` (port) in MySQL
* initially not recognizing `id` as an input parameter
* sometimes focusing too much on syntax instead of logic

---

## Mistakes / friction

* skipping theory too quickly because it felt familiar
* not reading task instructions carefully
* misinterpreting query outputs due to rushing

---

## What I think I understand now

* SQL Injection works by modifying query logic
* input validation is critical to prevent injection
* databases follow instructions blindly
* authentication bypass is often just a logic flaw
* even simple injections can have major impact

---

## What I need to improve

* slow down when reading tasks and queries
* practice reconstructing full SQL queries mentally
* get more comfortable with SQL syntax
* pay attention to small details in commands and flags

---

## Plan for next session

* finish SQL Injection introduction
* start Web Fuzzing (basic level)
* focus on understanding input discovery

---

## Session info

* Duration: ~2 hours
* Energy: High
