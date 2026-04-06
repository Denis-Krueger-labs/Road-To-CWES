---
layout: log
title: "Day 19 - Fingerprinting, Crawling, and Web Recon Workflow"
date: 2026-04-06
topics: ["Web Reconnaissance", "Fingerprinting", "Crawling", "robots.txt", "ZAP", "Scrapy", "Wappalyzer"]
summary: "A low-energy recon day focused on web fingerprinting, crawling, robots.txt analysis, and using ZAP to search through discovered content."
status: complete
---
# Day 19 – Fingerprinting, Crawling, and Web Recon Workflow

## What I studied today

Today I focused on:

- fingerprinting web applications
- crawling / spidering
- `robots.txt`
- well-known URIs
- using ZAP for crawling and searching
- general web recon workflow

---

## Summary of concepts

- Fingerprinting is about identifying technologies, frameworks, servers, and security controls used by a target.
- Good fingerprinting helps with:
  - targeted attacks
  - identifying misconfigurations
  - prioritizing targets
  - building a more complete profile of the application
- Crawling (or spidering) is the process of systematically following links and mapping accessible parts of a web application.
- `robots.txt` is intended for bots, but it can still reveal useful paths, hidden structure, or interesting directories.
- Well-known URIs can expose useful configuration details, especially in authentication and security-related contexts.

---

## Deeper understanding (optional but recommended)

One useful takeaway from today is that **recon is not just “finding pages”  it is about reducing uncertainty**.

Fingerprinting helps answer:
- what stack is this?
- what might be vulnerable?
- what assumptions are reasonable?

Crawling helps answer:
- what is actually reachable?
- what is linked?
- what might be hidden in comments, metadata, or supporting files?

So even if recon feels slower than exploitation, it directly improves the quality of later testing.

---

## What I actually did (important)

- used fingerprinting to identify:
  - CMS
  - Apache version
  - operating system
- analyzed an example `robots.txt`
- crawled a target using **OWASP ZAP**
- used ZAP’s search function to find relevant content
- worked a bit with **Scrapy** / crawling-related workflow

This was mainly a recon-focused session, so the value came from understanding structure, technology, and discoverability rather than exploitation.

---

## What went well

- using `curl` felt natural
- using ZAP for crawling and search felt useful
- working with crawling tools felt more structured than before

---

## What was confusing

- motivation to start was basically zero
- one exercise expected finding a very specific single comment line in a huge page, which felt more annoying than educational
- in practice, the search felt less like recon skill and more like guessing what the prompt wanted

---

## Mistakes / friction

- low motivation made it harder to get started
- some of the exercise design felt unnecessarily fiddly
- I still need more repetition to turn crawling and fingerprinting into a smoother workflow

---

## What I think I understand now

- fingerprinting is useful because it narrows the search space
- crawling is not just about links, but also about comments, metadata, and hidden structure
- `robots.txt` can still be useful from a recon perspective even though it is not a security control
- ZAP is strong for exploring and searching, even if some tasks still feel clunky

---

## What I need to improve

- build a cleaner recon workflow so slower modules feel more purposeful
- stay patient during theory-heavy or fiddly exercises
- keep practicing crawling and fingerprinting until they feel more natural and less like isolated tasks

---

## Plan for next session

- finish the Information Gathering module
- keep tying recon steps to realistic attack paths

---

## Session info (optional)

- Duration: ~1 hour
- Energy: Low
