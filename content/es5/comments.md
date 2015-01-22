---
title: ES5 Comments
linktitle: Comments (JS)
identifier: comments-js
date: 2014-12-19T21:36:34+11:00
tags:
  - ES5
  - Comments
  - JSDoc
menu:
  main:
    parent: js
prev: /intro
next: /es5/files
notoc: true
weight: 2010
---

Comment your code generously.
As a rule of thumb, you should *not* have a comment for every line of code.
Rather you should have a comment per function,
where the function is non-trivial.

Examples:

**Do not** comment every line,
especially when it is obvious what is happening.

```javascript
//declare a new variable called x, and assign its initial value
var x = 0;
//increment x by one
++x;
```

**Do not** comment trivial functions, such as getters and setters with no special logic.

```javascript
var x = 0;

//gets value of x
function getX() {
	return x;
}
```

**Do** comment complex functions.
As a rule of thumb,
if it is not immediately obvious what the function does based on its name,
or if it has special implementation details that cannot be expected unless inspecting the function body,
or any other complicating factor,
that function needs a comment

When a function is commented, adhere to a standard format throughout the code base.
The standard should be decided based on the choice of documentation pre-processor chosen.
If no documentation pre-processor has been chosen,
default to adhering to the format expeected by
[JSDoc](http://usejsdoc.org/about-getting-started.html)

```javascript
/**
 * Model class representing a Person
 * @constructor
 * @param {string} first - first name
 * @param {string} last - last name
 **/
function Person(first, last) { /* implementation goes here */ }
```

**Do** comment complex code snippets

```javascript
//allows us to use a 1D array to store a 2D grid of data
return arr[y * width + x];
```

**Do** use multiline comments instead of single line comments,
for comments that are three lines or more.

```javascript
/*
 * This comment is quite long,
 * and it spans multiple lines,
 * so we use a different type of syntax
 */

 // This is a short comment, just one line
 ```

Note that subtle difference such as the number of `*`s
is significant.
JSDoc interpret multiline comments that begin with exactly two `*`s
as a commnet that should be parsed and added to the documentation,
and ignores any other multiline commnents

**Avoid** checking in commented out lines of code.

Committing or checking in commented out lines of code
into version control systems is OK.
However, if doing so, add a comment with `TODO` or `NOTE`
to indicate what this is being left like this.

```javascript
//TODO disabling zeroing out of array due to ___
// revisit once resolved
//for (var x = 0; x < t; ++x) {
//	arr[x] = 0;
//}
```

Commenting out by means of an impossible conditional branch
is also likewise OK to commit or check in.
However, they should also be commented out likewise.

```javascript
//TODO disabling zeroing out of array due to ___
// revisit once resolved
if (false) {
	for (var x = 0; x < t; ++x) {
		arr[x] = 0;
	}
}
```

Note that these are both *undesirable*,
and should be avoided where possible.
However, if it happens that leaving in the disabled or commented out code
improves the ability of the next developer to comprehend what is going on
or the original intent of the code,
then these are permissible.
