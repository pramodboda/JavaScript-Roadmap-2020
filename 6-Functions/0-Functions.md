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

1. Immediately Invoked Function Expression (IIFE)
2. Anonymous Functions
3. Function Declaration
4. Function Constructors


### Immediately Invoked Function Expression (IIFE)

Another way of defining functions in JavaScript is to use Immediately Invoked Functions. The purpose of wrapping is to the namespace and control the visibility of member functions. It wraps the code inside a function scope and decreases clashing with other libraries. This is what we call Immediately Invoked Function Expression (IIFE) or Self Executing Anonymous Function.

```javascript
(function () {  
	var x = "Hello!!"; // I will invoke myself  
})();
```

### Anonymous Functions

Anonymous functions are always loaded using a variable name. if you are not using a variable name for Anonymous function it thorws an error `SyntaxError: Function statements must have a name.`

 Anonymous, as the name suggests, allows creating a function without any names identifier. It can be used as an argument to other functions. Call them using a variable name:

This is how JavaScript anonymous functions can be used:

```javascript
var func = function() {
	alert(‘This is anonymous');
}
func();

Here’s an example:
//anonymous function
var a = function() {
   return 5;
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

`sumFunction`  created with  `Function`  constructor invocation has parameters  `numberA`and  `numberB`  and the body  `return numberA + numberB`.

The functions created this way don’t have access to the current scope, thus closures cannot be created. They are always created in the global scope.

One  _possible_  application of  `new Function`  is a  [better way](https://twitter.com/WebReflection/status/269578376833024000)  to access the global object in a browser or NodeJS script:

Remember that functions  **almost never**  should be declared using  `new Function()`. Because the function body is evaluated on runtime, this approach inherits many  `eval()`  usage  [problems](http://stackoverflow.com/a/86580/1894471): security risks, harder debugging, no way to apply engine optimizations, no editor auto-complete.



let checkNumber = function check (num){

return (num %2==0)?"even" : "odd"

}

console.log(checkNumber(50))

// even

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI1MjczNDI5MiwxMDc3NDA2NTYxLDE2Nj
M5Nzk3MjcsNDkxODg4Nzc0LC0yODUwMzMwMywxODAyMjQ5MjE0
LDE4NTI4NTE2NjQsMTM4NTUxOTg3OSwtNzQyMjAxNTRdfQ==
-->