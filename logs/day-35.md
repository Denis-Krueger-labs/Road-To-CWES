---
layout: log
title: "Day 35 - CSRF, DOM-Based Attacks & LLM Security Work"
date: 2026-04-22
topics: ["CSRF", "DOM-Based Attacks", "LLM Security", "Prompt Injection Defences"]
summary: "Studied CSRF attacks and defenses, explored DOM-based vulnerabilities, and significantly improved a presentation on LLM prompt injection defenses."
status: complete
---

# Day 35 – CSRF, DOM-Based Attacks & LLM Security

## What I studied today

Today was a mix of classic web vulnerabilities and project work.

- Completed a TryHackMe room on **CSRF (Cross-Site Request Forgery)**
- Worked through a room on **DOM-Based Attacks**
- Fully reworked our **LLM Prompt Injection Defence presentation** for Friday

---

## Summary of concepts

### CSRF (Cross-Site Request Forgery)

CSRF is an attack where a victim’s browser is tricked into sending a request to a web application where they are already authenticated.

- The server trusts the request because it includes valid session cookies
- The victim does not realize they are performing an action
- The attacker does not need to steal credentials

Typical flow:

1. Victim is logged into a website
2. Victim visits attacker-controlled page
3. That page triggers a request (e.g. form submission or image request)
4. Browser automatically includes session cookies
5. Server processes the request as if it came from the victim

Key idea:
> **The attack abuses trust in the browser, not the user directly**

---

### DOM-Based Attacks

DOM-based vulnerabilities happen entirely on the client side.

- Input is processed by JavaScript in the browser
- The server is never involved in the dangerous step
- Vulnerabilities arise from unsafe **sources → sinks**

Important concepts:

- **Source** = where input comes from (URL, input field, hash, etc.)
- **Sink** = where input is written into the page (e.g. `innerHTML`)

If unsafe sinks are used without sanitization, JavaScript can execute.

---

### LLM Prompt Injection (Project Work)

We reworked the presentation heavily, focusing on clarity and structure.

Based on the slides:

- Prompt injection happens when **malicious instructions are hidden inside data** and the model follows them :contentReference[oaicite:0]{index=0}  
- The core problem:
  - **data and instructions are mixed**
  - the model cannot reliably distinguish between them :contentReference[oaicite:1]{index=1}  

Key risks:

- manipulated outputs
- data leakage
- incorrect decisions

Important takeaway we emphasized:

- **“Prompting is not a security boundary”** :contentReference[oaicite:2]{index=2}  

Defensive ideas:

- input filtering and guardrails
- separating prompt and data (structured input)
- marking untrusted data
- monitoring and logging

Most important insight:

> **No single defense is enough  security must be layered** :contentReference[oaicite:3]{index=3}  

---

## What I actually did (important)

- Completed CSRF room and understood attack flow + defenses
- Worked through DOM-based attack concepts and examples
- Rebuilt large parts of our presentation:
  - improved explanations
  - cleaned up structure
  - aligned slides with actual security concepts instead of surface-level wording

---

## What went well

- CSRF concept clicked quickly because it follows a clear request flow
- DOM-based attacks made more sense after linking them to XSS concepts
- The presentation now feels much more **coherent and technical**, not just descriptive
- I’m starting to connect **web security concepts with AI security**, which is actually really interesting

---

## What was confusing

- CSRF defenses can feel a bit abstract without seeing them implemented (tokens vs SameSite vs referer checks)
- DOM-based attacks require thinking in **JavaScript execution flow**, not request/response flow
- LLM security is still a bit messy because:
  - there is no single “correct” defense
  - everything is trade-offs

---

## Mistakes / friction

- Switching between topics (CSRF → DOM → LLM) made it harder to stay focused
- I sometimes default to “I get the idea” instead of verifying it with concrete examples
- Presentation rework took longer than expected because wording matters a lot more than I thought

---

## What I think I understand now

- CSRF is about abusing **trusted browser behavior**
- DOM-based vulnerabilities are about **unsafe client-side data handling**
- XSS, DOM XSS, and CSRF are all connected through:
  - trust
  - user context
  - browser behavior
- LLM prompt injection is basically:
  - **input validation problem + context confusion problem**

---

## What I need to improve

- Practice identifying CSRF in real applications (not just theory)
- Get more comfortable tracing JavaScript flows for DOM-based vulnerabilities
- Improve ability to:
  - quickly identify **source → sink patterns**
- Continue refining how I explain complex topics (presentation helped a lot here)

---

## Plan for next session

- Finish SQLMap Essentials
- start stack-based buffer overflow basics

---

## Session info (optional)

- Duration: ~4-5h (including project work)
- Energy: Medium (but split focus)
