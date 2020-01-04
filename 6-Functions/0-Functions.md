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
3. 


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

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY2Mzk3OTcyNyw0OTE4ODg3NzQsLTI4NT
AzMzAzLDE4MDIyNDkyMTQsMTg1Mjg1MTY2NCwxMzg1NTE5ODc5
LC03NDIyMDE1NF19
-->