[![view on npm](http://img.shields.io/npm/v/handbrake-js.svg)](https://www.npmjs.org/package/handbrake-js)
![npm module downloads per month](http://img.shields.io/npm/dm/handbrake-js.svg)
[![Build Status](https://travis-ci.org/75lb/handbrake-js.svg?branch=master)](https://travis-ci.org/75lb/handbrake-js)
[![Dependency Status](https://david-dm.org/75lb/handbrake-js.svg)](https://david-dm.org/75lb/handbrake-js)
![Analytics](https://ga-beacon.appspot.com/UA-27725889-6/handbrake-js/README.md?pixel)

handbrake-js
============
Handbrake-js is a [node.js](http://nodejs.org) module wrapping [Handbrake](http://handbrake.fr) (v0.9.9) with a Javascript API, documented below. It's primary purpose is to bring video transcoding to your app.

Tested on Mac OSX, Ubuntu 14, Windows XP, Windows 8.1.

Installation
============
System Requirements
-------------------
Just [node.js](http://nodejs.org). Every else is installed automatically.

*Mac / Linux users may need to run either of the following commands with `sudo`*.

As a library 
------------
Move into your project directory then run: 
```sh
$ npm install handbrake-js --save
```

As a command-line app
---------------------
From any directory run the following:
```sh
$ npm install -g handbrake-js
```

Now, you can call `handbrake` as you would HandbrakeCLI, using all the usual [options](https://trac.handbrake.fr/wiki/CLIGuide). This command will transcode an AVI to the more universal H.264 (mp4):
```sh
$ handbrake --input "some episode.avi" --output "some episode.mp4" --preset Normal
```

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

API Documentation
=================

handbrakeJs.spawn(options)
--------------------------

##spawn
Spawns a HandbrakeCLI process with the supplied [options](https://trac.handbrake.fr/wiki/CLIGuide), returning an instance of `Handbrake` which you can monitor for events.

All errors are delivered via the "error" event.

###Parameters
 {Object,Array} - [Options](https://trac.handbrake.fr/wiki/CLIGuide) to pass directly to HandbrakeCLI  
mocks {Object} - Optional mock objects, for testing *optional*  

**Returns** Handbrake A handle on which you can listen for events on the Handbrake process.

###Example
```js
var handbrakeJs = require("handbrake-js");

handbrakeJs.spawn(options)
    .on("error", console.error)
    .on("output", console.log);
```


