
# Phases
- capture phase
- bubbling phase(default in all modern browsers)
- target phase


![](https://www.w3.org/TR/2006/WD-DOM-Level-3-Events-20060413/images/eventflow.png)

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
  e.stopPropagation(); // 👈
});
```

later try this and see output:
```js
formEl.addEventListener("click", function(){
  alert("FORM");
});

divEl.addEventListener("click", function(e){
  alert("DIV");
  e.stopPropagation();  // 👈
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
},true); // 👈

divEl.addEventListener("click", function(){
  alert("DIV");
});

pEl.addEventListener("click", function(){
  alert("P");
});
```

Q) Which form of event propagation handles the registered container elements?  
a) Event Propagation  
b) Event Registration  
c) Event Capturing  
d) Default Actions  
View Answer

Answer: c  
Explanation: Event bubbling and capturing are two ways of event propagation in the HTML DOM API. With bubbling, the event is first captured and handled by the innermost element and then propagated to outer elements. With capturing, the event is first captured by the outermost element and propagated to the inner elements.


##  `event.target`
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
## `preventDefault`

If you’ve ever doubted how much power JavaScript gives you, try using `event.preventDefault()`! This method actually gives you the ability to _prevent a browser’s default behavior for events_.

Normally, when you click on a checkbox it’ll toggle the check. However if you use `preventDefault` it will actually stop the browser from doing that.

```html
<input  type="checkbox"  id="myCheckbox">
```

```js
let myCheckbox = document.querySelector('myCheckbox');

myCheckbox.addEventListener('click', function(e){
 e.preventDefault(); // 👈
});
```

Crazy! Just like that the browser is prevented from checking the box.
```html
  

<input  class="ctrlBehavior"  id="myCheckbox"  type="checkbox"> Check IT!<br>

<a  class="ctrlBehavior"  id="myLink"  href="https://pramodboda.com"  target="_blank">Click Pramod Boda</a><br>

<input  class="textFieldCtrlBehavior"  id="myInput"  type="text"/>
<br>

<input  class="ctrlBehavior"  id="myRadio"  type="radio"> Select!
<br>

<button  class="ctrlBehavior"  id="myBtn"  type="button">Click Me!</button>
<br>

<textarea  class="textFieldCtrlBehavior"  id="myTextarea"  name="message"  rows="10"  cols="30">
Try to change this text or Type any new text.
</textarea>
```
```js
const formElements = document.querySelectorAll('.ctrlBehavior');

const textFieldCtrlBehavior = document.querySelectorAll('.textFieldCtrlBehavior');

formElements.forEach(function(formElements){
	formElements.addEventListener('click',  function(e){
		e.preventDefault(); //👈
	});
});

textFieldCtrlBehavior.forEach(function(textFieldElements){
	textFieldElements.addEventListener('keypress',  function(e){
		e.preventDefault(); //👈
	});
});
```

Another Example:
```html
<div  class="container">
	<div  class="row">
			<div  class="col-lg-12">
			<h2><a  href="https://www.pramodboda.com"  target="_blank"  class="websiteLink">Pramod Boda</a></h2>
			<form  action="" name="signup">
				<div  class="form-group">
					<label  for="">Name</label>
					<input  type=""  class="form-control"></div>
				<div  class="form-group">
					<label  for="">Email</label>
					<input  type=""  class="form-control"></div>
				<div  class="form-check">
					<input  type="checkbox"  class="form-check-input"><label  for=""  class="form-check-label">I Agree</label>
				</div>
				<br>
				<button  class="btn btn-primary btn-block">Submit</button>
			</form>
		</div>
	</div>
</div>
```

```js
var websiteLink = document.querySelector('.websiteLink');

websiteLink.addEventListener('click', function(e){
	console.log('YOU CLICKED IT!');

	const shouldChangePage = confirm('This website might be super powerful!, do you wish to procced?');

	console.log(shouldChangePage);

	if(!shouldChangePage){
		e.preventDefault();
	}
});
```
Add this below to JS code:
```js
const signupForm = document.querySelector('[name="signup"]');

signupForm.addEventListener("submit",  function(evt)  {
	evt.preventDefault();
	console.log(evt); //👈
});
```
Update: 
```js
const signupForm = document.querySelector('[name="signup"]');

signupForm.addEventListener("submit",  function(evt)  {
	evt.preventDefault();
	console.log(evt.currentTarget); //👈
});
```





# **Conclusion :**
Event Bubbling and Event Capturing is the foundation of event handler and event delegation in JavaScript

Some of the popular properties from the  Event  type that we will use are:

1.  currentTarget
2.  target
3.  preventDefault
4.  stopPropagation
5.  type
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4MzQwOTYyMjMsNTc0MjMwNTY3LDEzNj
czMzUzMDksMjE0NzM1OTU2NCwtNjkzMDExOTEwLC00ODM5ODUw
ODEsODMyNDg5NDI1LC05NTIwMTQzNSwtMTU2MTExNDYyOCw3MD
c3NzAzODQsLTE1NjU2NjcxNDQsMTgxNjg4MTk2MSwtMjA4ODc0
NjYxMl19
-->