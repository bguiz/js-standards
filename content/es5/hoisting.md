---
title: ES5 Variable Hoisting
linktitle: Hoisting (ES5)
date: 2015-01-02T10:33:51+08:00
tags:
  - ES5
  - Hoisting
  - Variables
menu:
  main:
    parent: es5
prev: /es5/files
next: /es5/functions
notoc: true
weight: 2030
---

- Javascript has function scope, but no block scope
- In conjunction with variable hoisting and syntax similar to other languages with C-style syntax, this can lead to much developer confusion

```javascript
function () {
	var a = 1;
	{
		var a = 2;
	}
	console.log('a is', a);
}
//actual output: a is 2
```

- In the above example, a developer used to C-style syntax might assume that the output is 1.
However, what really happens here is that `var a` within the block inside the function
gets hoisted to the top of the function after the first declaration of `a`.
Essentially `a` is being declared twice, and assigned to twice, like so:

```javascript
function () {
	var a = 1;
	var a;
	{
		a = 2;
	}
	console.log('a is', a);
}
```

- Thus, avoid declaring variables within blocks inside of functions
- Preferably, declare all variables needed within a function at the top of the function,
and simply assign their values later on within the function
