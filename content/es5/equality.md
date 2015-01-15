---
title: ES5 Equality
linktitle: Strict Equality
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

Do not use `==` or `!=`. Use `===` or `!==` instead!

This is because the former (double equals) attempts to do type coercion before comparison, 
whereas the latter (triple equals) simply compares as-is.

The equality comparison which occurs with a type coercion is 
[notoriously difficult to comprehend](http://dorey.github.io/JavaScript-Equality-Table/)
so it is best to avoid it!

![Javascript double equals truth table. Source: http://dorey.github.io/JavaScript-Equality-Table/](/img/js-double-equals-truth-table.png)

If you cannot memorise this chart easily,
you are probably much better off using the triple equals form.
