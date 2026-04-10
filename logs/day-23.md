---
layout: log
title: "Day 23 - XSS Discovery, Automated Scanning, and Defacement/Phishing Concepts"
date: 2026-04-10
topics: ["XSS", "ZAP", "Automated Discovery", "Manual Discovery", "Defacement", "Phishing", "Web Security"]
summary: "A shorter fallback session focused on XSS discovery methods, basic attack concepts, and using ZAP to identify XSS issues in a lab environment."
status: complete
---
# Day 23 - XSS Discovery, Automated Scanning, and Defacement/Phishing Concepts

## What I studied today

Today I focused on:

- XSS discovery methods
- automated vs manual XSS discovery
- XSS payload placement
- basic defacement concepts
- phishing through XSS
- using ZAP in a lab environment

---

## Summary of concepts

- Finding XSS can be just as difficult as exploiting it.
- XSS is common, but the difficulty depends a lot on:
  - how the application handles input
  - how strong the filtering/sanitization is
  - whether the vulnerable behavior is in the backend or frontend
- Automated tools can help identify low-hanging issues, but they are not enough on their own.
- Manual testing and code review become more important as the application gets more complex.
- XSS payloads are not limited to form fields:
  - they can also appear in headers like `User-Agent` or `Cookie`
- XSS can be used for more than alerts:
  - defacement
  - phishing
  - session theft
  - browser-side actions as the victim

---

## Deeper understanding (optional but recommended)

A useful distinction from today:

**Automated discovery finds patterns. Manual discovery finds context.**

Tools like:
- Nessus
- Burp Pro
- ZAP

can help locate obvious or common XSS issues.

But more advanced XSS often needs:
- understanding how input moves through the app
- reviewing source code
- identifying where attacker-controlled input becomes HTML or JavaScript
- recognizing unsafe sinks and rendering behavior

So the real skill is not just “run a scanner,” but knowing:
- where to look
- what to test
- what kind of XSS might exist in that specific context

---

## What I actually did (important)

- Used **ZAP** in a lab environment to identify an XSS issue
- Continued building familiarity with using scanning/support tools to assist XSS discovery
- Focused on understanding discovery workflow rather than just payload execution

This was a shorter fallback session, so the goal was mainly to keep momentum and reinforce the discovery side of XSS rather than doing a full deep dive.

---

## What went well

- I still moved the XSS topic forward despite limited time
- Using ZAP felt useful for identifying issues in a lab environment
- The session helped reinforce that XSS is not only about payloads, but also about discovery strategy

---

## What was confusing

- The topic itself was okay, but I would have liked more time to go deeper into practical examples
- Short sessions always make it harder to feel like I did “enough,” even when I still made progress

---

## Mistakes / friction

- Started too late, so this became more of a fallback session than a full focused one
- Limited time meant I stayed mostly on the discovery side instead of going deeper into exploitation or code review

---

## What I think I understand now

- XSS discovery is a separate skill from XSS exploitation
- automated tools help, but they do not replace manual reasoning
- payload placement matters, and inputs are not limited to visible form fields
- XSS can be used for several browser-side attacks beyond simple alerts

---

## What I need to improve

- practice more manual XSS discovery instead of relying too much on tooling
- get more repetition with identifying XSS in different contexts
- start earlier when possible so fallback sessions happen less often

---

## Plan for next session

- finish the XSS room
- spend more time on practical XSS examples if possible

---

## Session info (optional)

- Duration: ~1.5 hours
- Energy: Low
