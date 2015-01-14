---
title: ES5 Files
linktitle: Files (ES5)
date: 2014-12-21T11:38:22+11:00
tags:
  - ES5
  - Files
menu:
  main:
    parent: es5
prev: /es5/comments
next: /es5/hoisting
notoc: true
weight: 2020
---

**Do** name an include Javascript files in a standard way.

Javascript files should be served with the file name extension `.js`,
and should be included in a HTML using a script tag.

```html
<script src="myfile.js"></script>
```

The `<script>` tags should be placed *not* within the `<head>` tag,
but rather within the `<body>` tag.
They should also be the last tags within the `<body>` tag.
This is because browsers load script tags synchronously,
and makes the HTML document appear to load more slowly to the end user.

**Do not** place any Javascript inline within HTML.

`<script>` tags containing Javascript are a bad idea,
as it fails to separate the concerns of behaviour and content.
This in a similar vein to why we should place CSS in a separate
file instead of inline within DOM elements.

Another place that Javascript is commonly found in HTML
is within `on*` attribute tags on DOM elements,
for example:

```html
<div onclick="myclicklistener();">Click Me</div>
```

Instead of doing this, use pure Javascript to bind to events on the DOM element.

```html
<div id="clickme">Click Me</div>
```

```javascript
document.getElementById('clickme').addEventListener('click', myclicklistener);
```

**Do not** make assumptions about the order in which the DOM is rendered
and the Javascript execution.

Instead, use the `DOMContentLoaded` event:

```javascript
document.addEventListener("DOMContentLoaded", function(event) { 
  //initialise stuff
});
```

or jQuery:

```javascript
jQuery(document).ready(function(event) { 
  //initialise stuff
});
```

**Do** use a standard line length and indentation format

Set your text editor to replace `tab` characters with two space characters,
and use this for indentation.

Additionally set your text editor to draw a line as a visual indicator
to show where the 120 character column is.
This visual indicator will help you to avoid lines that are way too long.

Many others will recommend that 80 character columns should be used here,
however, that is a little outdated with current day screen sizes and resolutions,
and is unnecesarily restrictive.

Another reason for placing a restriction on the maximum line length,
is that it is a great indicator of pyramid of doom -
when there is an overly high level of nesting of callback functions.
Extract the innermost callback functions to somewhere outside.
Better yet, use promises.

