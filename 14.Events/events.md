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

### DOM on-event handlers

This is common when an object has at most one event handler, as there is no way to add multiple handlers in this case:
```js
window.onload = () => {
  //window loaded
}
```
It’s most commonly used when handling  [XHR](https://flaviocopes.com/xhr/)  requests:

```js
const xhr = new XMLHttpRequest()
xhr.onreadystatechange = () => {
  //.. do something
}
```

### Using  `addEventListener()`

This is the  _modern way_. This method allows to register as many handlers as we need, and it’s the most popular you will find:

```js
window.addEventListener('load', () => {
  //window loaded
})
```

> Note that IE8 and below did not support this, and instead used its own  `attachEvent()`  API. Keep it in mind if you need to support older browsers.


## Listening on different elements

You can listen on  `window`  to intercept “global” events, like the usage of the keyboard, and you can listen on specific elements to check events happening on them, like a mouse click on a button.

This is why  `addEventListener`  is sometimes called on  `window`, sometimes on a DOM element.

This object contains a lot of useful properties and methods, like:

-   `target`, the DOM element that originated the event
-   `type`, the type of event
-   `stopPropagation()`, called to stop propagating the event in the DOM

([see the full list](https://developer.mozilla.org/en-US/docs/Web/API/Event)).

Other properties are provided by specific kind of events, as  `Event`  is an interface for different specific events:

-   [MouseEvent](https://developer.mozilla.org/en-US/docs/Web/API/MouseEvent)
-   [KeyboardEvent](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent)
-   [DragEvent](https://developer.mozilla.org/en-US/docs/Web/API/DragEvent)
-   [FetchEvent](https://developer.mozilla.org/en-US/docs/Web/API/FetchEvent)
-   … and others

Each of those has a MDN page linked, so you can inspect all their properties.

For example when a KeyboardEvent happens, you can check which key was pressed, in a readable format (`Escape`,  `Enter`  and so on) by checking the  `key`  property:

```js
window.addEventListener('keydown', event => {
  // key pressed
  console.log(event.key)
})

```

On a mouse event we can check which mouse button was pressed:

```js
const link = document.getElementById('my-link')
link.addEventListener('mousedown', event => {
  // mouse button pressed
  console.log(event.button) //0=left, 2=right
})
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

## Event - Target

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNzY3NDE5NDcsMTE5MTQ3NDgxOSwtMj
A0NTE5NjkxMywxMzA1MTUwODA5LDIzOTIxODQzNCw4ODkwMTE4
MzAsMjA4NzgwNDQxMCwtNjY5NTQ1OTE4LC00NDUxMTc0MF19
-->