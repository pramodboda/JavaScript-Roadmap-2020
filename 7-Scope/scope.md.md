
```javascript
for (vi = 0; i < 5; i++) {
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
eyJoaXN0b3J5IjpbMTk1NTQwMDYyOV19
-->