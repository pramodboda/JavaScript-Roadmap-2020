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
Hence, to err on the side of caution, we should _declare_ then _assign_ our variables to a value before using them.


### `const` 

The  `const`  keyword was introduced in es6 to allow  _immutable variables_. That is, variables whose value cannot be modified once assigned.

With  `const`, just as with  `let`, the variable is hoisted to the top of the block.
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTYxMjQxMjM4LDExNTg5MTE1MzksLTkzOD
A1NzcyLC02NjQwOTE5ODAsMTA5NjY2MDQ5LC0xNDg3MzYzNDcs
Mjg3MDIyODcxLDE0NzcxNTkwMDZdfQ==
-->