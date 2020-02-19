# Events

The event could be the DOM is loaded, or an asynchronous request that finishes fetching, or a user clicking an element or scrolling the page, or the user types on the keyboard.


## Event handlers

You can respond to any event using an  **Event Handler**, which is a function that’s called when an event occurs.

You can register multiple handlers for the same event, and they will all be called when that event happens.

To react on events we can assign a  _handler_  – a function that runs in case of an event.

Handlers are a way to run JavaScript code in case of user actions.

JavaScript offer three ways to register an event handler:
1.  HTML attribute:  `onclick="..."`.
2.  DOM property:  `elem.onclick = function`.
3.  Methods:  `elem.addEventListener(event, handler[, phase])`  to add,  `removeEventListener`  to remove.

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

Here’s a list of the most useful DOM events, just to take a look at:

**Mouse events:**

-   `click`  – when the mouse clicks on an element (touchscreen devices generate it on a tap).
-   `contextmenu`  – when the mouse right-clicks on an element.
-   `mouseover`  /  `mouseout`  – when the mouse cursor comes over / leaves an element.
-   `mousedown`  /  `mouseup`  – when the mouse button is pressed / released over an element.
-   `mousemove`  – when the mouse is moved.

**Form element events:**

-   `submit`  – when the visitor submits a  `<form>`.
-   `focus`  – when the visitor focuses on an element, e.g. on an  `<input>`.

**Keyboard events:**

-   `keydown`  and  `keyup`  – when the visitor presses and then releases the button.

**Document events:**

-   `DOMContentLoaded`  – when the HTML is loaded and processed, DOM is fully built.

**CSS events:**

-   `transitionend`  – when a CSS-animation finishes.

There are many other events. ([see the full list](https://developer.mozilla.org/en-US/docs/Web/API/Event)).

You can listen on  `window`  to intercept “global” events, like the usage of the keyboard, and you can listen on specific elements to check events happening on them, like a mouse click on a button.

This is why  `addEventListener`  is sometimes called on  `window`, sometimes on a DOM element.

## The Event object

An event handler gets an  `Event`  object as the first parameter:

```js
const link = document.getElementById('my-link')
link.addEventListener('click', event => {
  // link clicked
});
```
To properly handle an event we’d want to know more about what’s happened. Not just a “click” or a “keypress”, but what were the pointer coordinates? Which key was pressed? And so on.

When an event happens, the browser creates an  _event object_, puts details into it and passes it as an argument to the handler.

Here’s an example of getting mouse coordinates from the event object:

```js
```markup
<input type="button" value="Click me" id="elem">

<script>
  elem.onclick = function(event) {
    // show event type, element and coordinates of the click
    alert(event.type + " at " + event.currentTarget);
    alert("Coordinates: " + event.clientX + ":" + event.clientY);
  };
</script>
```
Some properties of  `event`  object:

`event.type`

Event type, here it’s  `"click"`.

`event.currentTarget`

Element that handled the event. That’s exactly the same as  `this`, unless the handler is an arrow function, or its  `this`  is bound to something else, then we can get the element from  `event.currentTarget`.

`event.clientX / event.clientY`

Window-relative coordinates of the cursor, for mouse events.

This object contains a lot of useful properties and methods, like:

-   `target`, the DOM element that originated the event
-   `type`, the type of event
-   `stopPropagation()`, called to stop propagating the event in the DOM



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

## [Object handlers: handleEvent](https://javascript.info/introduction-browser-events#object-handlers-handleevent)

We can assign not just a function, but an object as an event handler using  `addEventListener`. When an event occurs, its  `handleEvent`  method is called.

For instance:

```markup
<button id="elem">Click me</button>

<script>
  elem.addEventListener('click', {
    handleEvent(event) {
      alert(event.type + " at " + event.currentTarget);
    }
  });
</script>
```

As we can see, when  `addEventListener`  receives an object as the handler, it calls  `object.handleEvent(event)`  in case of an event.

We could also use a class for that:

```markup
<button id="elem">Click me</button>

<script>
  class Menu {
    handleEvent(event) {
      switch(event.type) {
        case 'mousedown':
          elem.innerHTML = "Mouse button pressed";
          break;
        case 'mouseup':
          elem.innerHTML += "...and released.";
          break;
      }
    }
  }

  let menu = new Menu();
  elem.addEventListener('mousedown', menu);
  elem.addEventListener('mouseup', menu);
</script>
```

Here the same object handles both events. Please note that we need to explicitly setup the events to listen using  `addEventListener`. The  `menu`  object only gets  `mousedown`  and  `mouseup`  here, not any other types of events.

The method  `handleEvent`  does not have to do all the job by itself. It can call other event-specific methods instead, like this:

```markup
<button id="elem">Click me</button>

<script>
  class Menu {
    handleEvent(event) {
      // mousedown -> onMousedown
      let method = 'on' + event.type[0].toUpperCase() + event.type.slice(1);
      this[method](event);
    }

    onMousedown() {
      elem.innerHTML = "Mouse button pressed";
    }

    onMouseup() {
      elem.innerHTML += "...and released.";
    }
  }

  let menu = new Menu();
  elem.addEventListener('mousedown', menu);
  elem.addEventListener('mouseup', menu);
</script>
```

Now event handlers are clearly separated, that may be easier to support.

## Bubbling and Capturing
```markup
<div id="tEl1">
  <em>If you click on <code>EM</code>, the handler on <code>DIV</code> runs.</em> but why?
</div>

<script>
let tEl1 = document.getElementById("tEl1");

tEl1.addEventListener("click", function(){
  alert("The handler!");
});
</script>
```
Isn’t it a bit strange? Why does the handler on `<div>` run if the actual click was on `<em>`?

## Bubbling
The bubbing princible 


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

## Event - Target
A handler on a parent element can always get the details about where it actually happened.



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk3NTQ0Mzg0MywzMjY0NDM1NDYsLTE5MD
UyNjc4MzgsLTE4OTMyMTgxNjQsLTY0MDMxMTI5NiwtMTg1MDMz
Nzc4NiwxNDk4MjI3NDgxLC0xMTQ2NTgzNzIwLC0xMTc2NzQxOT
Q3LDExOTE0NzQ4MTksLTIwNDUxOTY5MTMsMTMwNTE1MDgwOSwy
MzkyMTg0MzQsODg5MDExODMwLDIwODc4MDQ0MTAsLTY2OTU0NT
kxOCwtNDQ1MTE3NDBdfQ==
-->