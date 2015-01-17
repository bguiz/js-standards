---
title: ES5 Linting
linktitle: Linting
date: 2015-01-15T17:20:09+11:00
tags:
  - ES5
  - Lint
  - JsHint
menu:
  main:
    parent: es5
prev: /es5/types
next: /es5/comments
notoc: true
weight: 2090
---

### JsHint

While reading this set of ECMAScript 5 coding standards is a step in the right direction,
it does not get you all of the way.
Some rules are easier to remember and stick to than others.
It is best to have a tool that programmatically checks your sources code for
violations of coding standards as you develop,
and highlights them within your IDE,
and gives you detailed output as part of your build process.

There are several tools out there that do this,
and [JsHint](http://jshint.com/) is one of the more popular ones.
JsHint is most commonly used as a Javascript preprocessor as part of build tools,
and most IDEs popular with web developers

### `.jshintrc`

It is definitely worth reviewing the
[list of configuration options](http://jshint.com/docs/options/)
available on JsHint.
Looking at which rules are enabled by default (and can be turned off),
and which rules are disabled by default (and can be turned on),
gives you an good idea of how extremely relaxed the Javascript language specification can be;
and thus the importance of using something like JsHint.

These options are configurable using a file named `.jshintrc`,
which usually sits at the root directory of a project.

A sample `.jshintrc` file which conforms to the rules
that have been described in the ES5 specifications will be made available soon.

[ES5 `.jshintrc`](/downloads/es5/.jshintrc)

Essentially all the default JsHint options are used,
with a few exceptions.
