# abhisheksirigari-UI-interview-questions-answers-intermediate

## Define ES6 and mention the new features of ES6?
Answer: 
Below are the new features listed:
Constants (Immutable variables)
Scoping
Arrow functions
Extended parameter handling
Template literals
Extended literals
Modules
Classes
Enhanced Regular expressions
Enhanced object properties.
Destructuring Assignment
Symbol Type
Iterators
Generator
Map/Set & WeakMap/WeakSet
Typed Arrays
Built-in Methods
Promises
Metaprogramming
Internationalization and Localization.

## Explain about Webpack and the benefits of using Webpack?
Answer: 
Webpack is used to bundle javascript files that can be used in a browser. Webpack processes the 
application and builds a dependency graph to map each module of the project requirement and generated the
bundles. It allows you to run that environment which has been hosted babel. The advantage of using a web pack 
is that it bundles multiple modules and packs into a single JavaScript file. It integrated the dev server which
helps in updating code and asset management.

## Explain about Default parameter values, Rest parameter, Spread operator?
Answer:
Default parameter values are used to initialize the functions with default values. The value of a parameter 
can be anything like a null value, number or function.
The rest parameter is used to retrieve all the arguments to invoke the function. It means we can push the items 
of different categories separately. The rest parameter uses the rest parameter to combine parameters into a single array parameter.
A spread operator is donated by … and then the variable name has been provided. E.g. ‘…X’ syntax of spread operator. 
It has been used to manipulate objects and array in ES6 and to copy the enumerable properties from one object to another.


## Explain briefly about classes, modules, and proxies?
Answer:
Classes are based on the OOP style that is object-oriented programming. The class declaration makes the patterns
easier to use. It supports inheritance, base class access, static methods, and constructors.

Modules: it defines the patterns from popular javascript module loaders. It supports exporting or importing the 
values from or to modules without the global namespace. It supports marking the value as the default exported 
value and max-min values.
Proxies: It enables object creation with a wide variety of behaviors available to host objects. It can be used 
for logging, profiling, etc.

## Can you assign an anonymous function to a variable and pass it as an argument to another function?
Yes! An anonymous function can be assigned to a variable. It can also be passed as an argument to another function.

## What is argument objects in JavaScript & how to get the type of arguments passed to a function?
JavaScript variable arguments represents the arguments that are passed to a function. Using typeof operator, 
we can get the type of arguments passed to a function. 
For example −
```javascript
function func(x){
console.log(typeof x, arguments.length);
}
func(); //==> "undefined", 0
func(7); //==> "number", 1
func("1", "2", "3"); //==> "string", 3
```

## What is the difference between Attributes and Property?
Attributes-  provide more details on an element like id, type, value etc.
Property-  is the value assigned to the property like type=”text”, value=’Name’ etc.

## List out the different ways an HTML element can be accessed in a JavaScript code.
Here are the list of ways an HTML element can be accessed in a Javascript code:
(i) getElementById(‘idname’): Gets an element by its ID name
(ii) getElementsByClass(‘classname’): Gets all the elements that have the given classname.
(iii) getElementsByTagName(‘tagname’): Gets all the elements that have the given tag name.
(iv) querySelector(): This function takes css style selector and returns the first selected element.

##  What is an event bubbling in JavaScript?
Event bubbling is a way of event propagation in the HTML DOM API, when an event occurs in an element 
inside another element, and both elements have registered a handle for that event. With bubbling, the 
event is first captured and handled by the innermost element and then propagated to outer elements. 
The execution starts from that event and goes to its parent element. Then the execution passes to its
parent element and so on till the body element.

##  What are Exports & Imports?
Imports and exports help us to write modular JavaScript code. Using Imports and exports we can split our 
code into multiple files. 
For example-
```javascript
//------ lib.js ------</span>
export const sqrt = Math.sqrt;</span>
export function square(x) {</span>
return x * x;</span>
}
export function diag(x, y) {
return sqrt(square(x) + square(y));
}
 
//------ main.js ------</span>
 { square, diag } from 'lib';
console.log(square(5)); // 25
console.log(diag(4, 3)); // 5
```

