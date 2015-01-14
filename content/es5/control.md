---
title: ES5 Control Structures
linktitle: Control (ES5)
date: 2015-01-14T22:25:16+11:00
tags:
  - ES5
  - If
  - For
  - While
  - Do
  - Switch
menu:
  main:
    parent: es5
prev: /es5/naming
next: /es5/equality
notoc: true
weight: 2060
---

- The following keywords control the flow of execution in a program:
  `if`, `for`, `while`, `do`, `switch`
- The code block which follows these keywords (sometimes with a set of instructions enclosed in parentheses in between)
  must be surrounded with `{` and `}`
- For example, this `if` statement is **bad**:

```javascript
if (x > y)
	++x;
```

- ... and this `if` statement fixes the problem above:

```javascript
if (x > y) {
	++x;
}
```

Switch statements

- The block of the switch statement typically contains several `case`s and one `default`,
  each of which should contain a group of statements to execute.
- Each of these groups of statements must either `break`, `throw`, or `return` in order to avoid unintentionally falling through to the next group of statements 
