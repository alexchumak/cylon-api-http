# Cylon.js API plugin for HTTP

Cylon.js (http://cylonjs.com) is a JavaScript framework for robotics, physical computing, and the Internet of Things using Node.js

API plugins are separate from the Cylon.js main module, to allow for greater modularization of Cylon robots.

This repository contains the Cylon API plugin for HTTP.

For more information about Cylon, check out the repo at https://github.com/hybridgroup/cylon

[![Build Status](https://travis-ci.org/hybridgroup/cylon-api-socketio.svg)](https://travis-ci.org/hybridgroup/cylon-api-socketio)
[![Code Climate](https://codeclimate.com/github/hybridgroup/cylon-api-socketio/badges/gpa.svg)](https://codeclimate.com/github/hybridgroup/cylon-api-socketio)
[![Test Coverage](https://codeclimate.com/github/hybridgroup/cylon-api-socketio/badges/coverage.svg)](https://codeclimate.com/github/hybridgroup/cylon-api-socketio)

## How To Install

    $ npm install cylon cylon-api-http

## How To Use

With both of these modules installed, you can make your robots accessible over HTTP:

```javascript
"use strict";

var Cylon = require("cylon");

Cylon.api("http", {
  ssl: false // serve unsecured, over HTTP

  // optional configuration here.
  // for details see 'Configuration' section.
});

Cylon.robot({
  name: "Maria",

  connections: {
    arduino: { adaptor: 'firmata', port: '/dev/ttyACM0' }
  },

  devices: {
    led: { driver: 'led', pin: 13 }
  },

  work: function() {
    // we'll interact with this robot through the API
  }
}).start();
```

## How To Connect

Once you've got a Cylon instance with the API configured and running, you can use cURL to test it out:

      $ curl http://127.0.0.1:4000/api/robots/Maria
      { "robot": { "name": "Maria" /* ... */ } }

## Documentation

We're busy adding documentation to [cylonjs.com](http://cylonjs.com). Please check there as we continue to work on Cylon.js.

Thank you!

## Contributing

* All patches must be provided under the Apache 2.0 License
* Please use the -s option in git to "sign off" that the commit is your work and you are providing it under the Apache 2.0 License
* Submit a Github Pull Request to the appropriate branch and ideally discuss the changes with us in IRC.
* We will look at the patch, test it out, and give you feedback.
* Avoid doing minor whitespace changes, renamings, etc. along with merged content. These will be done by the maintainers from time to time but they can complicate merges and should be done seperately.
* Take care to maintain the existing coding style.
* Add unit tests for any new or changed functionality & lint and test your code using `make test` and `make lint`.
* All pull requests should be "fast forward"
  * If there are commits after yours use “git rebase -i <new_head_branch>”
  * If you have local changes you may need to use “git stash”
  * For git help see [progit](http://git-scm.com/book) which is an awesome (and free) book on git

## Release History

0.1.1 - Correct command issues, re-organize internals.

0.1.0 - Initial release

## License

Copyright (c) 2014-2015 The Hybrid Group. Licensed under the Apache 2.0 license.
