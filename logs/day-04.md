---
layout: log
title: "Day 04 — Backend Components, APIs, CVEs, and JavaScript Deobfuscation"
date: 2026-03-22
topics: ["Backend", "Web Servers", "Databases", "REST API", "CVEs", "JavaScript Deobfuscation", "Base64"]
summary: "Backend architecture, public CVEs, and a full JavaScript deobfuscation workflow — source review, request replication, and decoding chained together."
status: complete
---

## What I studied today

- backend servers, web servers, databases, and development frameworks
- web APIs, including REST and SOAP
- common web vulnerabilities, public CVEs, and CVSS scoring
- JavaScript obfuscation, deobfuscation, and basic code analysis

---

## Summary of concepts

- The **backend** handles core logic, processes requests, interacts with databases, and exposes functionality to the frontend.
- **Web servers** handle HTTP traffic and return responses like `200 OK`, `404 Not Found`, or `500 Internal Server Error`.
- **Databases** store application and user data. SQL databases use structured tables; NoSQL databases are more flexible.
- Most modern web applications are built with **frameworks** that provide common functionality.
- **REST** usually uses HTTP methods and JSON. **SOAP** is more XML-based and structured.
- **CVEs** are officially disclosed vulnerabilities with unique identifiers. **CVSS** estimates severity.
- **JavaScript obfuscation** makes code harder to read, but the logic often becomes clear after beautifying or unpacking.

---

## Key insight

> The frontend should never be treated as trusted.

Even though users interact with the frontend, the backend is where important decisions happen — authentication, authorization, database access, API processing. A user can inspect source code, modify requests, alter parameters, or replay actions manually with tools like `curl`. Backend validation matters far more than assuming the frontend will behave correctly.

---

## What I actually did

### Inspected headers and page content

```bash
curl -I https://academy.hackthebox.com
curl https://academy.hackthebox.com
```

### Sent a manual GET request to a parameterized endpoint

```bash
curl -X GET http://<Target_IP>/index.php?id=1
```

This reinforced how parameters are passed directly into backend functionality and why input handling matters.

### Found hidden content in source code

```html
<------HTB{[REDACTED]}------->
```

### JavaScript deobfuscation workflow

After deobfuscation, the script revealed:

```js
function generateSerial() {
  var flag = "HTB{[REDACTED]}";
  var xhr = new XMLHttpRequest();
  var url = "/serial.php";
  xhr.open("POST", url, true);
  xhr.send(null);
}
```

### Replicated the JavaScript behavior with cURL

```bash
curl -s -X POST http://SERVER_IP:PORT/serial.php
```

Received an encoded value, identified it as base64, decoded it, and reused the decoded value:

```bash
curl -X POST -d "serial=[REDACTED]" http://SERVER_IP:PORT/serial.php
```

This was one of the most useful parts of the session — it tied together source code review, JavaScript analysis, manual request replication, and decoding chained together.

### Researched public CVEs

- **CVE-2014-6271 (Shellshock)** — bash environment variable injection
- **CVE-2017-0144 (EternalBlue)** — SMB exploit used in WannaCry

Connected Shellshock to a previous lab path:
```
Nmap → Gobuster (/cgi-bin/user.sh) → ShellShock → shell → sudo perl (GTFOBins) → root
```

Also worked on a separate custom CTF challenge — reinforced how much enumeration, logic, and patience matter when a challenge is built around chained information disclosure rather than brute force.

---

## What went well

* Using cURL more actively made the HTTP and API material feel much more practical
* The JavaScript deobfuscation exercises combined code reading, request analysis, and decoding in one workflow
* Connected theory to practical actions instead of only taking notes
* Energy stayed high, making it easier to experiment and stay engaged

## What was confusing

* Briefly mixed up cURL syntax when sending POST requests
* Initially unclear whether I had found the correct hidden value or a decoy during deobfuscation
* Some backend/framework sections felt broad and list-heavy

## Mistakes / friction

* Forgot the `-` in `curl -X POST` at one point
* Tempted to copy too much module content instead of compressing into my own words
* Gave myself too many options for the next topic instead of one clear next step

## What I need to improve

* Compress broad theory sections more aggressively into key ideas
* Practice cURL syntax until simple request crafting feels automatic
* Pick one next topic at the end of each session

## Plan for next session

* Start **SQL Injection Fundamentals**
* Keep the session focused on one topic only
* Continue mixing theory with manual interaction and request testing

## Session info

* Duration: ~2 hours with a short break
* Energy: High
