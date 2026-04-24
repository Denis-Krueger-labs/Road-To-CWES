---
layout: log
title: "Day 37 - Presentation Pressure & Advanced SQLMap Tuning"
date: 2026-04-24
topics: ["SQLMap", "SQL Injection", "Attack Tuning", "WAF Bypass", "Presentation Skills", "P2P Systems"]
summary: "Delivered high-pressure LLM security presentation, progressed on P2P project, and deepened understanding of SQLMap tuning, enumeration, and bypass techniques."
status: complete
---

# Day 37 – Presentation Pressure & SQLMap Deep Dive

## What I did today

Today was a mix of performance under pressure and technical work.

- Delivered the **LLM Prompt Injection Defence presentation**
- Continued work on the **P2P backup project**
  - designed a first **network message model**
- Studied and practiced **advanced SQLMap usage**

---

## Presentation experience

This was easily the most intense presentation I’ve had so far.

- Very high mental pressure
- Felt like a “one-shot” situation
- Had to stay focused, structured, and confident under stress

Despite that:

- I got through the full presentation
- Kept structure and timing intact
- Delivered a technically complex topic clearly

---

## P2P Project Progress

- Started designing a **network message model**
- First step towards defining:
  - communication structure
  - data exchange format between peers

This is important because:

> without a clear message model, distributed systems quickly become inconsistent and hard to debug

---

## SQLMap – Advanced Concepts

Today I moved beyond “just using SQLMap” to actually understanding how to control it.

---

### Attack Tuning

SQLMap does not always work out of the box.

Key idea:

- **Vector** = core injection payload  
- **Boundaries** = prefix + suffix wrapping the payload  

Example:

```text
[prefix] UNION SELECT ... [suffix]
````

Used when the injection point requires a specific syntax context.

---

### `--level` and `--risk`

These control how aggressive SQLMap is.

* `--level` (1–5)

  * number of payloads and boundaries
* `--risk` (1–3)

  * how dangerous payloads are

Trade-off:

* Default → fast, safe (~72 payloads)
* Maximum → thorough, slow (~7865 payloads)

---

### Detection vs Exploitation

Mental model:

```text
Detect → Identify technique → Enumerate → Extract data
```

---

### Enumeration Workflow

Typical steps:

```bash
--banner
--current-user
--current-db
--is-dba
--tables -D <db>
--dump -T <table> -D <db>
```

Important:

* finding SQLi ≠ goal
* **data extraction is the real objective**

---

### Data Extraction Types

* **In-band (fast)**

  * UNION / error-based
  * direct output

* **Blind (slow)**

  * bit-by-bit extraction
  * no visible output

---

### Targeted Extraction

Used to reduce noise:

```bash
-C username,password
--start=1 --stop=5
--where="name LIKE 'admin%'"
```

---

### Schema & Search

* `--schema` → database structure
* `--search` → find interesting tables/columns

---

### Bypassing Protections

This was one of the most important parts today.

#### CSRF Tokens

```bash
--csrf-token=<name>
```

But:

* token must match session
* often tied to `PHPSESSID`

---

#### Randomized Parameters

```bash
--randomize=<param>
```

---

#### Calculated Parameters

```bash
--eval="python code"
```

Example:

```bash
--eval="import hashlib; uid=hashlib.md5(id.encode()).hexdigest()"
```

---

#### User-Agent Blocking

```bash
--random-agent
```

---

#### Tamper Scripts

Modify payloads to bypass filters:

```bash
--tamper=between,randomcase
```

Examples:

* `between` → bypass operators
* `space2comment` → bypass spaces
* `randomcase` → evade filters

---

#### WAF / IP Bypass

```bash
--proxy
--tor
--proxy-file
```

---

## What I actually did (important)

* Exploited multiple SQLi scenarios using SQLMap
* Used:

  * `--prefix` / `--suffix`
  * `--level` / `--risk`
  * `--union-cols`
  * `--data` for POST requests
  * `--csrf-token` with non-standard token (`t0ken`)
  * session handling via `PHPSESSID`
  * `--eval` for calculated values
  * `--random-agent`
  * `--tamper=between`
* Performed enumeration and dumping:

  * `--dbs`, `--tables`, `--columns`, `--dump`

---

## What went well

* I did not give up when SQLMap initially failed
* I adapted attack strategy instead of assuming no vulnerability
* I understood when to switch:

  * GET → POST
* Successfully handled:

  * CSRF tokens
  * calculated parameters
* Fixed Python 3 hashing issue (`.encode()`)
* Started thinking in terms of:

  * bypassing defenses
  * not just running tools

---

## What was confusing

* When to use GET vs POST in practice
* Why CSRF handling fails even with correct flag
* Dependency between:

  * CSRF token
  * session cookie
* Limitations of `--csrf-url`
* Why forcing techniques (`--technique=U`) can break detection
* When exactly tamper scripts are needed

---

## Mistakes / friction

* Over-forcing SQLMap techniques too early
* Assuming token handling is always straightforward
* Not immediately considering session dependency
* Needing multiple attempts to find correct bypass combination

---

## What I think I understand now

* SQLMap is not “automatic hacking” it needs tuning
* Most failures are:

  * request setup issues
  * or protection mechanisms
* Real skill is:

  * recognizing *why* it failed
  * and adjusting accordingly
* Web exploitation is often:

  > breaking assumptions, not just running payloads

---

## What I need to improve

* Faster identification of:

  * request structure
  * parameter type (GET vs POST)
* Better intuition for:

  * when to increase `level` and `risk`
* More experience with:

  * tamper scripts
  * WAF behavior
* Stronger understanding of:

  * session + token interaction

---

## Plan for next session

* Finish SQLMap room completely
* Continue work on P2P project
* Review presentation performance

---

## Session info (optional)

* Duration: ~6h
* Energy: Medium (high during presentation, lower after)
