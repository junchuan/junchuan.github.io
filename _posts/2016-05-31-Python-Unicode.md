---
title: Notes on Python 2.x Unicode
date: 2016-05-31 11:16:00
categories:
- Programming
tags:
- programming
- python

---


The difference between `Unicode string` and `byte string` is that `Unicode string` is an abstract design, whereas `byte string` is the abstract design’s realization in memory or on disk.  

Every character has a code point according to the Unicode standard. However, if you want to write a `Unicode string` onto disk, you have to encode it into bytes, which is the only thing that can be serialized onto disk. 

When you open a file : 
```
with open(fp) as f:
	f.write(...)
```
If the thing that you are trying to write into the file on the disk has already been encoded (e.g., utf-8, latin), then the write method will just write the byte sequence onto disk. However, if the thing has not been encoded yet, then write method will use the system’s default encoding (i.e., ascii). 

When you are using `codec` package, it will allow you to specify an encoding when opening a file. Thus, you can just pass in `Unicode string` without encoding. The `write` method will encode the `Unicode string` into byte sequence first before serializing it onto disk. 






