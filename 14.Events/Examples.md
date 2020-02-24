## Example 1:
### Event Listener

html:
```html
<button class="buy">Buy Item 1</button>
<button class="buy">Buy Item 2</button>
<button class="buy">Buy Item 3</button>
<button class="buy">Buy Item 4</button>
<button class="buy">Buy Item 5</button>
<button class="buy">Buy Item 6</button>
<button class="buy">Buy Item 7</button>
<button class="buy">Buy Item 8</button>
<button class="buy">Buy Item 9</button>
<button class="buy">Buy Item 10</button>
```

js:
```js
// Listen on multiple items
const buyBtns = document.querySelectorAll('.buy');
console.log(buyBtns);

function buyItem(){
  console.log('Buying Item');
}

function handleBuyBtnClick(anythingWeWant){
  console.log('Binding the buy button');
  anythingWeWant.addEventListener('click', buyItem);
}

console.log(buyBtns);
// console.dir(btns);

buyBtns.forEach(handleBuyBtnClick);
```

### Event - Target
A handler on a parent element can always get the details about where it actually happened.

```html
<button class="btnLike">Like1</button>
<button class="btnLike">Like2</button>
<button class="btnLike">Like3</button>
<button class="btnLike">Like4</button>
<button class="btnLike">Like5</button>
<button class="btnLike">Like6</button>
<button class="btnLike">Like7</button>
<button class="btnLike">Like8</button>
<button class="btnLike">Like9</button>
<button class="btnLike">Like10</button>
<button class="btnLike">Like11</button>
<button class="btnLike">Like12</button>
<button class="btnLike">Like13</button>
<button class="btnLike">Like14</button>
<button class="btnLike">Like15</button>
```

```js
const btns = document.querySelectorAll('.btnLike');
console.log(btns);

function handleBtnClickLike(){
  console.log('you liked it!');
}

btns.forEach(function(btnItemLike){
  btnItemLike.addEventListener('click', handleBtnClickLike);
});
```

## **`event.target`**
```js
const btns = document.querySelectorAll('.btnLike');
console.log(btns);

function handleBtnClickLike(e){
  console.log('you liked it!');
  console.log(e.target);
}

btns.forEach(function(btnItemLike){
  btnItemLike.addEventListener('click', handleBtnClickLike);
});
```
## **`event.target`**  with `data-` attributes
```html
<button data-price="100" class="btnLike">Like1</button>
<button data-price="200" class="btnLike">Like2</button>
<button data-price="300" class="btnLike">Like3</button>
<button data-price="400" class="btnLike">Like4</button>
<button data-price="500" class="btnLike">Like5</button>
<button data-price="600" class="btnLike">Like6</button>
<button data-price="700" class="btnLike">Like7</button>
<button data-price="800" class="btnLike">Like8</button>
<button data-price="900" class="btnLike">Like9</button>
<button data-price="1000" class="btnLike">Like10</button>
<button data-price="1100" class="btnLike">Like11</button>
<button data-price="1200" class="btnLike">Like12</button>
<button data-price="1300" class="btnLike">Like13</button>
<button data-price="1400" class="btnLike">Like14</button>
<button data-price="1500" class="btnLike">Like15</button>
```

```js
const btns = document.querySelectorAll('.btnLike');
console.log(btns);

function handleBtnClickLike(e){
  console.log('you liked it!');
  console.log(e.target.dataset);
}

btns.forEach(function(btnItemLike){
  btnItemLike.addEventListener('click', handleBtnClickLike);
});
```
update:
```js
function handleBtnClickLike(e){
  console.log('you liked it!');
  console.log(e.target.dataset.price);
}
```
update `typeof`:

```js
function handleBtnClickLike(e){
  console.log('you liked it!');
  console.log( typeof e.target.dataset.price);
}
```
update `parseFloat` :
```js
function handleBtnClickLike(e){
  console.log('you liked it!');
  console.log( parseFloat(e.target.dataset.price));
}
```
## **`event.currentTarget`**
```js
function handleBtnClickLike(e){
  console.log('you liked it!');
  console.log(e.target);
  console.log(e.currentTarget);
}
```

## Different btw **`event.target`** and **`event.currentTarget`**

-   `target`  is the element that triggered the event (e.g., the user clicked on)
-   `currentTarget`  is the element that the event listener is attached to.

```js
const btns = document.querySelectorAll('.btnLike');
console.log(btns);

function handleBtnClickLike(e){
  // console.log('you liked it!');
  // console.log( parseFloat(e.target.dataset.price));
  console.log(e.target);
  console.log(e.currentTarget);
}

btns.forEach(function(btnItemLike){
  btnItemLike.addEventListener('click', handleBtnClickLike);
});
```
update:
```js
function handleBtnClickLike(e){
  // console.log('you liked it!');
  // console.log( parseFloat(e.target.dataset.price));
  console.log(e.target);
  console.log(e.currentTarget);
  console.log(e.target === e.currentTarget);
}
```

Now update:
```html
<button data-price="100" class="btnLike">Like<strong>1</strong></button>
<button data-price="200" class="btnLike">Like<strong>2</strong></button>
<button data-price="300" class="btnLike">Like<strong>3</strong></button>
<button data-price="400" class="btnLike">Like<strong>4</strong></button>
<button data-price="500" class="btnLike">Like<strong>5</strong></button>
<button data-price="600" class="btnLike">Like<strong>6</strong></button>
<button data-price="700" class="btnLike">Like<strong>7</strong></button>
<button data-price="800" class="btnLike">Like<strong>8</strong></button>
<button data-price="900" class="btnLike">Like<strong>9</strong></button>
<button data-price="1000" class="btnLike">Like<strong>10</strong></button>
<button data-price="1100" class="btnLike">Like<strong>11</strong></button>
<button data-price="1200" class="btnLike">Like<strong>12</strong></button>
<button data-price="1300" class="btnLike">Like<strong>13</strong></button>
<button data-price="1400" class="btnLike">Like<strong>14</strong></button>
<button data-price="1500" class="btnLike">Like<strong>15</strong></button>
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbNTkyNzQ5MzM1LDE0MDgxMjI2MzUsLTU2OD
YyNjczNSwyMDk0MTA1ODkxLC03MzAzNTYwODcsNTUzNDA3NTI1
LC03ODg1MTEzNDcsLTExNTc0OTQyNzldfQ==
-->