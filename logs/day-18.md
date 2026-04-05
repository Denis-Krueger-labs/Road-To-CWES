---
layout: log
title: "Day 18 - Web Reconnaissance, DNS, WHOIS, and Virtual Host Discovery"
date: 2026-04-05
topics: ["Web Reconnaissance", "DNS", "WHOIS", "dig", "dnsenum", "VHosts", "Subdomains", "Zone Transfers"]
summary: "A recon-focused day covering passive and active web reconnaissance, DNS fundamentals, WHOIS, subdomain discovery, zone transfers, and virtual host enumeration."
status: complete
---
# Day 18 – Web Reconnaissance, DNS, WHOIS, and Virtual Host Discovery

## What I studied today

Today I focused on:

- web reconnaissance as a foundation for web security testing
- passive vs active reconnaissance
- WHOIS and DNS basics
- DNS records and DNS tools
- subdomain enumeration
- zone transfers
- virtual host discovery

---

## Summary of concepts

- Web reconnaissance is the foundation of a thorough security assessment.
- The goal is to systematically gather information before moving into deeper testing or exploitation.
- Passive recon gathers information without directly interacting much with the target.
- Active recon interacts with the target more directly and has a higher chance of detection.
- DNS and WHOIS can reveal a surprising amount of useful information:
  - domains
  - name servers
  - mail servers
  - subdomains
  - infrastructure hints
- Virtual hosts and subdomains are related, but they are not the same thing:
  - subdomain = DNS concept
  - VHost = web server concept

---

## Deeper understanding (optional but recommended)

The most important thing I want to keep from today is this:

**DNS gets me to the server. The Host header tells the server which website I want.**

That sounds simple, but it explains a lot of web enumeration:

- a domain can resolve correctly but still not show the right content if the correct VHost is missing
- a VHost can exist on a server even if there is no public DNS record for it
- subdomain brute forcing and VHost brute forcing are therefore related, but they are solving different problems

Another important point is that recon is not “just setup work.”  
It is often the phase that makes everything else possible later.

---

## What I actually did (important)

- used `whois` to look up registration and infrastructure-related information on different domains
- used `dig` to retrieve:
  - IP addresses
  - mail exchange records
  - other DNS information
- used `dnsenum` to brute-force subdomains
- used `dig` to perform a zone transfer
- used `gobuster` to brute-force virtual hosts

This session was mainly about getting more comfortable with recon workflow and the different places where useful information can be found before exploitation even starts.

---

## What went well

- using the tools felt natural enough
- the relationship between DNS, hosts files, and VHosts is starting to make more sense
- recon is starting to feel more like a structured process instead of random commands

---

## What was confusing

- the zone transfer part was explained much more clearly in theory than in practice
- I got distracted and accidentally turned part of the session into a rave

---

## Mistakes / friction

- I could have spent more time connecting the theory directly to realistic recon workflows
- some parts of the room felt more descriptive than hands-on
- distraction definitely cut into the focus of the session

---

## What I think I understand now

- passive and active recon serve different purposes and carry different detection risks
- WHOIS and DNS are both useful early recon sources
- subdomains and VHosts are not interchangeable
- recon is not optional background work; it directly shapes the rest of testing

---

## What I need to improve

- get more practical repetition with DNS zone transfers and recon workflows
- stay more focused during slower theory-heavy modules
- continue building a cleaner mental model for how DNS, Host headers, and VHosts fit together

---

## Plan for next session

- finish the information gathering room
- keep recon practical and tied to real attack paths

---

## Session info (optional)

- Duration: ~4 hours
- Energy: Low
