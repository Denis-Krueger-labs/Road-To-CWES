---
layout: log
title: "Day 09 - Fuzzing Introduction and Job Fair Recon"
date: 2026-03-27
topics: ["Fuzzing", "ffuf", "Gobuster", "Feroxbuster", "wfuzz", "Enumeration", "Career Fair", "Networking"]
summary: "A low-energy day focused on basic fuzzing tool overview and job fair recon. Light technical progress, but still useful for understanding both enumeration tooling and the current internship landscape."
status: complete
---
# Day 09 – Fuzzing Introduction and Job Fair Recon

## What I studied today

Today I focused on:

- basic fuzzing concepts and common web fuzzing tools
- differences between ffuf, Gobuster, Feroxbuster, and wfuzz
- real-world career fair recon and internship scouting

---

## Summary of concepts

- Fuzzing is a way to explore web application behavior by sending many inputs and observing the responses.
- Different tools overlap, but each has strengths:
  - **ffuf** is strong for fast web fuzzing, parameter discovery, and flexible filtering
  - **Gobuster** is widely used for directory, file, DNS, and vhost enumeration
  - **Feroxbuster** is especially strong for recursive content discovery
  - **wfuzz** is flexible for fuzzing parameters, payload positions, and web inputs
- Fuzzing is not just “spraying words at a target.” The useful part is interpreting responses and deciding what is worth deeper investigation.

---

## Deeper understanding (optional but recommended)

One thing that matters with fuzzing is that the tool itself is less important than the **testing logic** behind it.

The real workflow is:

1. choose a scope
2. choose the right wordlist or payload source
3. send many requests efficiently
4. filter out noise
5. investigate anomalies

So the value is not just in “running ffuf,” but in understanding:
- what am I actually looking for?
- what responses are normal?
- what differences matter?
- what should I investigate next?

That mindset matters more than memorizing flags.

---

## What I actually did (important)

- Reviewed the roles and common use cases of:
  - `ffuf`
  - `Gobuster`
  - `Feroxbuster`
  - `wfuzz`
- Started getting familiar with fuzzing as a practical skill area, even though today was more introductory than hands-on.
- Spent a large part of the day at the job fair in Stuttgart, talking to companies and trying to identify who actually offers relevant student roles or internships in technical security.
- Used the event more as a recon exercise than as a “perform and impress” day:
  - which companies seem technical?
  - which ones are mostly buzzwords?
  - which ones might actually be useful later?

---

## What went well

- I still kept the streak alive despite being very tired.
- I got a first overview of fuzzing tools and their different roles.
- The job fair was useful as a reality check for how companies present security roles and how vague many of those descriptions still are.
- I gathered some useful signal about which companies are worth paying attention to later.

---

## What was confusing

- Since today was more of an overview, fuzzing still feels broad and slightly abstract. I need more actual hands-on use before the tools feel natural.
- The job fair was a bit frustrating because many companies sounded more vague and buzzword-heavy than technically grounded.
- It was hard to separate “this company is not a fit for me” from “there are no good opportunities,” especially while tired.

---

## Mistakes / friction

- I was running on very low energy because of lack of sleep, which made technical study harder than it should have been.
- I expected more visible interest or clearer technical conversations at the job fair, which made the experience feel more disappointing than it probably really was.
- I did not have enough energy left for a deeper fuzzing session, so today stayed more introductory than practical.

---

## What I think I understand now

- Fuzzing tools overlap a lot, but each has slightly different strengths depending on the type of enumeration I want to do.
- The important part of fuzzing is not just the tool, but how I scope the test and interpret responses.
- A low-energy day can still be useful if I use it for recon, orientation, and keeping momentum alive.
- Job fairs are not always about immediate opportunity — sometimes they are more useful as intelligence gathering.

---

## What I need to improve

- Get actual hands-on fuzzing repetition instead of staying at the “tool overview” stage.
- Avoid turning tired frustration into broad conclusions like “entry is dead.”
- Protect sleep better before days where I need both social and technical energy.
- Keep using low-energy days for smaller, controlled tasks instead of expecting full technical performance.

---

## Plan for next session

- finish the fuzzing module
- make the next session more practical and tool-focused
- keep the goal small: one clean fuzzing workflow, not a giant grind session

---

## Session info (optional)

- Duration: ~1 hour of direct study, plus most of the day spent at the job fair
- Energy: Very low
