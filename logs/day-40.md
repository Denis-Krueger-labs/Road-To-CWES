---

layout: log
title: "Day 38 - SQLMap Exploitation & WAF Bypass"
date: 2026-04-25
topics: ["SQLMap", "Blind SQLi", "JSON requests", "WAF bypass"]
summary: "Discovered and exploited a JSON-based time-blind SQL injection and bypassed filtering to retrieve the flag."
status: complete
----------------

# Day 38 – SQLMap Exploitation & WAF Bypass

## What I studied today

* SQLMap exploitation on a real HTB-style web app
* Finding hidden endpoints via JavaScript
* Working with JSON-based POST requests in SQLMap
* Handling time-based blind SQL injection
* Using tamper scripts to bypass filtering

---

## Summary of concepts

* Not all vulnerabilities are visible in HTML. Sometimes the real attack surface is hidden in JavaScript (e.g. AJAX calls).
* SQLMap can handle JSON requests if you provide the correct `--data` and `Content-Type` header.
* Time-based blind SQLi works by measuring delays, but it is slow and less reliable than other techniques.
* Some characters like `>` can be filtered by the server, breaking payloads.
* Tamper scripts like `between` rewrite payloads to bypass such filters.

---

## Deeper understanding (optional but recommended)

The request flow in this challenge was important:

* The frontend (`shop.html`) used JavaScript to send a POST request:

  ```json
  {"id": 1}
  ```

  to `action.php`.

* This request was sent as:

  ```text
  POST /action.php
  Content-Type: application/json
  ```

* SQLMap needed:

  * `--data='{"id":1}'`
  * `--headers="Content-Type: application/json"`

Without matching the exact request format, SQLMap would not detect the injection.

Also, since the injection was time-based:

* SQLMap sent payloads like `SLEEP(10)`
* It inferred TRUE/FALSE based on response delay
* That is why extraction was slow and fragile

---

## What I actually did (important)

* Used `curl` to enumerate links and pages
* Realized forms were fake (`action="#"`)
* Inspected JavaScript manually and found:

  ```text
  action.php
  ```
* Identified JSON POST request with `id` parameter
* Used SQLMap with JSON data and correct headers
* Detected time-based blind SQL injection
* Increased reliability using:

  * `--time-sec=10`
  * `--technique=T`
* Fixed filtering issue using:

  * `--tamper=between`
* Enumerated database:

  * found database: `production`
* Searched tables:

  * found table: `final_flag`
* Dumped table and retrieved flag

---

## What went well

* Successfully pivoted from static HTML to hidden backend endpoint
* Correctly interpreted JavaScript to find attack surface
* Adapted SQLMap to JSON instead of standard GET/POST
* Understood SQLMap warnings and used `--tamper=between`
* Completed full exploitation chain to get the flag

---

## What was confusing

* Why SQLMap initially failed to retrieve database names
* Difference between detection working and extraction failing
* Handling time-based blind SQLi felt slow and unclear at first
* When to use `--no-cast`, `--hex`, or tamper scripts

---

## Mistakes / friction

* Initially focused on visible pages instead of backend logic
* Tried SQLMap too early without understanding request structure
* Ignored JavaScript at first, which hid the real endpoint
* Didn’t immediately follow SQLMap hint about `--tamper=between`

---

## What I think I understand now

* Real vulnerabilities are often hidden in API/backend endpoints, not visible UI
* SQLMap needs the exact request format to work correctly
* Time-based blind SQLi is slower but still powerful
* WAF/filtering can break payloads, but tamper scripts can fix that
* Enumeration is a step-by-step process:

  ```text
  find injection → confirm → enumerate DB → find tables → dump data
  ```

---

## What I need to improve

* Get faster at spotting hidden endpoints in JavaScript
* Practice more with blind SQLi scenarios
* Learn when to choose different SQLMap techniques (`B`, `E`, `U`, `T`)
* Better understand tamper scripts and when to apply them

---

## Plan for next session

* Practice another SQLMap lab with different injection type
* Focus on error-based and UNION-based SQLi for comparison
* Try manual exploitation (without SQLMap) for better understanding

---

## Session info (optional)

* Duration: ~2–3 hours
* Energy: Medium to High
