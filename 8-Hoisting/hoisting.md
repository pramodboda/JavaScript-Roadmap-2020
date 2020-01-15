# Hoisting

```javascript
console.log(category); //Output: undefined
var category = 'watercolor';
```

This is how the interpreter views the above code:
```javascript
var category;
console.log(category); // Output: undefined
category = 'watercolor';
```

The best option would be to declare and initialise our variable before use.

## Function scoped variables

```javascript
function hoist() {
	console.log(message);
	var message='Hoisting is all the rage!';
}
hoist();
```
This is how the interpreter views the above code:
```javascript
function hoist() {
	var message;
	console.log(message);
	message='Hoisting is all the rage!';
}
hoist();
// Ouput: undefined
```

To avoid this pitfall, we would make sure to **declare** and **initialise** the variable before we use it:


<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAzOTI3NDUzMSwxMDk2NjYwNDksLTE0OD
czNjM0NywyODcwMjI4NzEsMTQ3NzE1OTAwNl19
-->