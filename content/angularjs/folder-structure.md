---
title: AngularJs Folder Structure
linktitle: Angular Folder Structure
date: 2015-01-21T10:34:04+11:00
tags:
  - AngularJs
  - Folder
  - Project
menu:
  main:
    parent: angularjs

# prev: /angularjs/startup-logic
# next: /angularjs/testing
notoc: true
weight: 4031
---

## Feature Centric

Arrange the project folders such that the top level directories are the names of each feature.
The directory for each feature should contain sub-directories for:

- directive
- controller
- view
- service
- factory

```
my-project/
  login/
    (...)
  todo/
    directive/
      todo-item-directive.js
      todo-item-directive.html
      todo-item-directive.spec.js
    controller/
      todo-controller.js
      todo-controller.spec.js
    view/
      todo-page.html
    service/
      (...)
    factory/
      (...)
  app.js
  index.html
```

Take a look at [this article](https://medium.com/opinionated-angularjs/scalable-code-organization-in-angularjs-9f01b594bf06),
which explains this concept in greater detail.
