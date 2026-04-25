---
layout: log
title: "Day 38 - SQLMap Exploitation and WAF Bypass"
date: 2026-04-25
topics:
  - SQLMap
  - Blind SQLi
  - JSON requests
  - WAF bypass
summary: "Discovered and exploited a JSON-based time-blind SQL injection and bypassed filtering to retrieve the flag."
status: complete
---

# Day 38 - SQLMap Exploitation and WAF Bypass

## What I studied today

- SQLMap exploitation on a real HTB-style web app
- finding hidden endpoints via JavaScript
- working with JSON-based POST requests in SQLMap
- handling time-based blind SQL injection
- using tamper scripts to bypass filtering

---

## Summary of concepts

- Not all vulnerabilities are visible in HTML. Sometimes the real attack surface is hidden in JavaScript, such as AJAX calls.
- SQLMap can handle JSON requests if the correct `--data` value and `Content-Type` header are provided.
- Time-based blind SQLi works by measuring delays, but it is slow and less reliable than visible output-based techniques.
- Some characters, such as `>`, can be filtered by the server and break payloads.
- Tamper scripts like `between` can rewrite payloads to bypass certain filters.

---

## Deeper understanding (optional but recommended)

The request flow in this challenge was important.

The frontend (`shop.html`) used JavaScript to send a POST request:

```json
{"id": 1}
````

to:

```text
/action.php
```

This request was sent as:

```text
POST /action.php
Content-Type: application/json
```

SQLMap needed the request to match that structure:

```bash
sqlmap -u "http://TARGET/action.php" \
  --data='{"id":1}' \
  --headers="Content-Type: application/json"
```

Without matching the exact request format, SQLMap would not reliably detect or exploit the injection.

Since the injection was time-based:

* SQLMap sent payloads involving delays, such as `SLEEP(10)`
* TRUE/FALSE behavior was inferred from response timing
* extraction was slower and more fragile than normal output-based SQLi

---

## What I actually did (important)

* used `curl` to enumerate links and pages
* realized the visible forms were fake (`action="#"`)
* inspected JavaScript manually and found:

```text
action.php
```

* identified JSON POST request with the `id` parameter
* used SQLMap with JSON data and correct headers
* detected time-based blind SQL injection
* increased reliability using:

```bash
--time-sec=10
--technique=T
```

* fixed filtering issue using:

```bash
--tamper=between
```

* enumerated database:

  * found database: `production`
* searched tables:

  * found table: `final_flag`
* dumped table and retrieved the flag

---

## What went well

* successfully pivoted from static HTML to hidden backend endpoint
* correctly interpreted JavaScript to find the real attack surface
* adapted SQLMap to JSON instead of standard GET/POST form data
* understood SQLMap warnings and used `--tamper=between`
* completed the full exploitation chain to get the flag

---

## What was confusing

* why SQLMap initially failed to retrieve database names
* difference between detection working and extraction failing
* handling time-based blind SQLi felt slow and unclear at first
* when to use `--no-cast`, `--hex`, or tamper scripts

---

## Mistakes / friction

* initially focused on visible pages instead of backend logic
* tried SQLMap too early without understanding the request structure
* ignored JavaScript at first, which hid the real endpoint
* did not immediately follow SQLMap’s hint about `--tamper=between`

---

## What I think I understand now

* real vulnerabilities are often hidden in API/backend endpoints, not visible UI
* SQLMap needs the exact request format to work correctly
* time-based blind SQLi is slower but still powerful
* WAF/filtering can break payloads, but tamper scripts can fix that
* enumeration is a step-by-step process:

```text
find injection → confirm → enumerate DB → find tables → dump data
```

---

## What I need to improve

* get faster at spotting hidden endpoints in JavaScript
* practice more with blind SQLi scenarios
* learn when to choose different SQLMap techniques (`B`, `E`, `U`, `T`)
* better understand tamper scripts and when to apply them

---

## Plan for next session

* start Stack-Based Buffer Overflows on Linux x86
* continue work on the P2P backup system

---

## Session info (optional)

* Duration: ~3 hours
* Energy: Medium
