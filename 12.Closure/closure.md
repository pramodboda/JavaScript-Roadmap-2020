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
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExMjkxNzU0NDBdfQ==
-->