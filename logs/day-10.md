---
layout: log
title: "Day 10 - Fuzzing in Practice, Recursive Enumeration, and Output Filtering"
date: 2026-03-28
topics: ["Fuzzing", "ffuf", "Recursive Enumeration", "Filtering", "vhosts", "Web APIs"]
summary: "Hands-on fuzzing session using ffuf, wenum, and recursive enumeration. Learned how to filter noise, validate findings, and deal with real-world lab friction."
status: complete
---

# Day 10 – Fuzzing in Practice, Recursive Enumeration, and Output Filtering

## What I studied today

- directory and file fuzzing  
- recursive fuzzing  
- parameter and value fuzzing  
- virtual host and subdomain fuzzing  
- filtering fuzzing results effectively  
- differences between web servers and APIs  

---

## Summary of concepts

- Fuzzing is not just about sending requests, but about **interpreting results efficiently**.  
- Recursive fuzzing allows deeper exploration of a web application but increases complexity and runtime significantly.  
- Filtering is essential to reduce noise and focus on meaningful responses.  
- Different filters (status code, size, words, lines, time) help isolate interesting behavior.  
- APIs differ from traditional web servers in structure, data format (JSON/XML), and interaction model.  

---

## Deeper understanding (optional but recommended)

The biggest takeaway today:

> **Fuzzing without filtering is useless.**

Raw fuzzing output becomes overwhelming very quickly:
- thousands of responses  
- repeated patterns  
- false positives  

The actual workflow is:

1. fuzz  
2. observe baseline patterns  
3. filter aggressively  
4. investigate anomalies  

This turns fuzzing from brute force into **structured enumeration**.

---

## What I actually did (important)

- Created a structured **9-month CWES roadmap** with weekly targets  
- Used `ffuf` for:
  - directory fuzzing  
  - file discovery  
  - filtering by status codes and response size  
- Performed **recursive fuzzing** to discover deeper paths  
- Used `wenum` as an additional fuzzing tool  
- Validated findings using:
  - `curl -I` for response inspection  
- Completed the fuzzing module on HTB  

---

## What went well

- First real hands-on fuzzing session  
- Learned how to reduce noise using filtering  
- Successfully completed a complex fuzzing lab  
- Started thinking in **methodology instead of tool usage**  

---

## What was confusing

- Recursive fuzzing behavior and depth handling  
- Distinguishing real findings from noise  
- When to stop recursion vs. continue deeper  

---

## Mistakes / friction

- Recursive fuzzing is extremely slow and resource-heavy  
- Large wordlists without filtering created unnecessary noise  
- Forgot to include vhost fuzzing early  
- Pushed through exhaustion instead of taking breaks  

---

## What this session actually taught me (besides suffering)

1. **DNS and Host headers are not the same thing.**  
   `http://FUZZ.site` needs DNS resolution  
   `-H "Host: FUZZ.site"` only changes the HTTP header after connecting  

---

2. **Vhost fuzzing and directory fuzzing are different jobs.**  
   - vhost fuzzing → hostname  
   - directory fuzzing → path  

   Mixing them creates emotional damage.

---

3. **FUZZ has to live in the right place.**  
   - dirs → `-u http://site/FUZZ`  
   - vhosts → `-u http://site/ -H "Host: FUZZ.site"`  

---

4. **ffuf recursion is a needy little diva.**  
   It wants:
   - `FUZZ` at the end  
   - reasonable threads  
   - often `-recursion-strategy greedy`  
   - not chaos (`-t 50`)  

---

5. **Lab prompts lie by omission.**  
   - wrong wordlists  
   - `.com` vs `.htb` confusion  
   - tool/version mismatches  
   - screenshots not matching reality  

---

6. **Timeout noise is not automatically a lead.**  
   Sometimes interesting.  
   Sometimes just the box being dramatic.  

---

7. **Kali does not want you raw-dogging pip installs.**  
   Use a virtual environment.  

---

8. **I was not confused  the lab was confusing.**  
   Important distinction.  

---

9. **I actually do understand this.**  
   I was usually one layer away from the correct reasoning.  

---

### Final takeaway

Web fuzzing is:
- ~30% technique  
- ~70% figuring out hidden assumptions  

And sometimes:

> fuck this room  respectfully.

---

## What I think I understand now

- Fuzzing is about **pattern recognition**, not request volume  
- Recursive fuzzing needs control and filtering  
- Filtering is essential to find real results  
- Validation with tools like `curl` is necessary  
- Efficiency > brute force  

---

## What I need to improve

- practice ffuf filtering flags (`-mc`, `-fc`, `-fs`, etc.)  
- include vhost fuzzing earlier  
- control recursion depth better  
- take breaks earlier  

---

## Plan for next session

- File Inclusion (LFI/RFI basics + practice)  

---

## Session info (optional)

- Duration: several hours  
- Energy: very low  
