---
title: ES5 Naming Conventions
linktitle: Naming (JS)
identifier: naming-js
date: 2015-01-14T22:13:18+11:00
tags:
  - ES5
  - Functions
  - Variables
  - Naming
menu:
  main:
    parent: js
prev: /es5/functions
next: /es5/control
notoc: true
weight: 2050
---

### Case

Use **camelCase** when naming variables and functions

When a function is intended to be called as a constructor function (i.e. with the `new` keyword),
use the **PascalCase** instead.
Pascal case is simply camel case, except that the first letter is capitalised.

### Legal characters

Javascript is quite relaxed in which characters it allows in legal variable or function names,
use instead what would be normal variable naming conventions other C-style syntax languages:

- First character can be an alphabet (upper case or lower case)
- Second and subsequent characters can be a digit or an alphabet (upper case or lower case)
- Avoid using `_`, `$`, `\`
- Avoid any characters with an ASCII code of over 127
- Avoid all Unicode characters

### Project level consistency

There are a number of other naming conventions that you may choose to adopt,
that may not be applicable across different projects.
However, it always makes sense to ensure consistency within an entire project.

For example, because Javascript does not natively support the concept of private variables,
or support the concept of constants,
many developers adopt conventions such as:

- Private variables' names must be preceded with `_`
- Constants' names must be is **ALL_CAPS**

These additional naming conventions are not necessary,
but can be beneficial to adopt acorss the entire project,
in addition to the ones described here.
