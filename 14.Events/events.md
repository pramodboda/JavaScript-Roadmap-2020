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

## What mechanism should I use?
Of the three mechanisms, you definitely shouldn't use the HTML event handler attributes — these are outdated, and bad practice, as mentioned above.

The other two are relatively interchangeable, at least for simple uses:

-   Event handler properties have less power and options, but better cross-browser compatibility (being supported as far back as Internet Explorer 8). You should probably start with these as you are learning.
-   DOM Level 2 Events (`addEventListener()`, etc.) are more powerful, but can also become more complex and are less well supported (supported as far back as Internet Explorer 9). You should also experiment with these, and aim to use them where possible.



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

## Event Bubbling(Bottom to Top)
The bubbling principle is simple.

Event Bubbling is the event starts from the **it first runs the handlers on deepest element or target element, then on its parent, then all its ancestors which are on the way to bottom to top**. At present, all the modern browsers have event bubbling as the default way of event flow.

Let’s say we have 3 nested elements `FORM > DIV > P` with a handler on each of them:
```html
<h1>Event - Bubbling</h1>
<form id="formEl">FORM
  <div id="divEl">DIV
    <p id="pEl">P</p>
  </div>
</form>
```
```css
  body * {
    margin: 10px;
    border: 1px solid blue;
  }
```
```js
let formEl = document.getElementById('formEl');
let divEl = document.getElementById('divEl');
let pEl = document.getElementById('pEl');

formEl.addEventListener("click", function(){
  alert("FORM");
});

divEl.addEventListener("click", function(){
  alert("DIV");
});

pEl.addEventListener("click", function(){
  alert("P");
});
```
A click on the inner  `<p>`  first runs  `onclick`:

1.  On that  `<p>`.
2.  Then on the outer  `<div>`.
3.  Then on the outer  `<form>`.
4.  And so on upwards till the  `document`  object.

So if we click on `<p>`, then we’ll see 3 alerts: `p` → `div` → `form`.

The process is called “bubbling”, because events “bubble” from the inner element up through parents like a bubble in the water.

> :information_source: _Almost_  all events bubble.
> The key word in this phrase is “almost”. 
> For instance, a  `focus`  event does not bubble. There are other examples too, we’ll meet them. But still it’s an exception, rather than a rule, most events do bubble.



## Stop Event Bubbling :
If you want to stop the **event bubbling**, this can be achieved by the use of the `event.stopPropagation()` method. If you want to stop the event flow from event target to top element in DOM, `event.stopPropagation()` method stops the event to travel to the bottom to top.


```html
<h1>Event - Bubbling</h1>
<form id="formEl">FORM
  <div id="divEl">DIV
    <p id="pEl">P</p>
  </div>
</form>
```
```css
  body * {
    margin: 10px;
    border: 1px solid blue;
  }
```
```js
let formEl = document.getElementById('formEl');
let divEl = document.getElementById('divEl');
let pEl = document.getElementById('pEl');


formEl.addEventListener("click", function(){
  alert("FORM");
});

divEl.addEventListener("click", function(){
  alert("DIV");
});

pEl.addEventListener("click", function(e){
  alert("P");
  e.stopPropagation();
});
```

later try this and see output:
```js
formEl.addEventListener("click", function(){
  alert("FORM");
});

divEl.addEventListener("click", function(e){
  alert("DIV");
  e.stopPropagation();  
});

pEl.addEventListener("click", function(){
  alert("P");
});
```


## Event Capturing(Top to Bottom)
**Event Capturing** is the event starts from top element to target element. Modern browser doesn’t support event capturing by default but we can achieve that by code in JavaScript.
We can use third optional argument of addEventListner to set `true` to enable event capturing in the parent div.
```html
<h1>Event Capturing</h1>
<form id="formEl">FORM
  <div id="divEl">DIV
    <p id="pEl">P</p>
  </div>
</form>
```
```css
  body * {
    margin: 10px;
    border: 1px solid blue;
  }
```
```js
let formEl = document.getElementById('formEl');
let divEl = document.getElementById('divEl');
let pEl = document.getElementById('pEl');

formEl.addEventListener("click", function(){
  alert("FORM");
},true);

divEl.addEventListener("click", function(){
  alert("DIV");
});

pEl.addEventListener("click", function(){
  alert("P");
});
```



##  event.target
A handler on a parent element can always get the details about where it actually happened.

**The most deeply nested element that caused the event is called a  _target_  element, accessible as  `event.target`.**

For instance, if we have a single handler  `form.onclick`, then it can “catch” all clicks inside the form. No matter where the click happened, it bubbles up to  `<form>`  and runs the handler.

In  `form.onclick`  handler:

-   `this`  (=`event.currentTarget`) is the  `<form>`  element, because the handler runs on it.
-   `event.target`  is the actual element inside the form that was clicked.

```html
<style>
form {
  background-color: green;
  position: relative;
  width: 150px;
  height: 150px;
  text-align: center;
  cursor: pointer;
}

div {
  background-color: blue;
  position: absolute;
  top: 25px;
  left: 25px;
  width: 100px;
  height: 100px;
}

p {
  background-color: red;
  position: absolute;
  top: 25px;
  left: 25px;
  width: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0;
}

body {
  line-height: 25px;
  font-size: 16px;  
}
</style>


 A click shows both <code>event.target</code> and <code>this</code> to compare:

  <form id="form">FORM
    <div>DIV
      <p>P</p>
    </div>
  </form>

<script>
form.onclick = function(event) {
  event.target.style.backgroundColor = 'yellow';

  // chrome needs some time to paint yellow
  setTimeout(() => {
    alert("target = " + event.target.tagName + ", this=" + this.tagName);
    event.target.style.backgroundColor = ''
  }, 0);
};
</script>

```


# **Conclusion :**
Event Bubbling and Event Capturing is the foundation of event handler and event delegation in JavaScript

Some of the popular properties from the  Event  type that we will use are:

1.  currentTarget
2.  target
3.  preventDefault
4.  stopPropagation
5.  type

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



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNjE2MTcyNTUsMTMxOTQzNDU0NywtOT
M4NTY0Nzg1LC0xMjU5OTQyMTk2LC0yOTA5NzU1NTMsLTIxMDc1
NzE0NjIsMjExMDQ0MTYyMyw3OTQ5MTUxMzEsMzQ0NjAxNTA5LD
QxNzQ3NjE5MywxMzYxNDYxMjI2LDEzOTU2OTQ4MSwtODgzNjgy
NzIwLDE5NTU2NDExNDgsNTUwNzcxNDg3LDExMDY5MjkxMjEsMT
EwNjkyOTEyMSwtOTE1MDM0NTk5LC0xMjQxMTI5MDU2LDQ4NjYw
MTU5OV19
-->