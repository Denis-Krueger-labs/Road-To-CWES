---
layout: log
title: "Day 20 - Search Engine Discovery, OSINT, and Web Archives"
date: 2026-04-07
topics: ["OSINT", "Google Dorking", "Search Operators", "Wayback Machine", "Web Reconnaissance"]
summary: "Completed the web discovery module with focus on search engine reconnaissance, Google dorking, and historical web analysis using archives."
status: complete
---
# Day 20 – Search Engine Discovery, OSINT, and Web Archives

## What I studied today

Today focused on:

- search engine discovery (OSINT)
- search operators and Google dorking
- web archives (Wayback Machine)
- automated recon concepts
- finishing the Web Discovery room on HTB

---

## Summary of concepts

- Search engines are powerful recon tools because they index large parts of the internet passively.
- OSINT allows gathering information without directly interacting with the target.
- Search operators (Google dorks) can:
  - uncover hidden endpoints
  - find sensitive files
  - reveal misconfigurations
- Web archives provide historical insight into:
  - old endpoints
  - removed functionality
  - legacy vulnerabilities
- Automation improves recon by making it:
  - faster
  - more consistent
  - more scalable

---

## Deeper understanding (optional but recommended)

One key takeaway:

> Sometimes the best recon is not what exists now  but what used to exist.

Old endpoints, forgotten directories, and deprecated features often:
- still exist
- are less protected
- are not linked anywhere anymore

Search engines and archives are basically:
> **memory of the internet**

---

## What I actually did (important)

- used the **Wayback Machine** to:
  - explore previous versions of websites
  - identify older pages and potential hidden content
- applied search operators to:
  - narrow down results
  - think about how to find sensitive information
- finished the **HTB Web Discovery module**

---

## What went well

- understanding OSINT felt intuitive
- using the Wayback Machine was surprisingly useful
- connecting search operators to real recon scenarios made sense
- finishing the module gave a clean checkpoint in the recon phase

---

## What was confusing

- sometimes VHost-related behavior still feels inconsistent
- German train system still unreliable (critical vulnerability)

---

## Mistakes / friction

- didn’t fully explore advanced combinations of search operators
- could have tested more real-world dorking scenarios instead of just examples
- slight loss of focus during parts of the session

---

## What I think I understand now

- OSINT is not just “extra info”  it can directly lead to vulnerabilities
- search engines can expose things that should not be public
- web archives can reveal forgotten attack surfaces
- recon is about combining multiple small information sources into a bigger picture

---

## What I need to improve

- practice more real-world Google dorking scenarios
- combine OSINT with other recon techniques (DNS, VHosts, crawling)
- build a more structured recon workflow instead of isolated techniques

---

## Plan for next session

- start applying recon techniques to actual targets / boxes
- revisit weak areas (VHosts + DNS inconsistencies)
- continue Web Penetration Tester path

---

## Session info (optional)

- Duration: ~2h
- Energy: Medium
