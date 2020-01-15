# JavaScript  Closures

Global variables can be made local (private) with **closures**. 
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
eyJoaXN0b3J5IjpbNzQzOTI3NjJdfQ==
-->