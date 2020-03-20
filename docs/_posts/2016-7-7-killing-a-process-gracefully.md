---
title: Killing a process gracefully
categories:
  - tech
tags:
  - SIGKILL
  - SIGTERM
---

There have been a lot of talk and discussions about whether to use ``kill -9 <pid>`` or not. I deducted that the 'safest' way to kill a process is to use *SIGTERM (15)* instead of *SIGKILL (9)*. *SIGKILL* technically terminates a process immediately, whereas *SIGTERM* requests for process termination and handles it smoothly. In other words, ``kill -9`` is more like pulling the plug while ``kill -15`` is shutting down in a proper way.

**SIGKILL (9)**
The *SIGKILL* signal is sent to a process to cause it to terminate immediately (kill). In contrast to *SIGTERM* and *SIGINT*, this signal cannot be caught or ignored, and the receiving process cannot perform any clean-up upon receiving this signal.

**SIGKILL (15)**
The *SIGTERM* signal is sent to a process to request its termination. Unlike the *SIGKILL* signal, it can be caught and interpreted or ignored by the process. This allows the process to perform nice termination releasing resources and saving state if appropriate. *SIGINT* is nearly identical to *SIGTERM*.

So, if I would have to ``kill`` a *mongod* process, for instance, I would try *SIGTERM* first, and use *SIGKILL* if and only if *SIGTERM* fails, last resort.

Example:

```
$ ps ax | grep mongod // Get the process id (pid)
$ kill -15 pid // kill the mongod process with SIGTERM
```

Some more interesting information on:

* <a href="http://unix.stackexchange.com/questions/8916/when-should-i-not-kill-9-a-process" target="_blank">http://unix.stackexchange.com/questions/8916/when-should-i-not-kill-9-a-process</a>

* <a href="https://en.wikipedia.org/wiki/Unix_signal#List_of_signals" target="_blank">https://en.wikipedia.org/wiki/Unix_signal#List_of_signals</a>
