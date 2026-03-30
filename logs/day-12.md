---
layout: log
title: "Day 12 - Local File Inclusion, Path Traversal, and Simple Filter Bypasses"
date: 2026-03-30
topics: ["LFI", "Path Traversal", "PHP Filters", "Filter Bypass", "Web Security", "Reverse Engineering", "Buffer Overflow"]
summary: "A focused low-energy session on local file inclusion, traversal, and simple filter bypasses, plus a small amount of reverse-engineering work for university."
status: complete
---
# Day 12 – Local File Inclusion, Path Traversal, and Simple Filter Bypasses

## What I studied today

Today I focused on:

- local file inclusion (LFI)
- path traversal
- simple traversal filter bypasses
- PHP filters / wrappers
- a small amount of reverse engineering for university

---

## Summary of concepts

- Local File Inclusion (LFI) happens when user-controlled input affects which local file an application reads or includes.
- A common pattern is when applications dynamically load content like language files, templates, or page components based on a parameter.
- Path traversal sequences like `../` can be used to escape the intended directory and access files elsewhere on the system.
- Some applications try to block simple traversal patterns, which means bypasses like doubled traversal sequences, mixed separators, or encoding can become useful.
- PHP filters / wrappers can sometimes be used to turn file inclusion into source disclosure, especially when direct inclusion does not return useful readable output.

---

## Deeper understanding (optional but recommended)

The main idea I want to keep from today is:

**LFI is dangerous because it turns file paths into input surfaces.**

If an application trusts user input too much when building a file path, it may allow me to:
- read unintended local files
- escape the intended directory
- disclose source code or configuration
- sometimes move toward code execution, depending on the function and application behavior

The decision process matters too:

1. try direct file inclusion
2. if path restrictions exist, try traversal
3. if traversal is filtered, try bypasses
4. if the target is PHP and source disclosure matters, try wrappers like `php://filter/...`

That helps make the topic feel less like random tricks and more like a structured workflow.

---

## What I actually did (important)

- Used LFI against a test page to read local files from the target system
- Retrieved usernames from `/etc/passwd`
- Used path traversal to reach another directory and read a `flag.txt` file
- Tried different simple traversal bypass techniques to get around basic filters
- Practiced identifying when direct inclusion works and when bypasses are needed

### Extra: university work

I also did a small amount of reverse engineering / OS exploitation work for university:

- used `objdump` on a simple C binary
- identified the address of a function of interest
- used that information in a buffer overflow script to redirect execution to the hidden function

This was separate from the web topic, but still a useful low-volume technical task for the day.

---

## What went well

- I got useful hands-on repetition with LFI and traversal
- Reading local files and bypassing simple filters felt more intuitive than before
- The extra reverse-engineering task was a nice way to keep some momentum in university work without overloading myself

---

## What was confusing

- I am still building intuition for when to use which bypass technique
- I still felt more exhausted than I expected, even for a smaller session

---

## Mistakes / friction

- I started later than planned because I fell asleep
- I still tend to overcomplicate things before trying the simpler explanation first
- Low energy made it harder to think cleanly and calmly

---

## What I think I understand now

- LFI is really about unsafe trust in user-controlled file paths
- Path traversal is often the bridge from “local include” to “interesting file access”
- Basic filter bypasses are not random magic; they are just ways of getting around weak pattern matching
- PHP wrappers are especially useful when I want source disclosure rather than normal inclusion behavior

---

## What I need to improve

- build a cleaner decision tree for traversal bypasses
- keep trying the simple explanation before assuming the app is doing something more complicated
- continue practicing file inclusion in slightly harder contexts so the workflow becomes more natural

---

## Plan for next session

- finish the path traversal / file inclusion room
- keep the next session focused and low-chaos

---

## Session info (optional)

- Duration: ~1 hour
- Energy: Low

---

## Small reflection

> ⁺‧₊˚ ཐི⋆♱⋆ཋྀ ˚₊‧⁺ \
> Sometimes the people who smile the brightest carry the deepest pain. \
> For ianotouta  a reminder to remember you not by your hardest moment, but by who you were beyond it.
