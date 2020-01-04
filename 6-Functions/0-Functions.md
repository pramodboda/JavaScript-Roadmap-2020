# Functions

Functions are nothing but set of statements in a block.
```javascript
function name(parameters){
...statements ...
}
//To invoke our function, we call it.
name(arguments);
```




## Different ways of declaring functions in JavaScript

1. IIFE (Immediately Invoked Function Expression)
2. Function Declaration
4. Anonymous Function Expression
5. Named Function Expression
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
```javascript
let checkNumber = function check (num){
	return (num %2==0)?"even" : "odd"
}

console.log(checkNumber(50))
// even
```

_An important point of difference between Function Declaration and Function Expression is that there is no hoisting in Function Expression. If you try the same program as the one in hoisting Function Declaration, you’ll encounter an error._

```javascript
myName()
// ReferenceError: myName is not defined

let myName =function () {
console.log(`My name is Stuti Chauhan`)
}
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

Remember that functions  **almost never**  should be declared using  `new Function()`. Because the function body is evaluated on runtime, this approach inherits many  `eval()`  usage  [problems](http://stackoverflow.com/a/86580/1894471): security risks, harder debugging, no way to apply engine optimizations, no editor auto-complete.



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU0ODMyNTM4LC04NjE3Mzg0ODAsODQzOD
Y2MzM5LDEzMDg4NDA3OTAsMTA3NzQwNjU2MSwxNjYzOTc5NzI3
LDQ5MTg4ODc3NCwtMjg1MDMzMDMsMTgwMjI0OTIxNCwxODUyOD
UxNjY0LDEzODU1MTk4NzksLTc0MjIwMTU0XX0=
-->