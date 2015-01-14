---
title: ES5 Naming Conventions
linktitle: Naming (ES5)
date: 2015-01-14T22:13:18+11:00
tags:
  - ES5
  - Functions
  - Variables
  - Naming
menu:
  main:
    parent: es5
prev: /es5/functions
next: /es5/control
notoc: true
weight: 2050
---

- Use **camelCase** when naming variables and functions
- When a function is intended to be called as a constructor function (i.e. with the `new` keyword),
  use the **PascalCase** instead
- Javascript is quite relaxed in which characters it allows in legal variable or function names,
  use instead what would be normal variable naming conventions other C-style syntax languages:
  	- First character can be an alphabet (upper case or lower case)
  	- Second and subsequent characters can be a digit or an alphabet (upper case or lower case)
  	- Avoid using `_`, `$`, `\`
  	- Avoid any characters with ASCII code over 127
  	- Avoid all Unicode characters
