---
title: Notes on JQuery
date: 2014-09-13 09:16:00
categories:
- Programming

tags:
- programming
- javascript
---

## JQuery Notes

### Closures 
Closures are created whenever a variable that is defined outside the current scope is accessed from within some inner scope. In the following example, the variable counter is visible within the create, increment, and print functions, but not outside of them.  
```
function create() {
  var counter = 0;
  return {
    increment: function() {
      counter++;
    },
    print: function() {
      console.log(counter);
    }
  }
}
var c = create();
c.increment();
c.print(); // 1
```
The pattern allows you to create objects with methods that operate on data that isn't visible to the outside—the very basis of object-oriented programming. 
### Context, Call and Apply 
In JavaScript, the variable `this` always refers to the current context. By default, `this` refers to the `window` object. Within a function this context can change, depending on how the function is called. All event handlers in jQuery are called with the handling element as the context.  
```
$(document).ready(function() {
  // this refers to window.document
});
```
```
$("a").click(function() {
  // this refers to an anchor DOM element
});
```
You can specify the context for a function call using the function-built-in methods `call` and `apply`. The difference between them is how they pass arguments. `Call` passes all arguments through as arguments to the function, while `apply` accepts an array as the arguments.  
```
function scope() {
  console.log(this, arguments.length);
}
scope() // window, 0
scope.call("foobar", [1,2]); // "foobar", 1
scope.apply("foobar", [1,2]); // "foobar", 2
```

### Proxy Pattern 
Combining the above knowledge gives you as a JavaScript developer quite a lot of power. One way to combine that is to implement a proxy pattern in JavaScript, enabling the basics of aspect-oriented programming:  
```
(function() {
  // log all calls to setArray
  var proxied = jQuery.fn.setArray;
  jQuery.fn.setArray = function() {
    console.log(this, arguments);
    return proxied.apply(this, arguments);
  };
})();
```
The above wraps its code in a function to hide the "proxied"-variable. It saves jQuery's setArray-method in a closure and overwrites it. The proxy then logs all calls to the method and delegates the call to the original. Using `apply(this, arguments)` guarantees that the caller won't be able to notice the difference between the original and the proxied method. 
### Selector 
A `selector` is used in jQuery to select DOM elements from a DOM document. That document is, in most cases, the DOM document present in all browsers, but can also be a XML document received via AJAX. 
### Event
The standard events in the Document Object Model are: `blur`, `focus`, `load`, `resize`, `scroll`, `unload`, `beforeunload`, `click` ,`dblclick`, `mousedown`, `mouseup`, `mousemove`, `mouseover`, `mouseout`, `mouseenter`, `mouseleave`, `change`, `select`, `submit`, `keydown`, `keypress`, and `keyup`. Since the DOM event names have predefined meanings for some elements, using them for other purposes is not recommended. jQuery's event model can trigger an event by any name on an element, and it is propagated up the DOM tree to which that element belongs, if any.

### Element 
An `element` in the Document Object Model (DOM) has attributes, text and children. It provides methods to traverse the parent and children and to get access to its attributes. Due to a lot of flaws in DOM API specifications and implementations, those methods are no fun to use. jQuery provides a wrapper around those elements to help interacting with the DOM. But often enough you will be working directly with DOM elements, or see methods that (also) accept DOM elements as arguments. Whenever you use jQuery's each-method, the context of your callback is set to a DOM element. That is also the case for event handlers.  
 
### jQuery method
Since jQuery methods often use CSS selectors to match elements from a document, the set of elements in a jQuery object is often called a set of `matched elements` or `selected elements`. The jQuery object itself behaves much like an array;it has a length property and the elements in the object can be accessed by their numeric indices `[0] to [length-1]`. Note that a jQuery object is not actually a Javascript Array object, so it does not have all the methods of a true Array object such as `join()`.  
Most frequently, you will use the `jQuery()` function to create a jQuery object. `jQuery()` can also be accessed by its familiar single-character alias of `$()`, unless you have called `jQuery.noConflict()` to disable this option. Many jQuery methods return the jQuery object itself, so that method calls can be chained:  
 `$("p").css("color", "red").find(".special").css("color", "green");`  

Whenever you use a `destructive` jQuery method that potentially changes the set of elements in the jQuery object, such as `.filter()` or `.find()`, that method actually returns a new jQuery object with the resulting elements. To return to the previous jQuery object, you use the `.end()` method.  
A jQuery object may be empty, containing no DOM elements. You can create an empty jQuery object with `$()` (that is, passing no arguments at all). A jQuery object may also be empty if a selector doesn't select any elements, or if a chained method filters out all the elements. It is not an error; any further methods called on that jQuery object simply have no effect since they have no elements to act upon. So, in this example if there are no bad entries on the page then no elements will be colored red:  
`$(".badEntry").css({color: "red"});`

### XMLHttpRequest 
Some of jQuery's AJAX functions return the native `XMLHttpRequest(XHR) object`, or pass it as an argument to `success/error/complete` handlers, so that you can do additional processing or monitoring on the request. Note that AJAX functions only return or pass an `XHR object` when an XHR object is actually used in the request. For example, `JSONP` requests and cross-domain `GET` requests use a script element rather than an XHR object. Although the XHR object is a standard, there are variations in its behavior on different browsers.


### Selector Context
By default, selectors perform their searches within the DOM starting at the document root. However, an alternate context can be given for the search by using the optional second parameter to the $() function. For example, to do a search within an event handler, the search can be restricted like so:  
```
$('div.foo').click(function() {
  $('span', this).addClass('bar');
});
```
When the search for the span selector is restricted to the context of this, only spans within the clicked element will get the additional class.Internally, selector context is implemented with the `.find()` method, so `$('span', this)` is equivalent to `$(this).find('span')`.




