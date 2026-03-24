---
layout: log
title: "Day 06 — SQL Injection: UNION, Enumeration, and File Access"
date: 2026-03-24
topics: ["SQL Injection", "UNION SELECT", "INFORMATION_SCHEMA", "MySQL", "File Read", "File Write", "Webshell", "Docker"]
summary: "A long SQLi-heavy day focused on UNION-based enumeration, schema discovery, file access through SQL injection, and turning database access into code execution. Also included a separate machine involving Docker-related privilege escalation."
status: complete
---
# Day 06  SQL Injection: UNION, Enumeration, and File Access

## What I studied today

Today I focused on:

- UNION-based SQL injection
- database enumeration through `INFORMATION_SCHEMA`
- file read / file write through SQL injection
- applying SQLi in a longer black-box style assessment

---

## Summary of concepts

- SQL injection happens when user input is inserted into a SQL query without proper validation, allowing an attacker to change the logic of the query.
- `UNION SELECT` can be used to combine the original query result with attacker-controlled output, which makes it possible to extract data from other tables or metadata sources.
- For a `UNION` injection to work, the number of selected columns must match the original query.
- A common workflow is:
  1. confirm injection
  2. find column count
  3. find which columns are reflected in the page
  4. enumerate databases, tables, and columns
  5. extract useful data
- If the database user has high privileges, SQLi may go beyond data extraction and allow file reads or even file writes on the server.

---

## Deeper understanding (optional but recommended)

One important thing I understood more clearly today is that **SQLi is really about reconstructing query logic**.

It is not enough to memorize payloads like `' OR 1=1-- -`.

To use SQLi properly, I need to think about:
- what the original query probably looks like
- where my input is inserted
- whether I am inside a string, number, or clause
- how to close the current context cleanly
- how to comment out the rest of the original query

For `UNION` injection, there is another layer:
- the application’s original `SELECT` statement defines the number of columns
- my injected `UNION SELECT` must match that structure
- then I need to identify which of those columns are actually reflected back to me in the response

That makes SQLi much more of a logic puzzle than a copy-paste exercise.

---

## What I actually did (important)

- Practiced basic SQL interaction in MySQL:
  - listed databases
  - switched between databases
  - described table structures
  - inserted, selected, updated, altered, and dropped data
- Worked with queries like:
  - `SHOW DATABASES;`
  - `USE <database>;`
  - `DESCRIBE <table>;`
  - `SELECT * FROM <table>;`
  - `ALTER TABLE ...`
  - `UPDATE ... WHERE ...`

- Solved SQL filtering tasks using conditions such as:
  - `LIKE`
  - `AND`
  - `OR`

- Practiced SQL injection authentication bypass with `OR`-based payloads.

- Worked through a larger SQLi skill assessment and used `UNION SELECT` to:
  - determine the number of columns
  - identify reflected columns
  - enumerate schemata
  - enumerate tables and columns
  - identify a useful database and application files

- Used payloads in the style of:
  - `... UNION SELECT ... FROM INFORMATION_SCHEMA.SCHEMATA ...`
  - `... UNION SELECT ... FROM INFORMATION_SCHEMA.TABLES ...`
  - `... UNION SELECT ... database() ...`

- Followed the chain far enough to:
  - locate useful source code / configuration paths
  - extract sensitive information through SQLi
  - abuse file-write capability to place a simple PHP webshell
  - use the shell to retrieve the challenge flag

- Also completed a separate machine earlier in the day. That was outside the SQLi module itself, but still useful practical work:
  - exploited a vulnerable LimeSurvey path to get RCE
  - used that foothold to pivot into SSH as a normal user
  - learned enough Docker-specific behavior to understand the escalation path
  - escalated to root through a Docker-related abuse path  
  Main takeaway from that machine: unfamiliarity with Docker slowed me down more than the initial exploitation itself.

---

## What went well

- I understood the theory of SQLi better once I started actually applying it.
- The `UNION SELECT` workflow made more sense after using it repeatedly in a real assessment.
- I was able to move from simple injection into actual database enumeration and finally into file access.
- Even though the assessment was long and frustrating, I still got through the full chain and learned from it.

---

## What was confusing

- The black-box assessment was much messier than the earlier examples, especially because the vulnerable input point was not where I first expected it to be.
- I still find it easy to lose track of the original query shape when the injection chain becomes longer.
- File-read and file-write SQLi are conceptually clear, but in practice I still need more repetition before they feel natural.
- I was surprised by how much harder the assessment felt compared to the earlier theory sections.

---

## Mistakes / friction

- I studied for way too long while already exhausted, which made me much sloppier than necessary.
- I was not debugging my SQL queries carefully enough and sometimes rushed instead of checking assumptions.
- I made tired mistakes like mixing up payload purpose and trying to force the wrong next step too early.
- I focused too much on the pain of the assessment and started interpreting that as “I’m bad at SQLi,” which is not actually the same thing.
- I let a “just finish it” mindset turn a useful session into a six-hour marathon.

---

## What I think I understand now

- SQLi is not just about login bypass; it can become a full application compromise if the database privileges are too broad.
- `UNION SELECT` requires matching the original query structure, which means column counting and reflected-column discovery are essential steps.
- Metadata tables like `INFORMATION_SCHEMA` are extremely useful for enumerating the database environment.
- File read and file write through SQLi can turn a database issue into server-level access.
- Harder SQLi assessments are mostly about staying methodical, not about using magical payloads.

---

## What I need to improve

- Practice reconstructing the original query mentally before I try payloads.
- Get more fluent with `UNION SELECT` so the workflow feels less effortful.
- Train SQLi in shorter, sharper sessions instead of huge exhaustion marathons.
- Slow down and read both the task and the output more carefully.
- Do extra repetition with SQLi labs so this topic stops feeling like my weakest point.

---

## Plan for next session

- continue SQL Injection practice
- do one or two focused SQLi labs for repetition
- keep the next SQLi session shorter and more controlled than today

---

## Session info (optional)

- Duration: ~6 hours total with a food break
- Energy: Extremely low by the end
