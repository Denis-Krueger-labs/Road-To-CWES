---
layout: log
title: "Day 45 - Stack-Based Buffer Overflow, GDB, and Database Basics"
date: 2026-05-03
topics: ["Buffer Overflow", "Stack Memory", "Shellcode", "GDB", "Exploit Development", "Databases", "SQL"]
summary: "Exploited a SUID binary via stack overflow, built working shellcode payloads, analyzed stack space after EIP overwrite, and reviewed database theory plus SQL basics."
status: complete
---

# Day 45 - Stack-Based Buffer Overflow, GDB, and Database Basics

## What I studied today

Today had two main parts:

- stack-based buffer overflow exploitation
- database theory and SQL basics

Main technical focus:

- using GDB to analyze memory and registers
- finding EIP offset with cyclic patterns
- building payloads with NOP sleds and shellcode
- generating shellcode with `msfvenom`
- understanding stack layout and memory mappings
- reviewing database fundamentals
- practicing basic SQL queries

---

## Summary of concepts

### Stack-based buffer overflow

- A buffer overflow happens when input exceeds the allocated buffer and overwrites nearby memory.
- If the overwritten memory includes `EIP`, execution flow can be controlled.
- A payload usually consists of:

```text
padding → return address → NOP sled → shellcode
````

* A NOP sled increases reliability because the return address does not need to land exactly on the shellcode.
* The stack grows downward from higher to lower memory addresses.
* Stack mappings in GDB show mapped stack size, not simply “free remaining stack space.”

---

### Database basics

I also reviewed core database concepts:

* **Data** = information about objects or processes
* **Master data / Stammdaten** = mostly stable data, such as name or address
* **Transaction data / Bewegungsdaten** = event-based data, such as orders or payments
* **Data field** = single value
* **Record / Datensatz** = complete row
* **Database (DB)** = stored data
* **DBMS** = software that manages the database
* **DBS** = database + DBMS
* **CRUD** = Create, Read, Update, Delete
* **Data model** = general concept
* **Schema** = concrete structure
* **Logical schema** = what is stored
* **Physical schema** = how it is stored
* **External level** = user/application view
* **Data independence** = changes should affect applications as little as possible
* **Object data** = actual stored contents
* **Metadata** = data about data
* **Data Dictionary** = catalog for metadata

---

## Deeper understanding

### Buffer overflow mental model

When `EIP` is overwritten, the program returns to the address I provide.

Instead of trying to hit shellcode exactly, I can place a large NOP sled and jump somewhere into that region.

```text
return address → lands in NOP sled → slides into shellcode
```

That makes exploitation much more reliable.

Important points:

* controlling `EIP` means controlling execution flow
* exact addresses are less important when the NOP sled is large enough
* GDB helps verify what actually happens in memory
* the mapped stack size is not the same thing as remaining usable stack space

---

### Database mental model

A database system is not just “some tables.”

It consists of:

```text
data + structure + management software + metadata
```

The difference between DB, DBMS, and DBS is important:

* **DB** = the actual stored data
* **DBMS** = the software managing it
* **DBS** = the whole system

SQL then becomes the language used to interact with that structure.

---

## What I actually did: Buffer Overflow

* used `pattern_offset` to find the EIP overwrite offset:

  * `2060`
* confirmed control over EIP with:

  * `0x41414141`
* built multiple payloads with:

  * padding
  * NOP sled
  * shellcode
  * return address
* generated shellcode using `msfvenom`

  * reverse shell
  * file read payload for `/root/flag.txt`
* debugged crashes in GDB:

  * inspected memory with `x/xb`
  * checked registers with `info registers`
  * analyzed memory mappings with `info proc mappings`
* brute-forced return addresses inside the NOP sled
* successfully executed payload using:

```text
0xffffd6dc
```

* calculated stack size from mappings:

```text
0x22000
```

---

## What I actually did: Databases / SQL

Practiced basic SQL commands:

```sql
SELECT
FROM
WHERE
AND
OR
ORDER BY
ASC
DESC
```

I wrote queries for:

* filtering by specific cities
* displaying only names
* combining multiple conditions
* sorting by age
* sorting by name

---

## What went well

* successfully controlled EIP
* built a working exploit payload
* understood why NOP sleds help
* debugged memory and register state in GDB
* got a working return address after testing
* database basics felt understandable
* SQL query practice went well

---

## What was confusing

* difference between stack size and remaining stack space
* why some return addresses worked and others did not
* why exploits sometimes behave differently inside and outside GDB
* HTB wording around the stack size question
* keeping database terminology clean at first

---

## Mistakes / friction

* initially calculated stack space incorrectly using ESP subtraction
* focused too much on exact addresses instead of using the NOP sled range
* spent time looking for `jmp esp` even though it was not needed
* overcomplicated payload adjustments
* had to separate “database,” “DBMS,” and “DBS” clearly

---

## What I think I understand now

* stack-based buffer overflow exploitation end-to-end
* how to calculate the correct offset to EIP
* how NOP sleds improve reliability
* how GDB helps inspect crashes and memory state
* why return addresses only need to be “good enough”
* basic database terminology
* basic SQL query structure

---

## What I need to improve

* identify return address strategies faster
* understand ASLR impact better
* practice stack visualization more
* craft payloads with less trial and error
* learn alternative exploitation techniques:

  * return-to-libc
  * ROP basics
* keep practicing SQL until queries feel automatic

---

## Plan for next session

* Intro to Assembly Language
* recall university web exploitation notes into memory
* Intro to Recon
* start Fundamentals of Web Apps
* review:

  * attack
  * cause
  * protection
* continue database / SQL practice if time allows

---

## Session info (optional)

* Duration: 5 hours deep dive + database review
* Energy: Medium 
