---
layout: log
title: "Day 40 - TCP Messaging Prototype and First Sprint 1 Implementation Attempt"
date: 2026-04-27
topics: ["P2P Backup System", "C#", "TCP Messaging", "Sprint 1", "Prototype Work"]
summary: "Built an initial TCP-based messaging prototype for the P2P backup system before later discovering that the Sprint 1 implementation should move toward HTTP instead."
status: complete
---

# Day 40 - TCP Messaging Prototype

## What I did today

Today was focused on the university **P2P backup system** project.

I worked on the first implementation attempt for Sprint 1 and built out the initial messaging path using TCP.

---

## What I actually did

- worked on the P2P backup system
- implemented / extended TCP-based messaging demo code
- explored how peers could send messages directly
- worked on early message transport logic
- tested basic peer-to-peer communication ideas
- created implementation groundwork that later helped clarify what the project actually needed

---

## Summary of concepts

The main idea today was:

> peers need a way to exchange messages reliably enough for the prototype

The first attempt used TCP-style communication. This made sense as a lower-level transport experiment, but it later turned out not to be the preferred Sprint 1 direction.

Even though the TCP path became legacy/demo code, it still helped clarify:

- what a message needs to contain
- how peers identify each other
- what transport responsibilities look like
- why routing metadata matters
- why testability and debugging are important

---

## What went well

- I got hands-on implementation time in C#
- I started turning the project from theory into running code
- I learned more about how messaging transport should be structured
- the TCP work helped expose what would become important in the HTTP design later

---

## What was confusing

- the expected transport direction was not fully clear yet
- it was not obvious at first that TCP would become the wrong main path
- project scope and implementation expectations were still shifting

---

## Mistakes / friction

- spent time implementing TCP before discovering the project direction should be HTTP
- some work became legacy/demo code sooner than expected
- communication about the intended architecture could have been clearer earlier

---

## What I think I understand now

- even “wrong path” implementation work can still teach useful architecture lessons
- transport choice affects testability, debugging, and endpoint design
- early prototypes are allowed to be messy if they clarify the real direction
- Sprint 1 needed a practical and testable messaging flow more than a perfect transport abstraction

---

## What I need to improve

- clarify architectural expectations earlier before going deep into implementation
- document assumptions when starting a prototype
- keep experimental code clearly separated from the main implementation path
- avoid getting too attached to the first technical solution

---

## Plan for next session

- confirm the intended Sprint 1 transport direction
- adapt the messaging implementation if needed
- continue building toward a working prototype

---

## Session info

- Duration: project-heavy day
- Energy: Medium to Low
