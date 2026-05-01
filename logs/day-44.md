---
layout: log
title: "Day 44 - Scheme Basics, Algorithms, and Information Security Foundations"
date: 2026-05-01
topics: ["Algorithms", "Data Structures", "Scheme", "Information Security", "CIA Triad", "ISMS"]
summary: "A strong fundamentals day covering Scheme basics, the first algorithms exercise sheet, and core information security concepts like the CIA triad and ISMS basics."
status: complete
---

# Day 44 – Scheme Basics, Algorithms, and Information Security Foundations

## What I studied today

Today I focused on two main areas:

- Algorithms and Data Structures with Scheme
- Information Security / ISMS fundamentals

This was more of a fundamentals day than a hacking or project day, but it was actually very productive.

---

## Summary of concepts

### Algorithms and Scheme

I started building the basics for Algorithms and Data Structures.

Important ideas:

- an algorithm is basically a structured “recipe” for solving a problem
- Scheme uses prefix notation
- Scheme focuses more on thinking clearly than fighting complex syntax
- expressions are evaluated from the inside outward

Examples:

```scheme
(+ 2 3)
````

means:

```text
2 + 3
```

Nested expressions:

```scheme
(* (+ 2 3) 4)
```

are evaluated by solving the inner expression first.

---

### Scheme basics learned

I practiced:

#### Variables

```scheme
(define x 3)
```

#### Functions

```scheme
(define (f x)
  (+ x 1))
```

#### Conditions

```scheme
(cond ...)
```

#### Predicates

```scheme
(> x 10)
```

Predicates return true or false and are used to make decisions.

---

## What I actually did: Algorithms / Scheme

I completed **Exercise Sheet 1**.

That included:

* translating math expressions into Scheme
* writing my own functions
* debugging and fixing mistakes
* writing predicates
* solving the more difficult task 6

This was a big win because I started the session with resistance toward Scheme, but by the end I was solving tasks and explaining the theory correctly.

---

## Theory understood

### Substitution model

I practiced the idea that function calls can be understood by replacing parameters with actual values and then evaluating the expression.

### Evaluation strategies

I learned the difference between:

* **applicative order** → evaluate arguments first
* **normal order** → substitute first, evaluate later

Short version:

```text
applicative = first calculate
normal = first substitute
```

---

## Information Security foundations

I also reviewed basic Information Security / ISMS concepts.

Main idea:

> Information Security means protecting information from loss, manipulation, and unauthorized access.

The three most important protection goals are the **CIA triad**:

| Goal            | Meaning                                        |
| --------------- | ---------------------------------------------- |
| Confidentiality | only authorized people can access information  |
| Integrity       | data remains correct and unchanged             |
| Availability    | systems and data remain accessible when needed |

---

## Threat examples

I matched common threats to CIA goals:

| Threat                 | Main affected goal |
| ---------------------- | ------------------ |
| Insider / Data Leakage | Confidentiality    |
| Man-in-the-Middle      | Integrity          |
| DDoS                   | Availability       |

---

## Deeper understanding

One important thing I understood today:

**Security is not only about technology.**

It also includes:

* people
* behavior
* processes
* management
* risk decisions

Another key point:

> 100% security is not possible.

Risks never disappear completely, and security also has to make economic and practical sense.

---

## What I actually did: Information Security

* reviewed Information Security basics
* learned / repeated CIA triad concepts
* matched threats to security goals
* discussed why security is broader than just tools
* created 10 flashcards about:

  * CIA triad
  * threats
  * ISMS
  * technology vs. human factors

---

## What went well

* Scheme started to make much more sense
* I completed the full first exercise sheet
* I fixed mistakes instead of getting stuck
* I understood the substitution model better
* I built first exam-ready answers for Information Security basics
* I made useful flashcards for later review

---

## What was challenging

* I had resistance toward Scheme at the beginning
* Prefix notation felt strange at first
* Nested expressions required careful reading
* Some theory only clicked after doing examples

---

## What I think I understand now

* Scheme expressions follow a clear structure:

  ```text
  (operator arguments)
  ```
* inner expressions are evaluated first
* `define` gives a name to a value or function
* functions are reusable patterns
* predicates help decide true / false conditions
* Information Security is about confidentiality, integrity, and availability
* ISMS thinking includes humans and processes, not just technical controls

---

## What I need to improve

* keep practicing Scheme regularly so it feels less alien
* do more small exercises with nested expressions
* review substitution model again before the exam
* continue using flashcards for Information Security definitions
* practice formulating short exam-style answers

---

## Plan for next session

* continue Scheme practice
* review the next Algorithms and Data Structures topic
* repeat CIA triad / ISMS flashcards
* keep exercises small and manageable

---

## Session info

* Duration: focused learning session
* Energy: Medium
