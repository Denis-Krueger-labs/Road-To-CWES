---
layout: log
title: "Day 02 - APIs, CRUD Operations, and First API Interaction"
date: 2026-03-20
topics: ["APIs", "CRUD", "HTTP Methods", "JSON", "jq", "Web Applications"]
summary: "Moved from theory into actually interacting with a web API using cURL — GET, PUT, DELETE, and JSON responses."
status: complete
---

## What I studied today

Today I focused on:

- APIs (Application Programming Interfaces)
- CRUD operations
- interacting with APIs using HTTP methods
- basic web application concepts
- architecture and common security risks

The goal was to move from theory into actually interacting with a web API.

---

## API (Application Programming Interface)

An API is an **interface that allows different software systems to communicate with each other**.

In web applications, APIs usually:
- expose endpoints (URLs)
- accept HTTP requests
- return structured responses (often JSON)

---

## CRUD operations

| Operation | HTTP Method | Description |
|----------|------------|-------------|
| Create   | POST       | Add new data |
| Read     | GET        | Retrieve data |
| Update   | PUT        | Modify existing data |
| Delete   | DELETE     | Remove data |

These operations act on **resources exposed by the API**, not directly on database rows (even though they often map to them internally).

---

## Web application architecture

Typical layers:

- **Presentation layer** → what the user sees
- **Application layer** → logic and processing
- **Data layer** → storage (databases)

Vulnerabilities can exist in any layer, and not all issues are coding mistakes — some are design flaws.

---

## Common web application risks

- SQL Injection
- File Inclusion
- Unrestricted File Upload
- IDOR (Insecure Direct Object Reference)
- Broken Access Control

---

## What I actually did

### Reading data (GET)

```bash
curl http://<TARGET>/api.php/city/london | jq
```

Response:

```json
[
  {
    "city_name": "London",
    "country_name": "(UK)"
  }
]
```

### Updating data (PUT)

```bash
curl -X PUT http://<TARGET>/api.php/city/london \
  -d '{"city_name":"New_City","country_name":"Test"}' \
  -H 'Content-Type: application/json'
```

This showed how request bodies work and why `Content-Type` matters.

### Deleting data

```bash
curl -X DELETE http://<TARGET>/api.php/city/<NAME>
```

### Key takeaway

> Changing the request (method, body, headers) directly changes server behavior. This is where web security testing actually starts.

---

## What went well

* Moved from theory to actually interacting with an API
* CRUD operations made more sense after using them in practice
* cURL + jq made responses easier to understand

## What was confusing

* Nothing much — the theory block was just large today

## What I need to improve

* More hands-on experimentation instead of just reading
* Staying focused during longer sessions
* Read the environment more carefully before assuming setup issues

## Plan for next session

* Continue with the web applications module
* Focus on frontend vs backend concepts
* Spend time actively experimenting with requests

## Session info

* Duration: ~3 hours
* Energy: Low — next time keep sessions shorter and more focused
