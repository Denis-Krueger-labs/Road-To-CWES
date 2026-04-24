---
layout: log
title: "Day 36 - ITCS Job Fair & LLM Presentation Refinement"
date: 2026-04-23
topics: ["LLM Security", "Prompt Injection", "Presentation Skills", "Networking"]
summary: "Attended ITCS job fair, spoke with multiple companies, and fully rewrote the presentation script for LLM prompt injection defence."
status: complete
---

# Day 36 – ITCS Job Fair & Presentation Work

## What I did today

Today was less hands-on technical work and more focus on communication and networking.

- Attended the **ITCS job fair**
- Spoke with multiple companies about roles, tech stacks, and expectations
- Rewrote my entire **LLM Prompt Injection Defence presentation script**

---

## Summary of concepts (LLM Security)

The presentation focuses on **Prompt Injection**, a vulnerability where malicious instructions are hidden inside data that a language model processes.

Key ideas:

- The problem is **not the user prompt**, but the **data the model reads**
- LLMs cannot reliably distinguish between:
  - instructions
  - and untrusted content
- This leads to unintended behavior

Typical risks:

- manipulated outputs
- data leakage
- incorrect decisions in workflows

Core insight:

> **Data and instructions are not clearly separated for the model**

---

## Structure of the presentation

I structured the talk as a clear narrative:

1. **Real-world scenario**  
   → harmless prompt (“summarize this email”)

2. **Problem introduction**  
   → hidden instructions inside the data

3. **Definition**  
   → what Prompt Injection actually is

4. **Relevance**  
   → why this matters in real systems

5. **Attack surface**  
   → emails, websites, documents

6. **Impact**  
   → from wrong answers to real damage

7. **Root cause**  
   → no clear separation between data and commands

8. **Why it’s hard**  
   → models are designed to follow instructions

9. **Conclusion**  
   → no single defence is sufficient

---

## What I actually improved (important)

- Rewrote the full script for clarity and flow
- Reduced complexity without losing technical meaning
- Focused on:
  - shorter sentences
  - clearer transitions
  - stronger key statements
- Balanced:
  - technical accuracy
  - understandable language for a mixed audience

---

## What went well

- The presentation now feels **coherent and structured**, not just informative
- I can explain the topic without relying on slides
- Timing per slide is consistent (~17–19 seconds)
- The core message is clear:
  - problem → cause → impact → limitation of defenses

- Job fair was productive:
  - got a better feeling for industry expectations
  - practiced talking about technical topics in a real-world context

---

## What was challenging

- Translating a **complex security problem** into simple language without oversimplifying
- Finding the balance between:
  - technical depth
  - and clarity
- Avoiding “buzzword explanations” and instead explaining actual mechanisms
- Keeping the explanation precise while staying within time limits

---

## Mistakes / friction

- Initially overcomplicated explanations
- Some sentences were too long and unclear
- Took longer than expected to refine wording
- Switching between networking and deep focus made it harder to stay in flow

---

## What I think I understand now

- Prompt Injection is fundamentally a **context confusion problem**
- LLMs follow instructions well which is exactly why they are vulnerable
- Security for LLMs is not about a single fix, but about **layered defenses**
- Communication is just as important as technical understanding:
  - if I can’t explain it clearly, I don’t fully understand it yet

---

## What I need to improve

- Practice explaining technical topics even more concisely
- Get comfortable presenting without relying on memorized text
- Improve confidence in speaking freely while keeping structure
- Continue linking:
  - web security concepts
  - with AI/LLM security

---

## Plan for next session

- Final rehearsal for the presentation
- Prepare answers for possible discussion questions
- Finish SQLMap Essentials
- Finish XSS room

---

## Session info (optional)

- Duration: full day (job fair + prep)
- Energy: Medium
