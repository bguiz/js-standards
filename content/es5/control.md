---
title: ES5 Control Structures
linktitle: Control
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
    parent: js
prev: /es5/naming
next: /es5/equality
notoc: true
weight: 2060
---

### Blocks

The following keywords control the flow of execution in a program:
`if`, `for`, `while`, `do`, `switch`

The code block which follows these keywords
(sometimes with a set of instructions enclosed in parentheses in between)
must be surrounded with `{` and `}`.

For example, this `if` statement is **bad**:

```javascript
if (x > y)
	++x;
```
... and this `if` statement is much better:

```javascript
if (x > y) {
	++x;
}
```

### Switch statements

The block of the switch statement typically contains several `case`s and one `default`,
each of which should contain a group of statements to execute.
Each of these groups of statements must either `break`, `throw`, or `return` in order to avoid unintentionally falling through to the next group of statements.

```javascript
switch (myVar) {
case 2:
	console.log('Exiting function because myVar is two');
	return;
case 1:
	console.log('myVar is one');
	break;
case 0:
	throw 'myVar has an illegal value';
default:
	console.log('Nothing special about myVar');
}
```
The fopllwoing example illustrates what *not* to do in a switch statement:

```javscript
switch (myVar) {
case 2:
	console.log('myVar is two');
case 1:
	console.log('myVar is one');
}
```

When `myVar` is `1`, it works as expected.
However, when `myVar` is `2`, the output is:

```
myVar is two
myVar is one
```

What happened here was the `case 2` was entered correctly,
but after executing its only statement,
there was no `break` statement,
and therefore, the execution *fell through* to the next case.
Avoid this!
