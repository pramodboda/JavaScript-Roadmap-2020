# Events

The event could be the DOM is loaded, or an asynchronous request that finishes fetching, or a user clicking an element or scrolling the page, or the user types on the keyboard.

There are a lot of different kind of events.

## Event handlers

You can respond to any event using an  **Event Handler**, which is a function that’s called when an event occurs.

You can register multiple handlers for the same event, and they will all be called when that event happens.

JavaScript offer three ways to register an event handler:

### Inline event handlers

This style of event handlers is very rarely used today, due to its constraints, but it was the only way in the JavaScript early days:

```html
<a href="pramodboda.com" onclick="dosomething();">Pramod Boda Art</a>
```


## Event Listener

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
```javascript
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

## Event - Target

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIyOTAxODkxNiwyMzkyMTg0MzQsODg5MD
ExODMwLDIwODc4MDQ0MTAsLTY2OTU0NTkxOCwtNDQ1MTE3NDBd
fQ==
-->