
# Scope in JavaScript

In the JavaScript language there are two types of scopes:

-   Global Scope
-   Local Scope (inside block/ function)

## Global Scope
Variables defined outside any function, block, or module scope have global scope.
Variables in global scope can be accessed from everywhere in the application.
```javascript
// Initialize a global variable
let hobby = "dancing";

hobby;
// "dancing"
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
// Uncaught ReferenceError: hobby is not defined
```
```javascript
(function autoExecute() {
    let hobby = "painting";
    return hobby;
})();
// "painting"
```

## ````
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
//5
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
//Uncaught ReferenceError: i is not defined
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIyNzY1MjA3MiwtMTE1MTc0MDQ3OCwtNT
EwMDMyNTMsMTU5Njg2NTQxLDQwMTI5MDA4Nl19
-->