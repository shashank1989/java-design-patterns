---
layout: pattern
title: Half-Sync/Half-Async
folder: half-sync-half-async
permalink: /patterns/half-sync-half-async/
categories: concurrency
tags: pattern_tag
---

**Intent:** The Half-Sync/Half-Async pattern decouples synchronous I/O from
asynchronous I/O in a system to simplify concurrent programming effort without
degrading execution efficiency.

![Half-Sync/Half-Async class diagram](./half-sync-half-async/etc/half-sync-half-async.png)

**Applicability:** Use Half-Sync/Half-Async pattern when

* a system possesses following characteristics:
  * the system must perform tasks in response to external events that occur asynchronously, like hardware interrupts in OS
  * it is inefficient to dedicate separate thread of control to perform synchronous I/O for each external source of event
  * the higher level tasks in the system can be simplified significantly if I/O is performed synchronously.
* one or more tasks in a system must run in a single thread of control, while other tasks may benefit from multi-threading.

**Real world examples:**

* [BSD Unix networking subsystem](http://www.cs.wustl.edu/~schmidt/PDF/PLoP-95.pdf)
* [Real Time CORBA](http://www.omg.org/news/meetings/workshops/presentations/realtime2001/4-3_Pyarali_thread-pool.pdf)
* [Android AsyncTask framework](http://developer.android.com/reference/android/os/AsyncTask.html)
