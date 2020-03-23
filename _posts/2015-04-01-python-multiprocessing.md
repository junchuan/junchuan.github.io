---
title: Python Multiprocessing daemon
date: 2015-04-01 11:29:00
categories:
- Programming
- Data Science

tags:
- python
- programming
- multiprocessing


---


## Python multiprocessing daemon
By default, the main program will not exit until all the child processes have exited. Sometimes, however, we need to start some process that continue running without blocking the exit of the main program. In order to realize this , we can set the daemon mode of a process on. By default, it is off. 

One difference between `multithreading` and `multiprocessing` is the extra protection for using `__main__`. Wrapping the main part of the application in a check for `__main__` ensures that it is not run recursively in each child as the module is imported. 




