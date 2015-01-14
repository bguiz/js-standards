---
title: ES5 Functions
linktitle: Functions (ES5)
date: 2015-01-02T11:15:48+08:00
tags:
  - ES5
  - Functions
menu:
  main:
    parent: es5
prev: /es5/hoisting
next: /es5/naming
notoc: true
weight: 2040
---

- For anonymous functions, include a space between the `function` keyword and the parameter list:

```javascript
function (param, param2) {
	/* do stuff */
}
```

- For named functions, do not include a space between the function name and the parameter list:

```javascript
function doStuff(param, param2) {
	/* do stuff */
}
```

- For functions assigned to variables, place a `;` after the closing `}`:

```javascript
var doStuff = function (param, param2) {
	/* do stuff */
};
```

- For functions that are *not* assigned to variables, do *not* place a `;` after the closing `}`:

```javascript
function doStuff(param, param2) {
	/* do stuff */
}
```

- Immediately invoked function expressions (IIFEs) are anonymous functions that are surrounded by parentheses,
and called as soon as they are declared; and thus by definition can only ever be called once:

```javascript
(function (param, param2) {
	/* do stuff */
})('param', 1);
```

- Where possible avoid using IIFEs
	- As a rule of thumb, if it can be done without using an IIFE, use that other approach instead
	- Legitimate uses of IIFEs would be scenarios where there is a need to contain code from "leaking" out, and there is no way to know ahead of time what the input code will be,
	  such as when one is writing a tool or pre-processor that outputs generated or transformed code.

- Inner functions are functions that are declared within another function.
  In this scenario, variables within the scope of the outer function
  are made available for use within the inner function by means of closure.
  Thus, following the guidelines for variable declarations at the top of each function,
  inner functions should always be declared at the top of each function too,
  but immediately below these variable declarations for clarity.

```javascript
var outerFunction = function () {
	var variableAvailableThroughClosure = 1;

	var innerFunction = function () {
		++variableAvailableThroughClosure;
	}

	innerFunction();
	console.log('variableAvailableThroughClosure is', variableAvailableThroughClosure);
};
```
