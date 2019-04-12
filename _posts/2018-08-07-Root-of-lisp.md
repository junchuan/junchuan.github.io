---
title: Root of Lisp
date: 2018-08-07 13:29:08
categories:
- Notes
tags:
- programming

---


[John McCarthy](https://en.wikipedia.org/wiki/John_McCarthy_(computer_scientist)) shows that given a few operators and notation for functions, you can build a whole programming language. 


## Lisp Model of Computation

### expression: 
- an `atom` , which is a sequence of letters (e.g., foo)
- a list of zero or more expressions, separated by whitespace and enclosed by parenthesis.

### Seven primitive operators:
- `(quote x)` returns x. For example, `'x`, `(quote a)`,`(quote (a b c))` 
	- by quoting a list, we prevent it from being evaluated
- `(atom x)` returns the atoms `t` if the value of x is an atom or the empty list.
	- `(atom 'x) -> t`  
	- `(atom '(a b c)) -> ()` 
	- `(atom '())-> t`
- `(eq x y)` returns `t` if the values of `x` and `y` are the same atom or both the empty list
	- `(eq 'a 'a) -> t`
	- `(eq 'a 'b)-> ()`
- `(car x)`  returns `x`’s first element
- `(cdr x)` returns everything after the first element
- `(cons x y)` returns a list containing the value `x` followed by the elements of the value of `y`
- `(cond (p1 e1) …(pn en)`. The `p` expressions are evaluated in order until one returns `t`. When one is found, the corresponding `e` expression is returned as the value of the whole `cond` expression.


### Denoting function 
- `(lambda (p1...pn) e)`. `p1, ...pn` are atoms(*parameters*) and `e` is an expression 
- function call: `((lambda (p1...pn) e) a1...an)` 
	- Each expression `ai` is evaluated. Then `e` is evaluated. During the evaluation of `e`, the value of any occurrence of one of the `pi` is the corresponding `ai` in the most recent function call
	- parameters can be used as operators in expressions as well as arguments. 

```
	((lambda (f) (f '(b c))) '(lambda (x) (cons 'a x))) 
	output:(a b c)

```

- `(label f (lambda (p1...pn) e))` denotes a function behaves like `(lambda (p1...pn) e)`
- `(defun null. (x) (eq x ‘()))`
- `(defun and. (x y) (cond (x (cond ( y ‘t) (‘t ‘()))) (‘t ‘())))`

Using just  `quote`, `atom`, `eq`, `car`, `cdr`, `cons` , `cond`, we can define a function `eval`, that actually implements our language, and then using that we can define any additional functions we want. This is a very elegant model of computation. 
