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

### `let` 

```javascript
console.log(category); // Output: ReferenceError: category is not defined ... 
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
Hence, to err on the side of caution, we should _declare_ then _assign_ our variables to a value before using them.


### `const` 

The  `const`  keyword was introduced in es6 to allow  _immutable variables_. That is, variables whose value cannot be modified once assigned.

With  `const`, just as with  `let`, the variable is hoisted to the top of the block.

Let's see what happens if we try to reassign the value attached to a `const` variable.

```javascript
const PI = 3.142;
PI = 22/7; // Let's reassign the value of PI  
console.log(PI); 
// Output: TypeError: Assignment to constant variable.
```

How does `const` alter variable declaration? Let's take a look.

```javascript
console.log(PI); 
// Output: ReferenceError: PI is not defined 
const PI = 3.142;
```
Much like the `let` keyword.

Now, The same occurs when using `const` within functions.

```javascript
function getCircumference(radius) {
	console.log(circumference)
	circumference = PI*radius*2;
	const PI = 22/7;
}

getCircumference(2) // ReferenceError: circumference is not defined
```

```javascript
function getCircumference(radius) {
	const PI = 22/7;
	circumference = PI*radius*2;

	console.log(circumference);
}

getCircumference(2);
//output: 5 12.571428571428571
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg2MDg0NTI0OSwxMjY4MjE3OTcsMTE1OD
kxMTUzOSwtOTM4MDU3NzIsLTY2NDA5MTk4MCwxMDk2NjYwNDks
LTE0ODczNjM0NywyODcwMjI4NzEsMTQ3NzE1OTAwNl19
-->