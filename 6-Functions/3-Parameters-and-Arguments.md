
```javascript
let originalPrice = null;
let discount = null;
let afterDiscountPrice = null;
let youSaved = null;

function calculateBill(originalPrice, discount){
    let discounted = originalPrice * (discount / 100 );
    afterDiscountPrice = originalPrice - discounted;
    return `Price After Discount : ${afterDiscountPrice}`;
}

calculateBill(1175,15);
//"Price After Discount : 998.75"
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA5MjY0MjQ1Myw3MzA5OTgxMTZdfQ==
-->