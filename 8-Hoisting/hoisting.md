# Hoisting

```javascript
console.log(category); //Output: undefined
var category = 'watercolor';
```

same as 
```javascript
var category;
console.log(category); // Output: undefined
category = 'watercolor';
```

The best option would be to declare and initialise our variable before use.

## Function scoped variables

```javascript
function hoist() {   console.log(message);   var message='Hoisting is all the rage!' }  hoist();
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUyMTA4MTM5OSwxMDk2NjYwNDksLTE0OD
czNjM0NywyODcwMjI4NzEsMTQ3NzE1OTAwNl19
-->