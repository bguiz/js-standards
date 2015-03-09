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

### Avoid Anonymous Functions

While anonymous functions might be a convenient way to save an extra few keystrokes,
it is advisable to name all but the most trivial of functions,
for these reasons:

- Self documenting code: It is a good idea to give your functions descriptive names
- Stack traces: When an error or exception is raised in the scope of the function,l
  the function's name will be displayed in the stack trace.
  If that function is anonymous, however, its name does **not** get displayed,
  even where the function was assigned to a variable.

For these reasons, we should strive to avoid using anonymous functions.
By extension of this logic, assigning an anonymous function to a variable is,
therefore, considered an antipattern.
If you find yourself doing this, simply name the function
the same as the name of the variable.

```javascript
// Avoid doing this ...
var doesFoo = function() {
  /* do foo */
};
```

```javascript
// ... and do this instead
var doesFoo = function doesFoo() {
  /* do foo */
};
```

If this seems repetitive, another alternative:


```javascript
// ... simply define a function
function doesFoo() {
  /* do foo */
}
```

The more astute might point out that the last form is less desirable,
as that will mean that the function, `doesFoo`, will pollute the global scope.

That is indeed true in the default scope, however,
if placed within an outer function,
the scope will be restricted to within just that outer function.
This gives us an excellent segue to IIFEs!

Before discussing IIFEs, however,
it is worth pointing out that IIFEs should only be used when necessary.
If the platform that you are developing for automatically restricts scope
for each file, such as with NodeJs, then there is no need.
If you are using a build tool such as RequireJs, Browserify, or Webpack,
then there is similarly no need either.
If you are not using any of the above,
writing Javascript executed in the browser,
then consider using IIFEs.

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

Hoisting was covered in detail previously,
however, it was done in terms of hoisting of variable declarations.
Hoisting of function declarations works in very much the same way.
This is most pertinent when considering **inner functions**.

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

### Pyramid of Doom

Also known as Callback Hell.
This occurs when functions next other callback functions within each other,
one time too many.
After a certain level of nesting, it becomes heard to understand
what the original intent of the code was.
It also makes the code look like it has a triangle/ pyramid on its side doing the indentation.

Ensure that the maximum level of nesting is **four** functions.

Before:

```javascript
function foo() {
  bar(123, function() {
    baz(456, function() {
      quux(789, function() {
        // complete
        // But this bad, it is nested five levels deep
      });
    });
  });
}
```

Refactor to remove some levels of nesting,
by extracting on of the nested function and placing them outside:

```javascript
function innerFoo() {
  quux(789, function() {
    // complete
    // This is much better, as this function is only nested two levels deep
  });
}

function foo() {
  bar(123, function() {
    baz(456, innerFoo);
    // ... and this function is only nested three levels deep
  });
}
```

Extracting the functions and placing them outside of their original
containing function is the most basic and straightforward means
of avoiding the pyramid of doom.
There are more advanced ways to solve this problem,
for example, using promises.
