---
title: ES5 Naming Conventions
linktitle: Naming
date: 2015-01-14T22:13:18+11:00
tags:
  - ES5
  - Functions
  - Variables
  - Naming
menu:
  main:
    parent: js
    identifier: naming-js
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

### Abbreviations

With the exception of temporary variables,
such as the occasional `i` and `j` that you might use as the iterator index in a for loop,
avoid abbreviating or otherwise obfuscating your variable and function names.

Spell them out in full!
After all, abbreviations are the job for a **minifier**,
which will minimise the length of all of your Javascript variables anyway!

```javascript
function a(b) {
  return b.last || bar.first;
}
```

What is `a`?
What is `b`?
If you were to look at this in three months time,
would you not wish that you had written this instead?

```javascript
function selectDefaultName(person) {
  return person.last || person.first;
}
```

In the same vein, avoid giving ambiguous names to variables:

- Instead of `pos`, call it `boxPosition`
- Instead of `num`, call it `numBoxes`

### Prefixes and Suffixes

Avoid prefixing or suffixing variables names with the types that they contain.

- Instead of `studentArray` or `studentArr`, simply use `students` instead.
- Instead of `objWallet` or `walletObj`, simply use `wallet` instead.

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
but can be beneficial to adopt across the entire project,
in addition to the ones described here.
