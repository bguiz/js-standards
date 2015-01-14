---
title: ES5 Equality
linktitle: Equality (ES5)
date: 2015-01-14T22:41:41+11:00
tags:
  - ES5
  - Equality
menu:
  main:
    parent: es5
prev: /es5/control
next: /es5/types
notoc: true
weight: 2070
---

Strict equality

- Do not use `==` or `!=`
- Use `===` or `!==` instead
- This is because the former attempts to do type coercion before comparison, whereas the latter simply compares as-is
- The equality comparison which occurs with a type coercion is [notoriously difficult to comprehend](http://dorey.github.io/JavaScript-Equality-Table/)
  so it is best to avoid it!
