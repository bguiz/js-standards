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

prev: /angularjs/startup-logic
next: /angularjs/testing
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
    login-form-directive.js
    login-form-directive.spec.js
    login-form-directive.html
    login-service.js
    login-service.spec.js
    login-view.html
  todo/
    todo-item-directive.js
    todo-item-directive.html
    todo-item-directive.spec.js
    todo-controller.js
    todo-controller.spec.js
    todo-view.html
  app.js
  index.html
```

Organise the source code of your AngularJs project such that they are organised by feature
rather than file type.

- Do not create folders named `controllers`, `directives`, et cetera.
  - You can tell what type of file it is by looking at the suffix and extension of the file names
- Instead create folders with the intent to group features
  - When a feature gets too large or complex, requiring many different files,
    simply create subfolders for each feature.
  - For example, if the login feature, which previously has one directive for `form`,
    now wants to add a new directive for displaying `error`s,
    simply create `form` and `error` subfolders within the `login` folder,
    and move the files accordingly.

```
my-project/
  login/
    form/
      login-form-directive.js
      login-form-directive.spec.js
      login-form-directive.html
    error/
      login-error-directive.js
      login-error-directive.spec.js
      login-error-directive.html
    login-service.js
    login-service.spec.js
    login-view.html
  todo/
    todo-item-directive.js
    todo-item-directive.html
    todo-item-directive.spec.js
    todo-controller.js
    todo-controller.spec.js
    todo-view.html
  app.js
  index.html
```

The intent here is that files which need each other and are closely related are
the most likely to be colocated with the same folder or in sibling folders.

If files were organised into folders determined by their type instead,
quite often you find that files need to reference each other by longer paths,
and as a developer, you will often find yourself thinking about
parallel/ equivalent folder paths.
