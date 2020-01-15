# Hoisting

## Variables Hoisting

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

>:warning: The best option would be to **declare** and **initialise** our variable before use.

### Function scoped variables

```javascript
function painting() {
	console.log(category);
	var category='watercolor!';
}
painting();
// Ouput: undefined
```
This is how the interpreter views the above code:
```javascript
function painting() {
	var category;
	console.log(category);
	category='watercolor!';
}
painting();
// Ouput: undefined
```

>To avoid this pitfall, we would make sure to **declare** and **initialise** the variable before we use it:

```javascript
function painting() {
	var category='watercolor!';
	return category;
}
painting();
// Ouput: "watercolor!"
```

### `let` or `const`

```javascript
console.log(category); // Output: ReferenceError: hoist is not defined ... 
let category = 'watercolor!';
```
Like before, for the  `var`  keyword, we expect the output of the log to be  `undefined`. However, since the es6  _let_  doesn't take kindly on us using undeclared variables, the interpreter explicitly spits out a  `Reference`  error.

This ensures that we  **always**  declare our variables first.

However, we still have to be careful here. An implementation like the following will result in an ouput of `undefined` instead of a `Reference error`.

```javascript
let category;
console.log(category); // Output: undefined 
category = 'watercolor!';
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA0NjcxOTAxMSwtOTM4MDU3NzIsLTY2ND
A5MTk4MCwxMDk2NjYwNDksLTE0ODczNjM0NywyODcwMjI4NzEs
MTQ3NzE1OTAwNl19
-->