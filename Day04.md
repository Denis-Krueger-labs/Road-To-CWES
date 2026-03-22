
# Day 04  Backend Components, APIs, CVEs, and JavaScript Deobfuscation

## What I studied today

Today I focused on:

- backend servers, web servers, databases, and development frameworks
- web APIs, including REST and SOAP
- common web vulnerabilities, public CVEs, and CVSS scoring
- JavaScript obfuscation, deobfuscation, and basic code analysis

---

## Summary of concepts

- The backend is the part of a web application that handles the core logic, processes requests, interacts with databases, and exposes functionality to the frontend.
- Web servers handle HTTP traffic between the client and the application and return responses like `200 OK`, `404 Not Found`, or `500 Internal Server Error`.
- Databases store application and user data. SQL databases use structured tables and relationships, while NoSQL databases are more flexible and often better suited to unstructured data.
- Most modern web applications are built with frameworks, which provide common functionality and make development faster and more consistent.
- APIs allow the frontend or other systems to interact with backend functionality. REST usually uses HTTP methods and JSON, while SOAP is more XML-based and structured.
- Public CVEs are officially disclosed vulnerabilities with unique identifiers. CVSS is used to estimate how severe a vulnerability is.
- JavaScript obfuscation is used to make code harder to read, but the logic often still becomes clear after beautifying or unpacking it.

---

## Deeper understanding (optional but recommended)

One important idea from today is that the **frontend should never be treated as trusted**.

Even though users interact with the frontend, the backend is where important decisions happen:
- authentication
- authorization
- database access
- API processing
- sensitive logic

That means anything coming from the browser should be treated as untrusted input. A user can inspect source code, modify requests, alter parameters, or replay actions manually with tools like `curl`. From a security perspective, this is why backend validation matters much more than assuming the frontend will behave correctly.

---

## What I actually did (important)

- Used `curl` to inspect headers and page content from a real target:

```bash
curl -I https://academy.hackthebox.com
curl https://academy.hackthebox.com
````

* Sent a manual `GET` request to a vulnerable-style parameterized endpoint:

```bash
curl -X GET http://<Target_IP>/index.php?id=1
```

This reinforced how parameters are passed directly into backend functionality and why input handling matters.

* Checked page source and found hidden content in comments:

```html
<------HTB{[REDACTED]}------->
```

* Worked through a JavaScript deobfuscation exercise and unpacked obfuscated code to reveal the real function logic. After deobfuscation, the script looked like this:

```js
function generateSerial() {
  var flag = "HTB{[REDACTED]}";
  var xhr = new XMLHttpRequest();
  var url = "/serial.php";
  xhr.open("POST", url, true);
  xhr.send(null);
}
```

* Replicated the JavaScript behavior manually with `curl` by sending the same `POST` request to the endpoint:

```bash
curl -s -X POST http://SERVER_IP:PORT/serial.php
```

* Received an encoded value, identified it as base64, decoded it, and then reused the decoded value as input in a second request:

```bash
curl -X POST -d "serial=[REDACTED]" http://SERVER_IP:PORT/serial.php
```

This was one of the most useful parts of the session because it tied together:

* source code review

* JavaScript analysis

* manual request replication

* decoding and reuse of returned data

* Looked up public vulnerabilities like **CVE-2014-6271 (Shellshock)** and **CVE-2017-0144 (EternalBlue)** to get more comfortable researching known vulnerabilities and reading CVSS severity information.

* Connected Shellshock to a previous lab/box path:
  `Nmap → Gobuster (/cgi-bin/user.sh) → ShellShock → shell → sudo perl (GTFOBins) → root`

* Also spent some time on a separate custom CTF challenge today, which was outside the main module topic but still useful practical work. It reinforced how much enumeration, logic, and patience matter when a challenge is built around chained information disclosure rather than brute force.

---

## What went well

* Using `curl` more actively helped the HTTP and API material feel much more practical.
* The JavaScript deobfuscation exercises were useful because they combined code reading, request analysis, and decoding in one workflow.
* I was able to connect theory (web requests, source code, CVEs) to practical actions instead of only taking notes.
* My energy stayed high during the session, which made it easier to experiment and stay engaged.

---

## What was confusing

* I briefly mixed up syntax while using `curl`, especially when sending a `POST` request.
* During the deobfuscation section, it was initially unclear whether I had found the correct hidden value or whether I was still looking at a decoy.
* Some of the backend and framework sections were conceptually clear but still felt a little broad and list-heavy.

---

## Mistakes / friction

* I forgot the `-` in `curl -X POST` at one point and wasted time wondering why the command was not working.
* Some of the module content was dense, which made it tempting to copy too much instead of compressing it into my own wording.
* I gave myself too many options for the next topic instead of ending with one clear next step.

---

## What I think I understand now

* The backend is where application trust boundaries really matter, because it handles logic, data, and security-sensitive actions.
* Web servers are not just “sites”; they are active components that receive requests, route them, and return different kinds of responses depending on what happens.
* APIs are one of the main ways frontend and backend parts communicate, and tools like `curl` make that interaction easier to inspect and reproduce manually.
* JavaScript deobfuscation is not just about making code look nicer — it is about figuring out what functionality is hidden, what requests are being made, and what an attacker or tester can replicate manually.
* Public CVEs become much easier to understand when I connect them to real attack paths or previous labs instead of treating them like isolated IDs.

---

## What I need to improve

* Compress broad theory sections more aggressively into key ideas instead of rewriting too much of the module.
* Practice `curl` syntax until simple request crafting feels automatic.
* Get more confident recognizing when obfuscated code is hiding the real logic versus a fake or partial clue.
* Pick one next topic at the end of the session instead of leaving myself too many branches.

---

## Plan for next session

* Start **SQL Injection Fundamentals**
* Keep the session focused on one topic only
* Continue mixing theory with manual interaction and request testing

---

## Session info (optional)

* Duration: ~2 hours with a short break
* Energy: High

