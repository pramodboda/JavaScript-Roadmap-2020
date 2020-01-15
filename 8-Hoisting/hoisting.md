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

>:warning: The best option would be to **declare** and **initialise** our variable before use.

## Function scoped variables

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

`let` or `const`

```javascript
console.log(hoist); // Output: ReferenceError: hoist is not defined ... let hoist = 'The variable has been hoisted.';
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2OTE5NDkxNDIsMTA5NjY2MDQ5LC0xND
g3MzYzNDcsMjg3MDIyODcxLDE0NzcxNTkwMDZdfQ==
-->