## What will be the output of the following code?
```javascript
var Output = (function(x)
{
Delete X;
return X;
}
)(0);
console.log(output);
```
The output would be 0. The delete operator is used to delete properties from an object. Here x is 
not an object but a local variable. delete operators don’t affect local variables.


## What type of errors does JavaScript have?
Answer: Following are the 2 types of error:
Load time errors: Errors which come up when loading a web page like improper syntax errors are known 
as Load time errors and it generates the errors dynamically.
Run time errors: Errors that come due to misuse of the command inside the HTML language.
Logical Errors: These are the errors that occur due to the bad logic performed on a function which is 
having different operation.

## The following recursive code will cause a stack overflow if the array list is too large. 
## How can you fix this and still retain the recursive pattern?
```javascript
var list = readHugeList();

var nextListItem = function() {
    var item = list.pop();

    if (item) {
        // process the list item...
        nextListItem();
    }
};
```
The potential stack overflow can be avoided by modifying the nextListItem function as follows:
```javascript
var list = readHugeList();

var nextListItem = function() {
    var item = list.pop();

    if (item) {
        // process the list item...
        setTimeout( nextListItem, 0);
    }
};
```
The stack overflow is eliminated because the event loop handles the recursion, not the call stack.
When nextListItem runs, if item is not null, the timeout function (nextListItem) is pushed to the 
event queue and the function exits, thereby leaving the call stack clear. When the event queue runs
its timed-out event, the next item is processed and a timer is set to again invoke nextListItem. 
Accordingly, the method is processed from start to finish without a direct recursive call, so the 
call stack remains clear, regardless of the number of iterations.

## What will be the output of the following code:
```javascript
for (var i = 0; i < 5; i++) {
	setTimeout(function() { console.log(i); }, i * 1000 );
}
```
## Explain your answer. How could the use of closures help here?

Answer: 
The code sample shown will not display the values 0, 1, 2, 3, and 4 as might be expected; 
rather, it will display 5, 5, 5, 5, and 5.

The reason for this is that each function executed within the loop will be executed after 
the entire loop has completed and all will therefore reference the last value stored in i, 
which was 5.

Closures can be used to prevent this problem by creating a unique scope for each iteration, storing 
each unique value of the variable within its scope, as follows:
```javascript
for (var i = 0; i < 5; i++) {
    (function(x) {
        setTimeout(function() { console.log(x); }, x * 1000 );
    })(i);
}
```
This will produce the presumably desired result of logging 0, 1, 2, 3, and 4 to the console.

In an ES2015 context, you can simply use let instead of var in the original code:
```javascript
for (let i = 0; i < 5; i++) {
	setTimeout(function() { console.log(i); }, i * 1000 );
}
```

## What is the output out of the following code? Explain your answer.
```javascript
var a={},
    b={key:'b'},
    c={key:'c'};

a[b]=123;
a[c]=456;

console.log(a[b]);
```
Answer: The output of this code will be 456 (not 123).
The reason for this is as follows: When setting an object property, JavaScript will
implicitly stringify the parameter value. In this case, since b and c are both objects, they 
will both be converted to "[object Object]". As a result, a[b] anda[c] are both equivalent to 
a["[object Object]"] and can be used interchangeably. Therefore, setting or referencing a[c] 
is precisely the same as setting or referencing a[b].

## What will be the output of this code?
```javascript
var x = 21;
var girl = function () {
    console.log(x);
    var x = 20;
};
girl ();
```
Answer: Neither 21, nor 20, the result is undefined

It’s because JavaScript initialization is not hoisted.
(Why doesn’t it show the global value of 21? The reason is that when the function is 
executed, it checks that there’s a local x variable present but doesn’t yet declare it, 
so it won’t look for global one.)

## Define event bubbling?
JavaScript allows DOM elements to be nested inside each other. In such a case, if the handler of 
the child is clicked, the handler of parent will also work as if it were clicked too.

