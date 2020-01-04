# Functions

Functions are one of the key components in programming. They are defined to perform a specific task and can be called again and again to execute. The main difference between functions in Javascript and other programming languages is that in javascript functions are of first-class objects, which means that they behave like objects and can be assigned to variables, array, and other objects.

Functions are nothing but set of statements in a block.
```javascript
function name(parameters){
...statements ...
}
//To invoke our function, we call it.
name(arguments);
```




## Different ways of declaring functions in JavaScript

1. Function Declaration
3. Anonymous Function Expression
4. Named Function Expression
5. IIFE (Immediately Invoked Function Expression)
6. Function Constructors


### IIFE (Immediately Invoked Function Expression)

This means that the function runs as soon as it is defined, here function expression is enclosed within _Grouping Operator ()_,

Why do we need an IIFE in our typical function expression? We define the function and then call it sometime later any number of times, but what if I want to just call the function only once to produce an output and that's it — I don't want to use it again? This is where IIFE comes in. It is immediately executed and never ever in the future it is accessed by the program again. Since it is not called again, it doesn’t need a name, so an anonymous function expression is preferred for IIFE.

The purpose of wrapping is to the namespace and control the visibility of member functions. It wraps the code inside a function scope and decreases clashing with other libraries. This is what we call Immediately Invoked Function Expression (IIFE) or Self Executing Anonymous Function.

```javascript
(function () {
	let num = 4
	return num
})()
//4
```
```javascript
(function () {  
	var x = "Hello!!"; // I will invoke myself  
})();
```

### Anonymous Function Expression
Anonymous functions are always loaded using a variable name. if you are not using a variable name for Anonymous function it thorws an error `SyntaxError: Function statements must have a name.`

 Anonymous, as the name suggests, allows creating a function without any names identifier. It can be used as an argument to other functions. Call them using a variable name:

This is how JavaScript anonymous functions can be used:

```javascript
//Anonymous Function
let checkNumber = function (num){
	return (num %2==0)?"even" : "odd"
}

console.log(checkNumber(50))
// even
```
### Named Function Expression
A function expression is very similar to, and has almost the same syntax as, a function statement. The main difference is that a function expression does not start with the keyword `function` and the `name` of the function is also optional, in which case it becomes an _Anonymous Function_. If the function has a `name` then it is called _Named Function Expression_**.**
```javascript
let checkNumber = function check (num){
	return (num %2==0)?"even" : "odd"
}

console.log(checkNumber(50))
// even
```

_An important point of difference between Function Declaration and Function Expression is that there is no hoisting in Function Expression. If you try the same program as the one in hoisting Function Declaration, you’ll encounter an error._
```javascript
myName();

function myName() {
	console.log(`My name is Pramod Boda`)
}
//My name is Pramod Boda 
```
```javascript
myName()
// ReferenceError: myName is not defined

let myName = function () {
	console.log(`My name is Pramod Boda`)
}
// Uncaught ReferenceError: Cannot access 'myName' before initialization at <anonymous>:1:1
```

### Function Constructors

In JavaScript functions are first-class objects - a function is a regular object of type  `function`.  
The ways of the declaration described above create the same function object type. Let’s see an example:
```javascript
function sum1(a, b) {
  return a + b;
}
const sum2 = function(a, b) {
  return a + b;
}
const sum3 = (a, b) => a + b;
console.log(typeof sum1 === 'function'); // => true
console.log(typeof sum2 === 'function'); // => true
console.log(typeof sum3 === 'function'); // => true
```

The function object type has a constructor:  [`Function`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function).  
When  `Function`  is invoked as a constructor  `new Function(arg1, arg2, ..., argN, bodyString)`, a new function is created. The arguments  `arg1, args2, ..., argN`passed to constructor become the parameter names for the new function and the last argument  `bodyString`  is used as the function body code.

Let’s create a function that sums two numbers:
```javascript
const numberA = 'numberA', numberB = 'numberB';
const sumFunction = new Function(numberA, numberB, 
   'return numberA + numberB'
);
sumFunction(10, 15) // => 25
```
`sumFunction`  created with  `Function`  constructor invocation has parameters  `numberA`and  `numberB`  and the body  `return numberA + numberB`.

The functions created this way don’t have access to the current scope, thus closures cannot be created. They are always created in the global scope.

One  _possible_  application of  `new Function`  is a  [better way](https://twitter.com/WebReflection/status/269578376833024000)  to access the global object in a browser or NodeJS script:
```javascript
(function() {
   'use strict';
   const global = new Function('return this')();
   console.log(global === window); // => true
   console.log(this === window);   // => false
})();
```

Remember that functions  **almost never**  should be declared using  `new Function()`. Because the function body is evaluated on runtime, this approach inherits many  `eval()`  usage  [problems](http://stackoverflow.com/a/86580/1894471): security risks, harder debugging, no way to apply engine optimizations, no editor auto-complete.



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTMzMDQ3ODEzMCwxNTc5Mjg4NDI4LDY1Mj
I4MDc1MywtMjI4NTU0OTYsLTg2MTczODQ4MCw4NDM4NjYzMzks
MTMwODg0MDc5MCwxMDc3NDA2NTYxLDE2NjM5Nzk3MjcsNDkxOD
g4Nzc0LC0yODUwMzMwMywxODAyMjQ5MjE0LDE4NTI4NTE2NjQs
MTM4NTUxOTg3OSwtNzQyMjAxNTRdfQ==
-->