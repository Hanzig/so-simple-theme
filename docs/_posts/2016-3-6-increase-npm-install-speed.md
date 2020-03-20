---
layout: post
title: Increase NPM install speed
---

An interesting fact is that NPM install packages much faster when the progress bar is switched off. Note that this works with ``NPM 3.x`` as the previous versions don't have a progress bar.

### Test commands and results:

With progress bar: **51.783 total**

```
$ rm -rf node_modules
$ npm set progress=true
$ time npm install
$ npm install  19.46s user 6.26s system 49% cpu 51.783 total
```

Without progress bar: **39.855 total**

```
$ rm -rf node_modules
$ npm set progress=false
$ time npm install
$ npm install  16.29s user 5.47s system 54% cpu 39.855 total
```

While the progress bar looks pretty fancy and does give some feedback, disabling it might save you some time, especially if you have a bunch of packages to install.

Tested with ``NPM 3.10.3``
