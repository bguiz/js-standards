---
title: ES5 Functions
linktitle: Functions
date: 2015-01-02T11:15:48+08:00
tags:
  - ES5
  - Functions
menu:
  main:
    parent: js
prev: /es5/hoisting
next: /es5/naming
notoc: true
weight: 2040
---

### Anonymous and named functions

Anonymous function are functions without a name,
and named function are those with a name.
Note, however, that assigning an anonymous function to a variable
does *not* make that function a named function.
A function's name is the word in between the `function` keyword, and its parameter list.

```javascript
function namedFunction() {
	/* this is a named function, and its name is "namedFunction" */
}
```

```javascript
function () {
	/* This is an anonymous function, and it does not have a name */
}
```

```javascript
var namedFunctionReference = function () {
	/* This is an anonymous function, and it does not have a name
	   "namedFunctionReference" is *not* its name.
	*/
}
```

For anonymous functions, include a space between the `function` keyword and the parameter list:

```javascript
function (param, param2) {
	/* do stuff */
}
```

For named functions, do not include a space between the function name and the parameter list:

```javascript
function doStuff(param, param2) {
	/* do stuff */
}
```

### Trailing semicolons

For functions assigned to variables, place a `;` after the closing `}`:

```javascript
var doStuff = function (param, param2) {
	/* do stuff */
};
```

For functions that are *not* assigned to variables, do *not* place a `;` after the closing `}`:

```javascript
function doStuff(param, param2) {
	/* do stuff */
}
```

### IIFEs

Immediately invoked function expressions (IIFEs)
are anonymous functions that are surrounded by parentheses,
and called as soon as they are declared;
and thus by definition can only ever be called once:

```javascript
(function (param, param2) {
	/* do stuff */
})('param', 1);
```

Where possible, avoid using IIFEs.
As a rule of thumb, if it can be done without using an IIFE, use that other approach instead.
Legitimate uses of IIFEs would be scenarios where there is a need to contain code from "leaking" out,
and there is no way to know ahead of time what the input code will be
For example, when one is writing a tool or pre-processor that outputs generated or transformed code.

### Function hoisting

Hoistiong was covered in detail previously,
however, it was done in terms of hoisting of variable declarations.
Hoisting of function declarations works in very much the same way
as hoisting of variables.
This is most pertinent when considering inner functions.

Inner functions are functions that are declared within another function.
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

The sequence should be:

1. All variable declarations
1. All inner function declarations
1. Outer function instructions
