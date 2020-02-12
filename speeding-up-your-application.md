---
description: Coming Soon
---

# Speeding Up Your Application

Suggestions

First of all: do some profiling on the code: which part is running the slowest. Is it compute? Is it memory? Is it I/O? Which part in the code?

* Run in on Sid and come back the next day. It will run in the background even if you shut down your laptop.
* Sometime CSV files will slow down the performance and using and changing to, for example, an [sqlite](https://www.sqlite.org) database can help a lot.
* Parallelize the jobs to make use of more CPU cores.

