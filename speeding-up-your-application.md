---
description: Coming Soon
---

# Speeding Up Your Application

Suggestion

First of all: do some profiling on the code: which part is running the slowest. Is it compute? Is it Memory? Is it I/O? Which part in the code?

* Do you need faster CPU's, more memory? Change that in Sid and see if that helps
* Run multiple interactive sessions at once
* Run in on Sid and come back the next day. It will run in the background even if you shut down yor laptop.
* Sometime CSV file will slow down the performance and using and changing to for example sqlite database can help a lot
* Parallize the jobs to make use of more cores

