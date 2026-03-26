---
layout: log
title: "Day 08 - Fuzzing Basics, Project Planning, and Team Organization"
date: 2026-03-26
topics: ["Fuzzing", "Brute Force", "Wordlists", "SecOps", "MITRE ATT&CK", "Purple Teaming", "Project Planning"]
summary: "A lighter technical day focused on fuzzing fundamentals, early planning for a possible ATT&CK-aligned SecOps/Purple Team university project, and organizing a university CTF team."
status: complete
---
# Day 08 – Fuzzing Basics, Project Planning, and Team Organization

## What I studied today

Today I focused on:

- the difference between fuzzing and brute force
- core fuzzing concepts like wordlists, payloads, response analysis, and scope
- early planning for a possible university SecOps / Purple Team project
- organizing a university CTF team and related coordination work

---

## Summary of concepts

- **Fuzzing** is a broad testing technique where many unexpected or varied inputs are sent to an application to see how it behaves.
- **Brute force** is narrower and more targeted. It usually means systematically trying many possible combinations, such as passwords or tokens.
- Fuzzing is useful because it helps uncover hidden functionality, unexpected behavior, bad input handling, and weak validation.
- The quality of fuzzing depends a lot on:
  - the wordlist
  - the payloads
  - how responses are analyzed
  - the scope of the test
- Not every strange response is a vulnerability. False positives and false negatives are both part of real testing.

---

## Deeper understanding (optional but recommended)

The biggest distinction I want to keep in mind is this:

**Fuzzing is about exploring behavior, not just forcing access.**

Brute force asks:
> “What happens if I try many possible valid-looking combinations?”

Fuzzing asks:
> “What happens if I send lots of different or unexpected inputs and observe the response?”

That makes fuzzing especially useful for:
- hidden paths
- parameter discovery
- weird error behavior
- input validation issues
- spotting anomalies that may point to deeper vulnerabilities

So the value of fuzzing is not only in finding something directly exploitable, but also in **revealing structure and behavior** that I can investigate further.

---

## What I actually did (important)

This was not a heavy lab day. Most of the value today came from university and project-related work.

### Fuzzing theory

I reviewed the core differences between:
- fuzzing
- brute force

And I looked at key fuzzing concepts like:
- wordlists
- payloads
- response analysis
- false positives / false negatives
- fuzzing scope

### Early SecOps / Purple Team project planning

I spent time shaping an initial university project idea around ATT&CK-aligned attack simulation in an isolated VM environment.

At this stage, this is **only a project idea / proposal**. It has **not** been approved yet.

The current idea is to explore something along the lines of:

**Simulation of selected MITRE ATT&CK techniques to analyze visibility, detection opportunities, and countermeasures in a small lab infrastructure**

Possible technique examples:
- brute force
- network service scanning
- remote services / SSH
- account discovery

The current planning idea would be to document:
- how the activity is performed
- what artifacts or logs are generated
- what detection opportunities exist
- what countermeasures are effective

The important framing here is that this would be presented more as a:

- SecOps project
- Purple Team project
- attack simulation / adversary emulation exercise

rather than as a pure Red Team project.

### Other useful work today

I also spent time on:
- improving my CV so it reflects me more accurately
- organizing the university CTF team
- setting up and configuring the Discord server
- sending invitations and tracking interest

So while today was lighter on hands-on exploitation, it still moved several useful things forward.

---

## What went well

- I still kept the learning streak going even though the day was overloaded with university work.
- The project idea became clearer, even though it is still only in the planning stage.
- The ATT&CK-based framing feels strong for a future proposal.
- I got useful organization work done instead of letting the whole day dissolve into chaos.

---

## What was confusing

- Fuzzing itself was not especially confusing yet, but I still need more practical repetition before it feels natural.
- Today was more mentally fragmented than technically difficult, so the bigger issue was context-switching rather than one hard concept.
- It was not always easy to decide what counted as “enough” on a day that was already full of unrelated responsibilities.

---

## Mistakes / friction

- The day was hectic and changed a lot because university plans shifted unexpectedly.
- My energy was lower than I would like for technical work because lectures ran until late.
- I did not have enough uninterrupted focus time for a deeper hands-on session.
- I need to be careful not to judge a useful planning/organization day as “bad” just because it was not exploit-heavy.

---

## What I think I understand now

- Fuzzing and brute force are related but not the same thing.
- Good fuzzing depends heavily on scope, payload choice, and response interpretation.
- A lower-intensity technical day can still be a productive day if it moves planning, structure, and project direction forward.
- The SecOps / Purple Team project idea is promising, but it is still only a proposal and needs approval before it becomes a real project.

---

## What I need to improve

- Build in better fallback expectations for chaotic university days instead of expecting every day to be a full technical grind.
- Get more hands-on fuzzing practice so the theory turns into instinct.
- Reduce self-criticism on days that are productive in a more strategic or organizational way.
- Protect focused time better when possible, especially on lecture-heavy days.

---

## Plan for next session

- finish the fuzzing module
- make the next session more hands-on again
- keep the project idea in the background until I know whether it gets approved

---

## Session info (optional)

- Duration: ~1 hour of direct study, plus a lot of university/project organization work
- Energy: Low
