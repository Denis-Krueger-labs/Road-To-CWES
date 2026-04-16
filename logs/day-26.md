---
layout: log
title: "Day 26 - Session Hijacking Concepts and Quick Exploitation Practice"
date: 2026-04-13
topics: ["Session Hijacking", "Cookies", "XSS", "SQLMap", "Web Exploitation"]
summary: "A very short session due to real-life constraints, but still applied SQLMap and XSS to identify a vulnerability and simulate credential harvesting."
status: complete
---
# Day 26 – Session Hijacking Concepts and Quick Exploitation Practice

## What I studied today

- session hijacking basics
- role of cookies in modern web applications
- how XSS can be used to steal sessions or credentials

---

## Summary of concepts

- modern web applications rely heavily on **cookies for session management**
- if an attacker can obtain a valid session cookie:
  - they can impersonate the user
- XSS enables:
  - executing JavaScript in the victim’s browser
  - stealing cookies
  - redirecting users
  - capturing credentials

---

## What I actually did (important)

- used **SQLMap** to identify a vulnerability
- used **XSS** to:
  - create a fake login page (credential harvesting)
  - simulate how attackers capture user credentials

Even though the session was very short, it still included a full attack flow:
- discovery → exploitation → impact

---

## What went well

- stayed consistent despite limited time and external issues
- applied multiple concepts together (SQLi + XSS)
- focused on practical exploitation instead of theory

---

## What was challenging

- very limited time (only ~20 minutes)
- external stress and real-life interruptions made it hard to focus

---

## Mistakes / friction

- no deep exploration due to time constraints
- session felt rushed

---

## What I think I understand now

- XSS is not just about alerts  it can be used for real attacks like:
  - credential harvesting
  - session hijacking
- combining vulnerabilities increases impact significantly

---

## What I need to improve

- spend more time on chaining attacks in a structured way
- revisit session hijacking in more depth when time allows

---

## Plan for next session

- finish SQLMap
- finish XSS
- return to full-length focused session

---

## Session info (optional)

- Duration: ~20 minutes
- Energy: Low
