---
title: ES5 Variable Hoisting
linktitle: Hoisting
date: 2015-01-02T10:33:51+08:00
tags:
  - ES5
  - Hoisting
  - Variables
menu:
  main:
    parent: js
prev: /es5/files
next: /es5/functions
notoc: true
weight: 2030
---

Javascript is a programming language whose syntax is quite similar to
other programming languages that have a C-style syntax:
C, C++, Java, Actionscript, just to name a few.

Hoisting of variable and function definitions does not happen in these other languages,
but does happen in Javascript.
In a similar vein, these other languages have block scope as well as functions scope,
whereas Javascript only has function scope.

Given that many Javascript programmers have programmed in one or more of these other languages before,
the combination of a lack of block scope,
together with the presence hoisting,
is the cause of much frustration and programming errors when developing with Javascript.

Let us take the following example:

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

Here, a developer used to C-style syntax might assume that the output is 1.
After all, the second declaration of `var a` is only valid within the block inside the function, right?

However, what really happens here is that second declaration of `var a`
gets *hoisted* to the top of the function after the first declaration of `a`.
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

As a general guideline for coding standards,
it is best to avoid confusion where possible.

The recommended approach would be to avoid declaring variables within blocks inside of functions,
and instead declare them at the top of each function.

In addition, avoid creating unnecessary blocks.
An non-control structure block, such as the one above, should be avoided.

Sometimes blocks are necessary, such as when there is a control structure that requires it.

This function declares a variable, `var y`,
within an block, as it it is within the `if` control structure:

```javascript
function() {
	var x = 2;
	if (x < 10) {
		var y = 10;
	}
	console.log('y is', y);
}
```

A better way to write the same function,
would be to move the declaration for `var y` outside of the block,
but leave the assignment within the block.
This makes the the scope of the variables much more explicit,
and will not confuse developers with a background in another C-style language.

```javascript
function() {
	var x = 2;
	var y;
	if (x < 10) {
		y = 10;
	}
	console.log('y is', y);
}
```

tl;dr= Hoisting is great, but being explicit is better.
