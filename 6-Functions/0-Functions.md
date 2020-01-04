# Functions

Functions are nothing but set of statements in a block.
```javascript
function name(parameters){
...statements ...
}
//To invoke our function, we call it.
name(arguments);
```




## Different ways of declaring functions in JavaScript?


### Immediately Invoked Function Expression (IIFE)
```javascript
(function () {  
var x = "Hello!!"; // I will invoke myself  
})();
```


### Anonymous Functions

Anonymous functions are always loaded using a variable name. if you not using a variable name for Anonymous function it thorws an error `SyntaxError: Function statements must have a name.`

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
eyJoaXN0b3J5IjpbNDkxODg4Nzc0LC0yODUwMzMwMywxODAyMj
Q5MjE0LDE4NTI4NTE2NjQsMTM4NTUxOTg3OSwtNzQyMjAxNTRd
fQ==
-->