---
layout: log
title: "Day 15 - Sprint 0, P2P Backup Project Scope, and Light Cert Progress"
date: 2026-04-02
topics: ["University Project", "P2P", "C#", "Remote File Inclusion", "SSRF", "Project Planning", "Research"]
summary: "A project-heavy day focused on Sprint 0 for the P2P backup system, early architecture and protocol research, light RFI theory, and some creative work while still recovering."
status: complete
---
# Day 15 – Sprint 0, P2P Backup Project Scope, and Light Cert Progress

## What I studied today

Today was much more of a university / project day than a Hack The Box day.

I focused on:

- Sprint 0 planning for the university P2P backup system  
- initial research into how P2P systems work  
- thinking about how to approach the project in C#  
- a small amount of certification-related study on Remote File Inclusion (RFI)  
- some creative work while still recovering  

---

## Summary of concepts

- Not every productive day is measured by boxes rooted or rooms finished.  
- Early project meetings matter because they define the real scope, assumptions, and constraints before implementation starts.  
- P2P systems are not automatically “fully decentralized.” A design with superpeers changes both the technical model and the trust assumptions.  
- Remote File Inclusion can become dangerous when a vulnerable function accepts remote URLs, because that may allow:
  - reaching internal/local-only services  
  - including attacker-controlled code  
- Project planning becomes easier once the architecture is no longer vague  

---

## Deeper understanding (optional but recommended)

A big takeaway from today is that **scope clarity reduces chaos**.

Before a project has a clear structure, everything feels possible and nothing feels actionable. Once the scope is discussed properly, the work becomes easier to reason about:

- what kind of network model are we building?  
- is this true P2P or a superpeer-based design?  
- what roles exist?  
- where does trust live?  
- how do peers join the network?  
- what belongs in the UI, config parser, or protocol layer?  

This kind of clarity is not “less technical work.” It is what makes later technical work possible.

---

## What I actually did (important)

### University project: Sprint 0 meeting

We had the **Sprint 0** meeting for the P2P backup system project.

Main result:
- the project scope became much clearer  

Topics discussed:

- superpeers with whitelist (can ban others)  
- multiple superpeers may be useful  
- local network context  
- admin key used for signing / trust  
- superpeer communication + heartbeat logic  
- decision: **not true P2P → superpeer architecture**  
- testing via Docker / VMs  
- components:
  - frontend / UI  
  - config parser  
  - protocol / networking layer  
- cryptography tied to application logic  
- protocol / P2P research ownership  

---

### Initial research

- how P2P networks work  
- differences between decentralized and superpeer models  
- how this translates into a C# implementation  
- early thoughts about architecture and communication flow  

---

### Certification progress

#### Remote File Inclusion (RFI)

- if vulnerable functions allow remote URLs:
  - possible access to internal services (SSRF-like behavior)  
  - possible RCE via attacker-controlled scripts  

Only light theory today  no deep exploitation.

---

## Small creative work

Since I was still sick and needed something lower-pressure to do, I also made a small design piece.

![Big Brother Is Watching](/assets/img/eye_scanning_iris_only_fallback.svg)

---

## What went well

- project scope is finally clear  
- I now understand the direction of the P2P system  
- useful early research instead of staying vague  
- kept at least minimal momentum on cert topics  
- adapted to low energy instead of forcing heavy work  

---

## What was confusing

- exact boundary between “true P2P” and superpeer systems  
- how all components will interact in practice  
- mentally feeling like the day was unproductive when it actually wasn’t  

---

## Mistakes / friction

- judging the day too harshly because it wasn’t HTB-focused  
- still low energy due to being sick  
- undervaluing planning and research  

---

## What I think I understand now

- Sprint 0 is real progress, not filler  
- architecture decisions define everything that comes after  
- superpeer design changes trust and system behavior significantly  
- productivity is not limited to exploitation work  

---

## What I need to improve

- stop equating “no HTB” with “no progress”  
- balance university and cert work better  
- continue P2P research until I can clearly explain the system  
- recover properly to regain full focus  

---

## Plan for next session

- continue file inclusion topic  
- deepen understanding of P2P architecture  
- return to hands-on security work when energy is back  

---

## Session info (optional)

- Duration: mixed / project-heavy  
- Energy: Low (still sick)
