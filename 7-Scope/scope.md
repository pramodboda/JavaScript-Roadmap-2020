
# Scope in JavaScript

In the JavaScript language there are two types of scopes:

-   Global Scope
-   Local Scope (inside block/ function)

## Global Scope

```javascript
// Initialize a global variable
var hobby = "dancing";

hobby;
// "dancing"

```

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
eyJoaXN0b3J5IjpbMTc2NDg3MjY1MCwtNTEwMDMyNTMsMTU5Nj
g2NTQxLDQwMTI5MDA4Nl19
-->