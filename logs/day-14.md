---
layout: log
title: "Day 14 — PHP Filters, Wrappers, and Extending LFI to RCE"
date: 2026-04-01
topics: ["LFI", "PHP Filters", "PHP Wrappers", "RCE", "ffuf", "Web Security"]
summary: "Low-energy session focused on PHP filters and wrappers, using LFI for source disclosure and extending it to remote code execution."
status: complete
---
# Day 14 – PHP Filters, Wrappers, and Extending LFI to RCE

## What I studied today

Today I focused on:

- PHP filters and wrappers
- extending LFI into source disclosure and RCE
- identifying PHP configuration files
- using different wrappers (`filter`, `data`, `input`, `expect`)

---

## Summary of concepts

- PHP wrappers allow interaction with different input/output streams inside PHP applications.
- They are often used to extend Local File Inclusion (LFI) into more powerful attacks.
- `php://filter` is commonly used for **source code disclosure**, especially with base64 encoding.
- Some wrappers can allow **code execution**, depending on configuration and enabled features.
- Understanding PHP configuration (e.g. `allow_url_include`) is critical for knowing what is possible.

---

## Deeper understanding (optional but recommended)

The important distinction I am starting to understand:

> Not all wrappers do the same thing.

### 1. `php://filter`
- used for **reading files safely**
- often combined with:
```

php://filter/read=convert.base64-encode/resource=config.php

```
- main purpose → **source disclosure**

### 2. `data://`
- used to inject **inline data**
- can be used for RCE if:
- `allow_url_include = On`
- example idea:
- inject PHP code directly into the include

### 3. `php://input`
- reads raw HTTP request body
- can be used to inject PHP code via POST requests
- useful when input is passed directly to an include

### 4. `expect://`
- allows command execution
- only works if the `expect` extension is enabled (rare)

### Key idea

- `filter` → read files
- `data` / `input` → inject code
- `expect` → direct command execution (rare but powerful)

This helps decide **which wrapper to try and when**.

---

## What I actually did (important)

- Used `ffuf` to fuzz for additional PHP files
- Used `php://filter` to read the source code of `configure.php`
- Extracted useful information (including a hidden flag) from the source
- Used LFI + `data` wrapper to build a simple web shell
- Achieved remote code execution through the vulnerable include
- Completed the HTB module on **Learning Process**

---

## What went well

- I used LFI methodically instead of guessing
- I adapted my approach instead of getting stuck
- I took more time to understand each step instead of rushing
- I successfully extended LFI → source disclosure → RCE

---

## What was confusing

- the difference between `data`, `input`, and `expect` wrappers at first
- when exactly each wrapper is usable (depends heavily on config)
- why I still feel restless even though I am clearly sick

---

## Mistakes / friction

- still struggling to fully rest even when my body needs it
- low energy made it harder to think clearly at times

---

## What I think I understand now

- LFI can often be extended beyond file reading if the environment allows it
- PHP wrappers are context-dependent and rely on configuration
- Source disclosure is often the first step before escalation
- Choosing the right wrapper is about understanding **what the application allows**

---

## What I need to improve

- actually resting and sleeping instead of pushing until I crash
- reinforcing when to use each wrapper through more practice
- staying calm and systematic even with low energy

---

## Plan for next session

- finish file inclusion topic fully
- rest properly
- recover before pushing into harder material

---

## Session info (optional)

- Duration: ~1 hour
- Energy: Low (still sick lol)

---

## Guardian

⠀⠀⣠⡶⠂⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀             \
⠀⣰⣿⠃⠀⠀⠀⠀⠀⠀⠀⢀⣀⡀⠀⠀⠀⠀⠀⠀⠀\
⢸⣿⣯⠀⠀⠀⠀⠀⠀⢠⣴⣿⣿⣿⣿⣦⠀⠀⠀⠀⠀\
⢼⣿⣿⣆⠀⢀⣀⣀⣴⣿⣿⣿⠋⠀⠀⠀⠀⠀⠀⠀⠀\
⢸⣿⣿⣿⣿⣿⣿⣿⠿⠿⣿⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀\
⠀⢻⣿⠋⠙⢿⣿⣿⡀⠀⣿⣷⣄⠀⠀⠀⠀⠀⠀⠀⠀\
⠀⢸⠿⢆⣀⣼⣿⣿⣿⣿⡏⠀⢹⠀⠀⠀⠀⠀⠀⠀⠀\
⠀⠀⡀⣨⡙⠟⣩⣙⣡⣬⣴⣤⠏⠀⠀⠀⠀⠀⠀⣀⡀ \
⠀⠀⠙⠿⣿⣿⣿⣿⣿⣿⣿⣧⠀⠀⠀⣀⣤⣾⣿⣿⡇ \
⠀⠀⠀⠀⠀⢀⣿⣿⣿⣿⣿⣿⣇⠀⢸⣿⣿⠿⠿⠛⠃ \
⠀⠀⠀⠀⢠⣿⣿⢹⣿⢹⣿⣿⣿⢰⣿⠿⠃⠀⠀⠀⠀\
⠀⢀⣀⣤⣿⣿⣿⣿⣿⣿⣿⣿⣿⣷⡛⠀⠀⠀⠀⠀⠀\
⠀⠻⠿⣿⣿⣿⣿⣿⣿⣿⣿⡿⠿⠿⠛⠓⠀⠀⠀⠀⠀\
⠀⠀⠀⠀⠀⠀⠀⠉⠀⠉⠈⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀
