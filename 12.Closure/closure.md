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
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU3MDU1ODk0MF19
-->