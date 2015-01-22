---
title: AngularJs Comments
linktitle: Comments
date: 2015-01-21T10:34:04+11:00
tags:
  - AngularJs
menu:
  main:
    parent: angularjs

prev: /angularjs/animations
next: /angularjs/js-hint
notoc: true
weight: 4020
---


## Comments

### jsDoc
###### [Style [Y220](#style-y220)]

  - If planning to produce documentation, use [`jsDoc`](http://usejsdoc.org/) syntax to document function names, description, params and returns. Use `@namespace` and `@memberOf` to match your app structure.

  *Why?*: You can generate (and regenerate) documentation from your code, instead of writing it from scratch.

  *Why?*: Provides consistency using a common industry tool.

  ```javascript
  /**
   * Logger Factory
   * @namespace Factories
   */
  (function() {
    angular
        .module('app')
        .factory('logger', logger);

    /**
     * @namespace Logger
     * @desc Application wide logger
     * @memberOf Factories
     */
    function logger($log) {
        var service = {
           logError: logError
        };
        return service;

        ////////////

        /**
         * @name logError
         * @desc Logs errors
         * @param {String} msg Message to log
         * @returns {String}
         * @memberOf Factories.Logger
         */
        function logError(msg) {
            var loggedMsg = 'Error: ' + msg;
            $log.error(loggedMsg);
            return loggedMsg;
        };
    }
  })();
  ```



