
# Scope in JavaScript

In the JavaScript language there are two types of scopes:

-   Global Scope
-   Local Scope (inside block/ function)

A local variable can only be used inside the function where it is defined. It is hidden from other functions and other scripting code.

Global and local variables with the same name are different variables. Modifying one, does not modify the other.

## Global Scope
Variables defined outside any function, block, or module scope have global scope.
Variables in global scope can be accessed from everywhere in the application.
```javascript
// Initialize a global variable
let hobby = "dancing";

hobby;
//Output: "dancing"
```

## Local/Function/Block Scope

If a variable is declared inside a code block `{...}`, it’s only visible inside that block.

Function scope means that parameters and variables defined in a function are visible everywhere within the function, but are not visible outside of the function.

Consider the next function that auto-executes, called IIFE.
```javascript
(function autoExecute() {
    let hobby = "painting";
})();
hobby;
//Output: Uncaught ReferenceError: hobby is not defined
```
```javascript
(function autoExecute() {
    let hobby = "painting";
    return hobby;
})();
//Output: "painting"
```

## Different btw Global and Local Scopes

- Global variables can be used (and changed) by all scripts in the page (and in the window).
- A local variable can only be used inside the function where it is defined. It is hidden from other functions and other scripting code.
- Global and local variables with the same name are different variables. Modifying one, does not modify the other.

> :warning: 
Do NOT create global variables unless you intend to.
Your global variables (or functions) can overwrite window variables (or functions).  
Any function, including the window object, can overwrite your global variables and functions.


## different between `var`,`let` and `const` scope
`var` variables are function scope.
```javascript
for (var i = 0; i < 5; i++) {
  console.log(i);
}

0
1
2
3
4

i
//Output: 5
```
`let` and `const` variables are block scope. can not access outside of the block.
```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}

0
1
2
3
4

i
//Output: Uncaught ReferenceError: i is not defined
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUyOTkzMTM4Nl19
-->