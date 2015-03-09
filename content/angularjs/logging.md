---
title: AngularJs Logging
linktitle: Logging
date: 2015-03-09T17:25:24+11:00
tags:
  - AngularJs
menu:
  main:
    parent: angularjs

prev: /angularjs/folder-structure
next: /angularjs/credit
notoc: true
weight: 4050
---

# Logging

## `console.log` versus `$log`

  - Use `console.log` as liberally as needed during development,
    for debugging purposes or otherwise
  - However do not commit/ push any code containing `console.log` statements
    to your version control system (git/ svn, et cetera)
  - In most cases you should simply delete the `console.log`s
  - However, if you want to keep some of these log statements,
    replace their usages with `$log` instead,
    as it provides a more robust and more easily extendible logging solution.
