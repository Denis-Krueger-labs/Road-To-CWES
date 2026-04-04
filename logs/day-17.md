---
layout: log
title: "Day 17 - Web Proxies, Burp/ZAP Workflow, and Practical Request Manipulation"
date: 2026-04-04
topics: ["Burp Suite", "ZAP", "Web Proxies", "Request Manipulation", "Fuzzing", "Web Security"]
summary: "A fast-paced session reinforcing proxy fundamentals, request manipulation, fuzzing, and comparing Burp Suite with ZAP."
status: complete
---
# Day 17 – Web Proxies, Burp/ZAP Workflow, and Practical Request Manipulation

## What I studied today

Today focused on:

- web proxies and their role in web testing  
- Burp Suite workflow (intercept → modify → repeat → fuzz)  
- basic ZAP exploration  
- request manipulation in real scenarios  
- fuzzing through a proxy  

---

## Summary of concepts

- Web proxies act as a **man-in-the-middle (MITM)** between client and server  
- They allow:
  - interception  
  - inspection  
  - modification  
  - replaying requests  

- Most proxies operate over:
  - HTTP (port 80)  
  - HTTPS (port 443)  
  - but are not limited to those  

- Core use cases:
  - request/response analysis  
  - fuzzing  
  - vulnerability testing  
  - application mapping  

---

## Key insight

> Burp (or any proxy) is not the skill.  
> The skill is understanding **what to change in a request and why**.

---

## Tools explored

### Burp Suite
- very intuitive workflow  
- strong ecosystem  
- built-in Chromium browser  
- Repeater + Intruder are essential  

### OWASP ZAP
- open source  
- lightweight compared to Burp  
- extremely feature-rich  
- feels powerful but less intuitive at first  

---

## What I actually did (important)

- Set up both **Burp Suite and ZAP**  
- Intercepted requests and modified input to execute a command:
  - identified current directory  
  - retrieved flag  

- Used **Repeater** to:
  - quickly test multiple payloads  
  - avoid re-intercepting every request  

- Decoded a value encoded **4 times (quad base64)** to retrieve a flag  

- Used **Burp Intruder (Sniper attack)**:
  - fuzzed parameters  
  - identified a weak cookie mechanism  
  - discovered cookie = username hashed with MD5  
  - used that to access another user  

- Explored ZAP features:
  - initial impression: powerful but confusing  
  - potential future switch depending on workflow  

- Completed the **HTB Web Proxies module** in roughly half the estimated time  

---

## Extra: Box rooted (HTB – Secret)

- Completed the **Secret** machine (Linux, Easy)
- Focus areas:
  - Git history analysis
  - JWT forgery
  - command injection
  - SUID privilege escalation via core dumps

### Key takeaways

- Git history is a goldmine — deleting secrets ≠ removing them  
- JWT trust is dangerous when based only on client-controlled claims  
- command injection in backend tools (`git log`) is easy to miss but critical  
- core dump exploitation is insane — crashing a SUID binary to leak memory is something I hadn’t done before  

### Attack chain (simplified)

Git leak → JWT secret → admin token → command injection → shell → SUID core dump → root

---

Full writeup available on my page.

---

## What went well

- Burp usage felt completely natural  
- chaining actions (intercept → modify → repeat → fuzz) felt fluid  
- recognized patterns instead of learning from scratch  
- finished the module quickly  
- reached **~34% completion of the Web Penetration Tester path**  
- 8/20 modules done → strong progress  

---

## What was confusing

- most content felt obvious, but translating that into documentation was harder  
- using Burp for directory fuzzing feels inefficient compared to ffuf  
- ZAP is powerful but has a confusing interface initially  
- scanning features feel almost “too strong” needs deeper understanding  
- unclear why proxying through tools like Metasploit would be preferred over direct use  

---

## Mistakes / friction

- underestimating the value of reviewing basics  
- slight confusion when switching between tools (Burp vs ZAP mindset)  
- still refining when to use which tool efficiently  

---

## What I think I understand now

- proxies are about **control over communication**, not just interception  
- Repeater is one of the most powerful tools for controlled testing  
- fuzzing through a proxy is useful, but not always the most efficient method  
- tool choice matters less than understanding request flow  

---

## What I need to improve

- get more comfortable with ZAP workflow  
- decide when to use:
  - Burp  
  - ZAP  
  - ffuf  
- deepen understanding of automated scanning vs manual testing  

---

## Plan for next session

- Information Gathering Web Edition  

---

## Session info (optional)

- Duration: ~3h  
- Energy: High  

---

## Small note

> Do not underestimate how much better things go with the right music playing 
