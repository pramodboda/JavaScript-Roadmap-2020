# Hoisting

## Hoisting `Variables`

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

## Hoisting `Functions`
JavaScript functions can be loosely classified as the following:

1.  Function declarations
2.  Function expressions

We'll investigate how hoisting is affected by both function types.

### `Function` declarations

These are of the following form and are hoisted completely to the top. Now, we can understand why JavaScript enable us to invoke a function seemingly before declaring it.

```javascript
hoisted(); // Output: "This function has been hoisted."
function hoisted() {
	console.log('This function has been hoisted.'); 
};
```

### `Function` expressions

Function expressions, however are not hoisted.
```javascript
expression(); //Output: "TypeError: expression is not a function
var expression = function() {
	console.log('Will this work?');
};
```

Let's try the combination of a function declaration and expression.

```javascript
expression(); // Ouput: TypeError: expression is not a function
var expression = function hoisting() {
	console.log('Will this work?');
};
```
As we can see above, the variable declaration `var expression` is hoisted but it's assignment to a function is not. Therefore, the intepreter throws a `TypeError` since it sees `expression` as a _variable_and not a _function_.

## Hoisting `Classes`

JavaScript classes too can be loosely classified either as:

1.  Class declarations
2.  Class expressions

### `Class` declarations

Much like their function counterparts, JavaScript class declarations are hoisted. However, they remain uninitialised until evaluation. This effectively means that you have to declare a class before you can use it.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTcxNjQwNjM1MywtMjYyNTM4ODc5XX0=
-->