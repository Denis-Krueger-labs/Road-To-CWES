---
layout: log
title: "Day 28 - XSS Phishing & Credential Harvesting"
date: 2026-04-15
topics: ["XSS", "Phishing", "Credential Harvesting", "Social Engineering", "JavaScript"]
summary: "Used reflected XSS to inject a fake login form, remove legitimate elements, and capture credentials via a controlled server."
status: productive
---

# Day 28 – XSS Phishing Attack

## What I studied today

- XSS-based phishing attacks
- login form injection via JavaScript
- manipulating DOM to make attacks believable
- capturing credentials using a custom server

---

## Summary of concepts

### XSS → Phishing bridge

- XSS is not just “alert()”
- real impact = **social engineering + trust abuse**
- inject malicious UI into trusted application

---

### Attack flow

1. find XSS vuln (reflected)
2. inject JavaScript payload
3. render fake login form
4. remove legit elements (to reduce suspicion)
5. send credentials to attacker server
6. optionally redirect victim back → stealth

---

### DOM manipulation

- `document.write()` → inject fake login form
- `document.getElementById().remove()` → remove real UI
- `<!--` → clean leftover HTML

Goal:
→ make page feel **legitimate**

---

### Credential harvesting

#### Basic (noisy)

- netcat listener
- captures GET request with creds

#### Improved (stealth)

- PHP server
- logs creds into file
- redirects victim back to original page

→ victim thinks login worked

---

## What I actually did (important)

- discovered working XSS payload in image viewer
- injected full login form via `document.write()`
- removed original form using DOM manipulation
- cleaned up page for realism
- captured credentials using:
  - netcat (test)
  - PHP server (realistic attack)
- verified credentials stored in `creds.txt`

---

## What went well

- started thinking in **attack chains instead of single vulns**
- understood how UI manipulation = psychological attack
- successfully combined:
  → XSS + phishing + backend listener

---

## What was confusing

- figuring out why initial payload didn’t execute
- understanding how input is rendered in HTML
- cleaning up leftover HTML without breaking page

---

## Mistakes / friction

- forgetting to replace `OUR_IP` initially
- netcat approach causing obvious connection errors
- payload formatting getting messy when too long

---

## What I think I understand now

- XSS becomes dangerous when combined with **user trust**
- phishing via XSS is more about **believability** than code
- small UI details make or break the attack

---

## Real life context

- pre Sprint 1 meeting for P2P backup project
- helped out at dorm bar (unexpected side quest lol)

---

## Plan for next session

- finish XSS module completely
- practice cleaner payload building
- start thinking about chaining XSS with other attacks

---

## Session info (optional)

- Duration: ~3–4h total (split focus)
- Energy: Medium (busy but productive)
