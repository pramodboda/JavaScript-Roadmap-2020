# Variables

  

### Types of variable declarations (`var`, `let`, `const`)

  

### Initialized and Uninitialized Variables in JavaScript

  

### Variable Declaration with `var` keyword

  

Declared But Not Initialized any value, even thought JavaScript will assign the `undefined` value to the uninitialized variable.

  

```javascript
var  person; // Declared But Not Initialized any value.

// Calling a variable.
person;
// output: undefined

```

### Variable Initialization

Initialized means a variable was declared (i.e. using var, let, or const) and was assigned a value.

```javascript

var  person; // Declared But Not Initialized any value.
person  =  "Pramod"; // Now Initialized
// Calling a variable.

person;
// output: "Pramod"
```

### Initializing variable without `var` keyword
If you declared or initialized a variable anywhere in the script without using any `var` or `let` or `const` keyword, by JavaScript that variable will be converted to global variable for entire script.

```javascript
// person = "Pramod"; // Became global by JavaScript
function  someFunc(){
	person  =  "Pramod"; // this will become global variable at the top of script.
}

  

// variable `person` can be accessible from outside the function, Thats not the best practice.

person;

// output: "Pramod"

```

  

## Variable Declaration with `let` keyword
`let` will not allow the duplicate variable declaration.

re-declaration is not allowed with `let`.

You can re-initialize/ re-assign the vaule to the declared variable. but you can't re-declaration the variable name.

  

```javascript

let  person  =  "Pramod";
let  person  =  "Boda"; // Uncaught SyntaxError: `let` will not allow the duplicate variable declaration, re-declarations is not allowed with `let`.

```

  

## Variable Declaration with `const` keyword

  

With `let` you can atleast re-initialize/ re-assign the vaule to the declared variable. but you can't re-declaration the variable name.

 
But with `const` you can't do re-declaration or re-initialize/ re-assign
```javascript
const  person  =  "Pramod";
const  person  =  "Boda";
or
person  =  "Boda"; //Uncaught SyntaxError
```

  

| | Scope | Re-Declaration | Re-Initialization | Mutable | Temporal Dead Zone |

|---|---|---|---|---|---|

| `var` | function based scope | Yes | Yes | Yes | No |

| `let` | block based scope | No | Yes | Yes | Yes |

| `const` | block based scope | No | No | Yes | Yes |

  

## `var` hoisting thing

  

```javascript

var  age;

console.log(age);

  

//output: undefined

```

  

```javascript

console.log(age);

var  age; // At this point when we delcared a variable with var its declaraion - hoisted at the top of the scope.

  

//output: undefined

```

  

```javascript

console.log(age);

let  age; // Error: At this point when we delcared a variable with let its declaraion - hoisted at the same place(scope).

  

//output: undefined

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNDM4NDkyNjgsLTEwMDgyNzE4Myw3Mz
A5OTgxMTZdfQ==
-->