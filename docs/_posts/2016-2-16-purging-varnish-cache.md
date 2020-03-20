---
title: Purging Varnish cache
categories:
  - tech
tags:
  - Varnish
  - cache
---

The easiest and quickest way to purge the entire cache is simply to just restart Varnish on the server. This will purge the entire content of Varnish instead of a single (or more) object(s).

```
$ /etc/init.d/varnish restart
```
