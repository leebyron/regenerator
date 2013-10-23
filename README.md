regenerator [![Build Status](https://travis-ci.org/facebook/regenerator.png?branch=master)](https://travis-ci.org/facebook/regenerator)
===

This package implements a fully-functional source transformation that
takes the proposed syntax for generators/`yield` from future versions of
JS (ECMAScript6 or ES6, experimentally implemented in Node.js v0.11) and
spits out efficient JS-of-today (ES5) that behaves the same way.

A small runtime library (less than 1KB compressed) is required to provide the
`wrapGenerator` function. You can install it either as a CommonJS module
or as a standalone .js file, whichever you prefer.

Installation
---

From NPM:
```sh
npm install regenerator
```

From GitHub:
```sh
cd path/to/node_modules
git clone git://github.com/benjamn/regenerator.git
cd regenerator
npm install .
npm test
```

Usage
---

You have several options for using this module.

Simplest usage:
```sh
path/to/node_modules/regenerator/bin/regenerator es6.js > es5.js
```

Programmatic usage:
```js
var es5Source = require("regenerator")(es6Source);
```

AST transformation:
```js
var recast = require("recast");
var ast = recast.parse(es6Source);
ast = require("regenerator").transform(ast);
var es5Source = recast.print(ast);
```

How can you get involved?
---

The easiest way to get involved is to look for buggy examples using [the
sandbox](http://facebook.github.io/regenerator/), and when you find
something strange just click the "report a bug" link (the new issue form
will be populated automatically with the problematic code).

Alternatively, you can
[fork](https://github.com/facebook/regenerator/fork) the repository,
create some failing tests cases in [test/tests.es6.js](
https://github.com/facebook/regenerator/blob/master/test/tests.es6.js),
and send pull requests for me to fix.

If you're feeling especially brave, you are more than welcome to dive into
the transformer code and fix the bug(s) yourself, but I must warn you that
the code could really benefit from [better implementation
comments](https://github.com/facebook/regenerator/issues/7).
