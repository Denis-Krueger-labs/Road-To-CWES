---
layout: log
title: "Day 07 - SQL Injection Detection, UNION Attacks, and Database Enumeration"
date: 2026-03-25
topics: ["SQL Injection", "UNION SELECT", "Database Enumeration", "Oracle", "MySQL", "Burp Suite", "PortSwigger"]
summary: "Focused SQLi practice using PortSwigger labs: detection, login bypass, UNION-based extraction, DBMS fingerprinting, and database enumeration across Oracle and non-Oracle targets."
status: complete
---
# Day 07 SQL Injection Detection, UNION Attacks, and Database Enumeration

## What I studied today

Today I focused on:

- how to detect SQL injection vulnerabilities
- `UNION SELECT` attacks
- database fingerprinting and DBMS-specific behavior
- database enumeration through SQL injection

---

## Summary of concepts

- SQL injection can often be detected by sending input that changes how the backend query behaves, such as a single quote, boolean conditions, timing payloads, or DB-specific syntax.
- The most common injection point is inside the `WHERE` clause of a `SELECT` statement, but SQLi can also happen in `INSERT`, `UPDATE`, `ORDER BY`, and other parts of a query.
- `UNION SELECT` can be used to combine the application’s original query results with attacker-controlled results, which makes it possible to retrieve data from other tables.
- For a `UNION` attack to work, the number of columns and their compatible data types must match the original query.
- Different DBMS behave differently. Oracle, MySQL, and Microsoft SQL Server use different metadata tables and sometimes require slightly different syntax.
- Enumeration matters more than guessing. The clean workflow is: detect injection, determine query shape, identify reflected columns, fingerprint the database, then enumerate useful data.

---

## Deeper understanding (optional but recommended)

One of the biggest takeaways from today is that SQLi becomes much easier when I stop thinking in terms of “payloads I memorized” and start thinking in terms of **query structure**.

What really matters is:
- where my input lands in the query
- whether I am inside a string, number, or clause
- how many columns the original query has
- which columns are actually reflected in the application response
- what DBMS I am talking to

Once I understand that structure, the payloads stop feeling magical and start feeling logical.

---

## What I actually did (important)

Today I worked through a focused set of **PortSwigger SQLi labs**:

- SQL injection vulnerability in `WHERE` clause allowing retrieval of hidden data
- SQL injection vulnerability allowing login bypass
- SQL injection `UNION` attack: determining the number of columns returned by the query
- SQL injection `UNION` attack: finding a column containing text
- SQL injection `UNION` attack: retrieving data from other tables
- SQL injection `UNION` attack: retrieving multiple values in a single column
- SQL injection attack: querying the database type and version on Oracle
- SQL injection attack: querying the database type and version on MySQL and Microsoft
- SQL injection attack: listing the database contents on non-Oracle databases
- SQL injection attack: listing the database contents on Oracle

I practiced the following workflow repeatedly:

- testing whether an input is injectable
- using `'` to trigger syntax errors or anomalies
- using boolean conditions to observe response differences
- determining the number of columns with:
  - `ORDER BY`
  - `UNION SELECT NULL, NULL, ...`
- identifying which columns were visible in the response
- adapting payloads depending on the database type
- enumerating:
  - databases / schemata
  - tables
  - columns
- retrieving useful data once the structure was mapped

I also reinforced an important Oracle-specific detail:

- Oracle requires `FROM` in `SELECT` statements, even for simple injected values
- the built-in `dual` table is often used for this

Example concept:
```sql
UNION SELECT 'abc' FROM dual
````

---

## What went well

* The repetition across several PortSwigger labs helped the SQLi workflow feel more consistent instead of random.
* I got better at understanding why some errors happened instead of just seeing them as failure.
* I’m starting to understand SQLi as a structured process: detect, measure, adapt, enumerate.
* Practicing against Oracle and non-Oracle targets made the DBMS differences feel more concrete.

---

## What was confusing

* At first, PortSwigger’s SQLi section felt huge, so I wasn’t sure where to start.
* Sometimes I got the same error repeatedly and was not always sure whether the problem was:

  * column count
  * wrong data type
  * wrong syntax for the DBMS
* Encoding and DBMS-specific syntax differences still slow me down.

---

## Mistakes / friction

* I need to look more carefully at what I type, because small syntax mistakes still cost me time.
* Sometimes I still want to guess instead of enumerating cleanly first.
* A repeated error can make me want to jump ahead too quickly instead of checking assumptions one by one.

---

## What I think I understand now

* how to approach SQLi detection more methodically
* how `UNION SELECT` depends on matching the original query structure
* why reflected columns matter
* how to fingerprint the database type through behavior and syntax differences
* why enumeration is more important than clever guessing

---

## What I need to improve

* stay calmer when I hit repeated SQL errors
* debug payload structure more precisely instead of changing too many things at once
* get more comfortable with Oracle-specific differences
* keep reinforcing SQLi until the workflow feels natural under pressure

---

## Plan for next session

* start practicing **blind SQL injection**
* review SQLi in XML / encoded contexts
* continue with web fuzzing after that, not in the same overloaded session

---

## Session info (optional)

* Duration: ~2 hours
* Energy: High
