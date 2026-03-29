---
layout: log
title: "Day 11 — Recovery Day, Academy Writeup, File Inclusion, and Light C# Practice"
date: 2026-03-29
topics: ["Recovery Day", "HTB Academy", "File Inclusion", "C#", "Writeups", "Crisis Interruption"]
summary: "A disrupted and emotionally heavy day. Main progress came from documenting the Academy machine, finishing a basic file inclusion room, and doing a small amount of C# practice."
status: complete
---
# Day 11 – Recovery Day, Academy Writeup, File Inclusion, and Light C# Practice

## What I studied today

Today was not a normal study day.

I was dealing with a real-life crisis involving a close friend, which made it very hard to focus. Because of that, this was more of a recovery / maintenance day than a deep technical one.

Even so, I still moved a few things forward:

- finished and documented the HTB machine **Academy**
- completed a basic **file inclusion** room on TryHackMe
- did a small amount of **C#** work in Visual Studio to get back into the language

---

## Summary of concepts

- Some days are not good for deep technical work, and that does not mean progress disappears.
- Writing up a machine properly is also part of training, especially when it forces me to reconstruct the attack chain and explain why each step worked.
- File inclusion basics are feeling easier now, which suggests I am moving past the very introductory level in that topic.
- Light practice in a language like C# still counts, even if it is not a full project session.

---

## Deeper understanding (optional but recommended)

A useful lesson from today is that **documentation is part of learning, not something separate from it**.

The Academy machine was not just “something I rooted.” Writing the report forced me to clearly structure:

- the initial flaw
- the trust boundary failure
- the staging exposure
- the RCE path
- the credential pivot
- the privilege escalation path

That kind of reconstruction is valuable because it trains me to think in chains rather than isolated tricks.

Another important lesson is more personal:

**A disrupted day is not the same thing as a failed day.**

When real life hits hard, maintaining even a little momentum is enough.

---

## What I actually did (important)

### 1. Finished the HTB machine *Academy* and completed the writeup

I finalized the technical report for **Academy**.

Main chain:

- hidden registration parameter manipulation
- administrative access
- staging subdomain discovery
- exposed Laravel debug page
- `APP_KEY` leak
- **CVE-2018-15133** leading to RCE
- credential recovery from `.env`
- SSH pivot
- audit log review
- `composer` sudo abuse to root

This was useful because it reinforced several important web testing themes:

- hidden client-side parameters are not trustworthy
- staging/debug exposure can completely collapse trust boundaries
- app secrets often become the bridge from web access to code execution
- local privilege escalation is often about chaining “boring” findings correctly

### 2. Finished a basic TryHackMe file inclusion room

I completed the file inclusion room on TryHackMe.

Main takeaway:
- it felt easier than expected, which probably means I am already beyond the most basic file inclusion concepts

What I think that means:
- I do not need to stay in very beginner file inclusion material for too long
- I should move toward harder file inclusion contexts, where traversal, wrappers, filters, or chaining matter more

### 3. Did a small amount of C# practice in Visual Studio

I also spent a little time getting back into C#.

This was not a major coding session, but it was still useful as a low-pressure way to reconnect with the language.

---

## What went well

- I still managed to keep the streak alive on a very difficult day.
- The Academy writeup is strong and captures a full web-focused attack chain clearly.
- The file inclusion room confirmed that some beginner material is already below my current level.
- I chose smaller, realistic tasks instead of pretending I could do a full focused grind session.

---

## What was confusing

- Concentration was the biggest issue today, not the technical material itself.
- It was hard to judge what “counts” as enough on a day that was emotionally heavy.
- I still need a better sense of when a room is useful reinforcement vs. when it is too basic for where I am now.

---

## Mistakes / friction

- I was emotionally exhausted and could not focus well.
- Real-life stress made it hard to think clearly or stick to a normal study rhythm.
- I briefly felt guilty for not being able to do more, even though the day was obviously not normal.

---

## What I think I understand now

- A writeup is not just documentation; it is also a way of training attack-chain thinking.
- I am likely past very beginner-level file inclusion rooms.
- Smaller maintenance tasks still matter on bad days.
- Real interruptions do not erase progress.

---

## What I need to improve

- Be kinder and more realistic with myself on crisis days.
- Move file inclusion practice toward harder, more realistic targets instead of very basic rooms.
- Keep using light fallback tasks when I cannot manage deep technical work.
- Continue turning rooted machines into strong reports, because that process clearly helps my understanding.

---

## Plan for next session

- return to the main roadmap with a more normal-energy session
- choose the next file inclusion target or next roadmap target more intentionally
- keep the session focused and manageable

---

## Session info (optional)

- Duration: fragmented / low-focus day
- Energy: very low