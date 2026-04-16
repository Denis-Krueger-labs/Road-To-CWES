---
layout: log
title: "Day 27 - SQLMap Request Handling and Real-World Usage"
date: 2026-04-14
topics: ["SQLMap", "HTTP Requests", "Burp Suite", "Automation", "Debugging"]
summary: "Low-energy day focused on understanding how to properly configure SQLMap with real HTTP requests, including cookies, headers, and request files."
status: partial
---
# Day 27 - SQLMap Request Handling

## What I studied today

- using SQLMap with real HTTP requests
- handling GET vs POST parameters
- importing requests from Burp / browser (cURL → SQLMap)
- working with request files (`-r`)
- debugging SQLMap issues

---

## Summary of concepts

### Proper request setup matters more than the tool

Most SQLMap failures are not because:
- the target is not vulnerable

but because:
- request is wrong
- cookies missing
- headers missing
- POST data malformed

---

### Using cURL → SQLMap workflow

- copy request from browser (Copy as cURL)
- replace `curl` with `sqlmap`
- ensures:
  - correct headers
  - correct cookies
  - realistic request

---

### GET vs POST

- GET → `-u`
- POST → `--data`
- specific param → `-p`
- injection marker → `*`

---

### Full request handling

- use `-r req.txt`
- best for:
  - complex requests
  - auth flows
  - long headers / JSON bodies

---

### Customization

- cookies → `--cookie`
- headers → `-H`
- user-agent → `--random-agent`
- HTTP method → `--method`

---

### Debugging SQLMap

- `--parse-errors` → show DB errors
- `-t` → save traffic
- `-v 6` → full verbose output
- `--proxy` → send through Burp

---

## What I actually did (important)

- learned how to:
  - convert real web traffic into SQLMap input
  - handle complex HTTP requests
  - debug failed SQLMap runs
- focused on understanding **why SQLMap fails**, not just using it blindly

---

## What went well

- started thinking like:
  → “what does the server actually expect?”
- understood that SQLMap is only as good as the request you give it
- connected Burp + SQLMap workflow properly

---

## What was challenging

- low energy and mental fatigue
- felt like “not doing enough” even though learning was happening
- lots of small details (headers, cookies, formats)

---

## Mistakes / friction

- underestimating how precise requests need to be
- tendency to overcomplicate instead of simplifying input

---

## What I think I understand now

- SQLMap is not magic:
  → it just automates what you already understand
- real skill = crafting the correct request
- debugging is part of exploitation, not a failure

---

## Plan for next session

- finish SQLMap room
- apply request file (`-r`) in a real scenario
- combine SQLi with previous attack chains

---

## Session info (optional)

- Duration: ~1–2h (low focus)
- Energy: Low
