---
layout: log
title: "Day 24 - SQLMap Basics and LLM Defense/Attack Presentation Work"
date: 2026-04-11
topics: ["SQLMap", "SQL Injection", "Automation", "LLM Security", "Prompt Injection", "Presentation Work"]
summary: "A low-energy day focused on introductory SQLMap concepts, while most of the real output went into building a full presentation on LLM attacks and defenses."
status: complete
---
# Day 24 - SQLMap Basics and LLM Defense/Attack Presentation Work

## What I studied today

Today I focused on:

- introductory SQLMap concepts
- supported SQL injection types
- supported databases
- basic SQLMap usage and output interpretation
- a large amount of presentation work on LLM attacks and defenses

---

## Summary of concepts

- **SQLMap** is a free, open-source Python tool that automates the detection and exploitation of SQL injection vulnerabilities.
- It supports a wide range of databases and SQL injection techniques.
- SQLMap can help with:
  - detection
  - fingerprinting
  - enumeration
  - data retrieval
  - file system access
  - sometimes even OS command execution

### Supported SQLi types

- **B** → Boolean-based blind
- **E** → Error-based
- **U** → Union-based
- **S** → Stacked queries
- **T** → Time-based blind
- **Q** → Inline queries

### Key beginner takeaway

A lot of SQLMap’s usefulness depends on understanding:
- whether the parameter is dynamic
- whether the page response is stable enough for automation
- what kind of SQLi behavior is actually present

So even though SQLMap automates things, it still helps to understand the underlying logic.

---

## Deeper understanding (optional but recommended)

One useful thing from today is that **automation does not replace reasoning**.

SQLMap can test and exploit a lot automatically, but it still relies on good assumptions:

- is the target parameter actually linked to database behavior?
- are the responses stable enough to compare?
- is the injection type something automation can clearly detect?
- are protections or filters interfering?

That means SQLMap is strongest when used by someone who already understands:
- how SQLi works
- what kind of behavior to expect
- when automation output looks trustworthy vs misleading

---

## What I actually did (important)

### SQLMap

- reviewed what SQLMap is and what it supports
- looked at:
  - supported database systems
  - supported SQLi techniques
  - basic usage flags like `-h`, `-hh`, and `-u`
- noted the meaning of common output such as:
  - “URL content is stable”
  - “parameter appears to be dynamic”

### Main output of the day

Most of the actual work today went into university / presentation work:

- built a full presentation on **LLM attacks and defenses**

That was the real main task of the day and took most of the time and energy.

So even though the study topic on paper was SQLMap, the day was much more presentation-heavy in practice.

---

## What went well

- I still kept cert progress moving, even if only lightly
- I got a major non-cert deliverable done with the LLM presentation
- the SQLMap basics were easy enough to absorb even on a low-energy day

---

## What was confusing

- SQLMap itself was not very confusing yet, because this was still introductory material
- the bigger challenge today was balancing cert study with a large separate workload

---

## Mistakes / friction

- low energy made it hard to go deeper into practical SQLMap usage
- most of the day’s time went into the presentation, so cert work stayed lighter than planned
- this was more of a theory / overview session than hands-on practice

---

## What I think I understand now

- SQLMap is powerful, but it is still built on top of normal SQLi logic
- automation is most useful when I already understand what the target is doing
- a day can still be productive even if the main output is university work rather than cert progress

---

## What I need to improve

- move from SQLMap theory into actual hands-on use
- keep balancing university output and certification progress realistically
- avoid treating “lighter cert day” as “bad day”

---

## Plan for next session

- continue SQLMap
- finish XSS after the topic break
- try to make the next SQLMap session more practical

---

## Session info (optional)

- Duration: ~8 hours total work
- Energy: Low
