---
title: Python memoryview and memory-map file
date: 2017-09-22 19:19:18
categories:
- Notes

tags:
- python

---


## What is mmap?

- Map file objects directly into memory. Memory-mapped file objects behave like both strings and like file objects. Unlike normal string objects, however, these are mutable. 
- You can use mmap objects in most places where strings are expected. A memory-mapped file is created by the mmap constructor, which is different on Unix and on Windows. In either case you must provide a file descriptor for a file opened for update

## What is memoryview object ?

- Buffer protocol that provides a way to access the internal data of an object.
- Memoryview is a safe way to expose buffer protocol in python.

## Why do we need memoryview object ?
- Whenever we perform an action on an object (pass it to a function, slice it etc.) , we need to make a copy of it. 
If we have to work with a huge file, this would create unnecessary overhead. Using buffer protocol, we can give another object access to the file to user/modify it without copying it. 
- Memoryview (obj): obj must support buffer protocol.
- `memoryview()` method returns a memoryview object of the given object. 





