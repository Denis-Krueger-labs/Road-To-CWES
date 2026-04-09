---
layout: log
title: "Day 22 - XSS + Project Progress (README & P2P Work)"
date: 2026-04-09
topics: ["XSS", "Stored XSS", "Reflected XSS", "DOM XSS", "JavaScript", "Web Security", "Project Work", "Documentation"]
summary: "Worked through XSS fundamentals and payloads while also making progress on the P2P backup project and completing the README."
status: complete
---
# Day 22 - XSS + Project Progress

## What I studied today

- Cross-Site Scripting (XSS)
- Stored, Reflected, and DOM-based XSS
- JavaScript execution in the browser
- continued work on P2P backup project
- wrote and finished project README

---

## Summary of concepts

- XSS happens when user input is not properly sanitized and gets executed in the browser
- it is a **client-side vulnerability**
- allows execution of JavaScript in another user’s session
- can be used to:
  - steal session cookies
  - manipulate pages
  - perform actions as the victim

### XSS Types

| Type | Description |
|---|---|
| Stored XSS | Payload is stored on backend and affects all users |
| Reflected XSS | Payload is reflected immediately in response |
| DOM XSS | Payload is handled entirely in browser via JavaScript |

---

## Deeper understanding

Key concept today:

**Where is the payload processed?**

- Stored → backend + database  
- Reflected → backend response  
- DOM → frontend JavaScript  

Also:

**Source → Sink**

- Source = user-controlled input  
- Sink = where it gets written into the DOM  

Unsafe sinks:
- `innerHTML`
- `document.write()`
- `outerHTML`

---

## What I actually did (important)

### XSS

- tested:
```html
  <script>alert(document.cookie)</script>
```

* reflected XSS via:

  ```text
  http://SERVER_IP:PORT/index.php?task=<script>alert(document.cookie)</script>
  ```

* DOM-based payload:

  ```html
  <img src="" onerror=alert(document.cookie)>
  ```

---

### Project Work (important)

* continued working on **P2P backup system project**
* participated in ongoing development discussions
* **finished writing the README**

This is important because:

* documentation is part of real-world engineering
* README = first thing others (or recruiters) see
* turns code into something usable and understandable

---

## What went well

* XSS concepts clicked much better
* payload testing felt intuitive
* made real progress on project (not just theory)
* finishing README felt like an actual milestone

---

## What was confusing

* still mixing up reflected vs DOM XSS sometimes
* need more repetition to instinctively recognize context

---

## Mistakes / friction

* forgot to reset session cookie → misleading results
* still defaulting to simple payloads instead of experimenting further

---

## What I think I understand now

* XSS is about unsafe rendering of user input in browser context
* the main difference between XSS types is **where execution happens**
* DOM XSS = frontend problem, not backend
* practical testing is the fastest way to understand web vulns

---

## What I need to improve

* practice identifying XSS context faster
* move beyond `alert()` to more realistic payloads
* continue building project + documentation habit

---

## Plan for next session

* finish XSS module
* test more payload variations
* continue project work if time allows

---

## Session info (optional)

* Duration: ~2h
* Energy: Medium
