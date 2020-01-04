
```javascript
let originalPrice = null;
let discount = null;
let afterDiscountPrice = null;
let youSaved = null;

function calculateBill(originalPrice, discount){
    let discounted = originalPrice * (discount / 100 );
    afterDiscountPrice = originalPrice - discounted;
    youSaved = originalPrice % afterDiscountPrice; 
    return `Price After Discount : ${afterDiscountPrice}, You saved: ${youSaved}`;
}


calculateBill(1175,15);
//"Price After Discount : 998.75, You saved: 176.25"
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI0Mjk3MDAxNyw5ODU4NjIxOTUsMjA5Mj
Y0MjQ1Myw3MzA5OTgxMTZdfQ==
-->