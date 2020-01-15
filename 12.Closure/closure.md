# JavaScript  Closures

Global variables can be made local (private) with **closures**. 



Suppose you want to use a variable for counting something, and you want this counter to be available to all functions.

You could use a global variable, and a  `function`  to increase the counter:
```javascript
var counter = 0;

// Function to increment counter
function add() {
  return counter += 1;
}

add();
//output: 1

add();
//output: 2

add();
//output: 3

counter;
//output: 3
```

There is a problem with the solution above: Any code on the page can change the counter, without calling `add()`.

The counter should be local to the `add()` function, to prevent other code from changing it:

We can remove the global counter and access the local counter by letting the function return it:

```javascript
// Function to increment counter  
function add() {  
	var counter = 0;  
	counter += 1;  
	return counter;  
}  
  
// Call add() 3 times  
add(); 
//output: 1 

add();  
//output: 1

add();  
//output: 1
  
//The counter should now be 3. But it is 1. 
```
It did not work because we reset the local counter every time we call the function.

**A JavaScript inner function can solve this.**

This could have solved the counter dilemma, if we could reach the  `plus()`  function from the outside.

We also need to find a way to execute  `counter = 0`  only once.

**We need a closure.**

----------

## JavaScript Closures

Remember self-invoking functions? What does this function do?

```javascript
var add = (function () {
	var counter =  0;  
	return function () {
		counter +=  1;
		return  counter
	}
})();  
  
add();  
add();  
add();  
  
// the counter is now 3
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMzY0NzkzOTQsLTEwNDgyNDcwNjZdfQ
==
-->