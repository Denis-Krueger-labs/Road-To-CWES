---
layout: log
title: "Day 16 - File Inclusion Mastery, RFI, Poisoning, and Bug Bounty Fundamentals"
date: 2026-04-03
topics: ["LFI", "RFI", "Log Poisoning", "Session Poisoning", "File Upload Attacks", "Bug Bounty", "CVSS", "Reporting", "Web Security"]
summary: "A high-energy session covering full file inclusion attack chains, RFI exploitation, poisoning techniques, and completing both the File Inclusion and Bug Bounty modules."
status: complete
---
# Day 16 - File Inclusion Mastery, RFI, Poisoning, and Bug Bounty Fundamentals

## What I studied today

Today was a **high-energy session** where I:

- completed the **HTB File Inclusion module**  
- applied LFI → RFI → RCE techniques in practice  
- explored file upload abuse and poisoning techniques  
- completed the **Bug Bounty fundamentals module**  
- learned how vulnerabilities are actually reported and evaluated  

---

## Summary of concepts

### File Inclusion

- Almost every **RFI vulnerability is also an LFI vulnerability**, but not vice versa  
- RFI is often blocked by configuration (`allow_url_include = Off`)  
- Even when RFI is not possible:
  - LFI can still be escalated via:
    - file uploads  
    - log poisoning  
    - session poisoning  

---

### Bug Bounty

- Bug bounty ≠ just “finding bugs”  
- It involves:
  - scope awareness  
  - rules of engagement  
  - proper reporting  
  - understanding impact  

- A vulnerability without a clear **impact explanation** is weak  
- A good report is as important as the technical finding  

---

## Key insight

> Exploitation gets you access.  
> Reporting is what makes it valuable.

---

## What I actually did (important)

### File Inclusion

- Successfully used **RFI to retrieve a hidden flag**  
- Used multiple file upload techniques:
  - GIF image upload (magic bytes bypass)  
  - zip wrapper  
  - phar wrapper  
- Achieved **remote code execution** through file inclusion  

- Performed:
  - **PHP session poisoning**
  - **server log poisoning**

- Fuzzed for:
  - traversal paths (`../`)  
  - server files  
  - configuration locations  

- Identified:
  - `/etc/php/7.4/apache2/php.ini`

- Experimented with:
  - modifying PHP behavior (e.g. disabling `system()`)

---

### Bug Bounty module

- learned structure of bug bounty programs:
  - scope  
  - rules of engagement  
  - disclosure policies  
  - eligibility  

- learned how to write a proper report:
  - vulnerability title  
  - description  
  - proof of concept  
  - impact  
  - optional remediation  

- introduced to **CWE & CVSS scoring**

---

## What went well

- chaining techniques instead of treating them separately  
- understanding attack flow instead of guessing payloads  
- finishing **two modules in one session**  
- strong focus and momentum despite being sick  

---

## What was confusing

- reverse shell failed initially → no bash available  
- understanding that `GIF8` is just a file signature prefix  
- session poisoning required correct targeting  
- log poisoning is powerful but easy to break  
- Burp interfered with log poisoning → switched to curl  
- double encoding still painful  
- still making small path mistakes (`/`…)

---

## Mistakes / friction

- overcomplicating before trying simpler approaches  
- small technical mistakes slowing me down  
- environment assumptions (e.g. expecting bash)  

---

## What I think I understand now

- file inclusion is a **chainable vulnerability class**, not a single exploit  
- uploads + inclusion = reliable RCE path  
- poisoning turns read access into execution  
- reporting and impact explanation matter just as much as exploitation  

---

## What I need to improve

- slow down and check basics first  
- reduce small technical mistakes  
- continue practicing full attack chains  
- improve clarity when explaining impact  

---

## Plan for next session

- start module on **Using Web Proxies**  
- do some schema / database practice  
- revisit algebra + lecture notes  

---

## Session info (optional)

- Duration: ~5h  
- Energy: High (still sick, but locked in)

---

    » 𝕾𝖕𝖊𝖈𝖙𝖊𝖗 𝕭𝖆𝖉 𝕺𝖒𝖊𝖓𝖘 «
    0:47 —〇——————- 4:34
