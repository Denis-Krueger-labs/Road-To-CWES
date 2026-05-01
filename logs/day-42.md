---
layout: log
title: "Day 42 - Exploit Development & Buffer Overflow Fundamentals"
date: 2026-04-29
topics:
  - Exploit Development
  - Buffer Overflows
  - CPU Architecture
  - GDB
summary: "Started exploit development fundamentals, focusing on CPU architecture, memory layout, and stack-based buffer overflows with hands-on GDB usage."
status: complete
---

# Day 42 - Exploit Development & Buffer Overflow Fundamentals

## What I studied today

Today was the start of **exploit development**, which feels like stepping from “breaking web apps” into “breaking actual programs.”

Main focus areas:

- What exploits actually are and how they are classified
- CPU architecture basics (Von-Neumann model)
- Memory layout of programs
- Stack-based buffer overflows
- CPU registers and stack frames
- Using **GDB** to inspect binaries and memory

---

## Summary of concepts

- An **exploit** is code that abuses a vulnerability to control program behavior
- Exploits can be:
  - Local (privilege escalation)
  - Remote (network-based)
  - DoS
  - Web-based
- **0-day vs N-day** is about whether the vulnerability is publicly known

---

### Memory & execution

- Programs are loaded into memory sections:
  - `.text` → code
  - `.data` → initialized variables
  - `.bss` → uninitialized variables
  - **Heap** → dynamic memory (grows up)
  - **Stack** → function calls (grows down)

- The CPU runs in a loop:
```

Fetch → Decode → Execute

````

---

### Buffer overflow core idea

A buffer overflow happens when:

```c
char buffer[1024];
strcpy(buffer, input);
````

Input > 1024 bytes → overflow into adjacent memory

This can overwrite:

* local variables
* saved registers
* **return address (most important)**

If you control the return address → you control execution flow.

---

### CPU registers (important for exploitation)

Key registers:

* `EIP / RIP` → next instruction (TARGET)
* `ESP / RSP` → top of stack
* `EBP / RBP` → base of stack frame

Controlling **EIP/RIP = control of execution**

---

### Stack frames

Each function call creates a stack frame:

```
[ local variables ]
[ saved EBP       ]
[ return address  ]  ← target for overflow
```

Function lifecycle:

**Prologue**

```
push ebp
mov ebp, esp
sub esp, ...
```

**Epilogue**

```
leave
ret
```

`ret` jumps to the saved return address → which can be overwritten.

---

### Endianness

x86 uses **little-endian**:

```
0xAABBCCDD → DD CC BB AA
```

Important when writing addresses in exploits.

---

### Protections

Modern protections:

* **DEP / NX** → prevents execution on stack
* **ASLR** → randomizes memory addresses

Bypasses:

* ROP (Return-Oriented Programming)
* Info leaks to defeat ASLR

---

### GDB

Used for:

* inspecting memory
* analyzing registers
* disassembling functions
* tracing execution

Also learned:

* Intel vs AT&T syntax (just reversed operand order… still annoying)

---

## What I actually did (important)

* Used **GDB** to inspect memory and locate specific addresses
* Started understanding how stack layout looks in a real binary
* Began connecting theory (stack frames, registers) to actual debugging output

---

## What went well

* Concepts started to *click together* (finally)
* Stack + registers + return address now feels like a system, not random theory
* GDB usage felt less intimidating than expected
* I didn’t get stuck on syntax differences for too long

---

## What was confusing

* Keeping track of stack direction (up vs down) still messes with my brain
* Translating C → assembly → memory layout is not intuitive yet
* AT&T vs Intel syntax is unnecessarily annoying
* Understanding how protections (DEP/ASLR) actually affect real exploits

---

## Mistakes / friction

* Had to reread stack frame explanations multiple times
* Initially treated registers as abstract instead of *actual control points*
* Got slightly lost when following execution flow in GDB
* Mixed up byte order before remembering little-endian

---

## What I think I understand now

* Exploit dev is about controlling execution flow, not just finding bugs
* The **return address on the stack is the main target**
* Registers (especially EIP/RIP) are the key to control
* Memory layout matters A LOT
* Buffer overflows are basically:

  ```
  overwrite memory → control return → redirect execution
  ```

---

## What I need to improve

* Practice reading stack layouts faster
* Get comfortable navigating GDB without hesitation
* Understand assembly instructions more fluently
* Practice writing and visualizing memory layouts
* Learn how protections actually change exploitation strategy

---

## Plan for next session

* Continue buffer overflow lab
* Try to overwrite return address intentionally
* Practice using GDB step-by-step during exploitation

---

## Session info (optional)

* Duration: 3h
* Energy: Medium
