---
title: Notes on Javascript
date: 2015-05-30 09:16:00
categories:
- Notes

tags:
- programming
- javascript
---

## undefined 
- `undefined` variable will be interpreted as `NaN` when used as number
- Javascript doesn’t have block statement scope. It will be local to the code that the block resides within. 
- In javascript, if you refer to variable that has not been declared yet,  but it will return `undefined`. Thus, all `var` statements in a function should be placed as near to the top of the function as possible.
- Global variables are properties of global objects. In web pages, the global object is `window`, so you can set and access global variables using `window.variable`. 
- You can declare a constant with the same name as a function or variable in the same scope. 

## Object:
- an object is a collection of properties, a property is an association between a name and a value. 
- a value of a property can be a function, which also known as the object’s method. 
- an object property name can be any valid javascript string, or anything that can be converted to a string, including an empty string. 

### traverse over an object’s properties;
- `for ...in`: traverses all the enumerable properties of an object and its prototype chain.
- `Object.keys(o)`: returns an array with all the own enumerable properties names of an object o. 
- `Object.getOwnPropertyNames(o)`: returns an array containing all the own properties names of an object (whether enumerable or not)

### create new objects

- using object initializer, also referred to as creating object using literal notation.		

```
var obj={
		property1: value1,
		2: 	value2
		“property2”:  value3
			
}
```

- using a constructor function : create a function for the object type that specifies its name, properties and methods.  
``` 
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}
```
Then you can create a new object like this:  
```
var mycar=new Car(“Eagel”,”Talon”,1993).
```

- using `Object.create` method.


- `Object.getPrototypeOf(apple)` will retrieve the prototype of `apple`’s prototype
- `apple.prototype`  retrieves the prototype for all the instances inherited from it
- use `Object.create(null)` to create a prototypeless object
- use `apple.hasOwnProperty`  to determine whether a property belongs to `apple` 
- use `Object.DefineProperty` to define a property that’s not enumerable, which means it’s not gonna show up in the for/in loop result.


### Inheritance
- all objects in javascript inherit from at least one object. The object being inherited from is known as `prototype`. The inherited properties can be found in the prototype object of the constructor. You can add a property to a previously defined object type by using `prototype` property. 

### Defining methods
- methods are functions associated with an object. 

### Using `this` for object references
- In general, `this` refers to the calling object in a method. When combined with the form property, `this` can refer to the current object’s parent form. 


## `var o = {a: 1};`

- The newly created object `o` has `Object.prototype` as its [[Prototype]].
- `o` has no own property named `hasOwnProperty`
- `hasOwnProperty` is an own property of `Object.prototype`. So `o` inherits `hasOwnProperty` from `Object.prototype`.
- `Object.prototype` has `null` as its prototype.
- `o ---> Object.prototype ---> null`

## Array object prototype 
`var a = ["yo", "whadup", "?"];`  
- Arrays inherit from `Array.prototype` (which has methods like `indexOf`, `forEach`, etc.).
- The prototype chain looks like:
- `a ---> Array.prototype ---> Object.prototype ---> null`

## Function object prototype  
```
function f(){
  return 2;
}
```
- Functions inherit from `Function.prototype` (which has methods like `call`, `bind`, etc.),
- `f ---> Function.prototype ---> Object.prototype ---> null`

To check whether some objects have properties defined as their own, use `hasOwnProperty` to evaluate. 
Be aware of the long prototype chain, which will bring negative impacts on the performance. Also, don’t try to add new properties to the built-in prototype. 
When an instance of an object is created, the `_proto_` property is linked to its constructor’s prototype.  
Function objects are linked to `Function.Prototype`, which itself is linked to `Object.prototype`. Every function is also created with two additional hidden properties: the function’s context and the code that implement the function’s behavior. Every function object is also created with prototype property, whose value is an object with a constructor property whose value is the function. .

## Method invocation pattern
- when a function is defined as a property of an object , it is called a method. When a method is invoked, `this` refers to the object. 

## Function invocation pattern
- when a function is not a property of an object, `this` is bound to the global object. This can cause a problem since the inner function of an outer function will have a different context for `this`. A way to work around this is to define a `that` variable and assign `this` to `that`.

## Constructor invocation pattern:
- when a function is invoked with a `new` operator, then a new object will be created with a hidden link to the value of the function’s prototype member. 

## Apply invocation pattern
- function can have methods. apply method takes two arguments, the first is the value that should be bound to `this`. The second is an array of parameters. 

## General pattern of module in javascript 
- create private variables and functions inside function
- using privileged functions, through closure,to access the private variable and functions
- return privileged function or store them somewhere accessible. 






  

