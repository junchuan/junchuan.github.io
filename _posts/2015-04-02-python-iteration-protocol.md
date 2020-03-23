---
title: Python Iteration Protocol
date: 2015-04-02 11:29:00
categories:
- Programming

tags:
- python
- programming


---


## Python Iteration Protocol
In order for an object to be iterable, it must implement `__iter__()` method. This method will automatically make the class object an `iterator`. You know what an iterator should do? Obviously, you need to implement a `next()` method in order for this iterator to function normally. 
But when you run `iter()` on an object, it will only check whether the parameter you passed in is iterable or not, i.e., whether it has `__iter__()` method implemented or not. So, even if you have not implemented `next()` method, `iter()` will still run. 