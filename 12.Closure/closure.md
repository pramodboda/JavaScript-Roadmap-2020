# JavaScript  Closures

Global variables can be made local (private) with **closures**. 



Suppose you want to use a variable for counting something, and you want this counter to be available to all functions.

You could use a global variable, and a  `function`  to increase the counter:

var counter = 0;

// Function to increment counter
function add() {
  return counter += 1;
}
undefined
add();
1
add();
2
add();
3
counter
3
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0ODE4NDEwODRdfQ==
-->