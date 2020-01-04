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
As you can see above, the following pair of parentheses converts the code inside the parentheses into an expression:

function(){...}


### Anonymous Functions

Anonymous functions are always loaded using a variable name. if you not using a variable name for Anonymous function it thorws an . Anonymous, as the name suggests, allows creating a function without any names identifier. It can be used as an argument to other functions. Call them using a variable name:

This is how JavaScript anonymous functions can be used:

var func = function() {
   alert(‘This is anonymous');
}
func();

Here’s an example:

//anonymous function
var a = function() {
   return 5;
}

function Display()
      {
         alert("Hello World!");
      }
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc0NDk1ODM5MiwxODAyMjQ5MjE0LDE4NT
I4NTE2NjQsMTM4NTUxOTg3OSwtNzQyMjAxNTRdfQ==
-->