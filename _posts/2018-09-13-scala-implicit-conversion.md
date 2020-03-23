---
title: Scala implicit conversion
date: 2018-09-13 19:29:00
categories:
- Programming

tags:
- scala



---

## Implicit conversion in scala
`implicit` conversion is often helpful for working with two bodies of software that were developed without each other in mind.  
`implicit` conversion reduces the number of explicit conversions that are needed from one type to another. 
`implicit definitions` can be inserted into a program by a compiler in order to fix any of its type error.  

Rules for implicits:
- Only definitions that are marked implicit are available to the compiler.
- Scala compiler will only consider `implicit conversions` that are in scope. Therefore, you have to make `implicit conversion` in scope as a single identifier. *Exception: the compiler will also look for implicit definitions in the companion object of the source or expected target types*. 
- Only one implicit is tried for a variable. 
- Compiler will not change code that already works.Thus, you can always replace implicit identifiers by explicit ones.
- Conversion of the receiver: adapt the object on which a method is invoked. 




