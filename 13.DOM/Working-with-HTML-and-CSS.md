# DOM - Working with HTML and CSS



### The DOM - Traversing and Removing Nodes

```html
<div class="myCard">
	<img class="ItemImg"  src="data:image/jpeg;base64,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"  alt="">
	<h2>Card Title</h2>
	<h3>Price: 6990/-</h3>
	<p>More description</p>

</div>
```
```css
.myCard{
	border: 1px  solid  #cccccc;
	padding: 15px;
	width: 300px;
}

.myCard .ItemImg{
	width: 100%;
}
```
```javascript
const cardEl = document.querySelector('.myCard');
console.log(cardEl);


// This are all for Elements
console.log(cardEl.children);
// HTMLCollection(4) [img.ItemImg, h2, h3, p]

console.log(cardEl.firstElementChild);
// <img class=​"ItemImg" src=​"data:​image/​jpeg;​base64,/​9j…oDtcoooDtcoooArtcooDtFFFAf/​Z" alt>​

console.log(cardEl.lastElementChild);
// <p>​More description​</p>​

console.log(cardEl.previousElementSibling);
// null

console.log(cardEl.parentElement);
// <body>​<div class=​"myCard">​…​</div>​</body>​


// This are all for Nodes
console.log(cardEl.childNodes);
// NodeList(9) [text, img.ItemImg, text, h2, text, h3, text, p, text]

console.log(cardEl.firstChild);
// #text

console.log(cardEl.lastChild);
// #text

console.log(cardEl.previousSibling);
// #text

console.log(cardEl.nextElementSibling);
// null

console.log(cardEl.parentNode);
// <body>​<div class=​"myCard">​…​</div>​</body>​
``` 

Removing Elements
```javascript
const para = document.createElement('p');
para.textContent = 'I will be removed!';
cardEl.appendChild(para);

para.remove();

// Removed, but it still exist in javascript memory.
console.log(para);
// <p>​I will be removed!​</p>​

```

## DOM Excerise
```javascript
// Make a div
const  divEl  =  document.createElement('div');

// add a class of wrapper to it
divEl.classList  =  "wrapper"

// put it into the body
document.body.appendChild(divEl);

// make an unordered list
// add three list items with the words "one, two three" in them

const  ul  =  `
<ul>
<li>one</li>
<li>two</li>
<li>three</li>
<li>four</li>
</ul>
`

// put that list into the above wrapper
divEl.innerHTML  =  ul;

// create an image
const  imgEl  =  document.createElement('IMG');

// set the source to an image
imgEl.src=  "https://images.pexels.com/photos/546819/pexels-photo-546819.jpeg?auto=compress&cs=tinysrgb&dpr=2&w=500"

// set the width to 250
imgEl.width  =  250;

// add a class of imgEl
imgEl.classList  =  imgEl;

// add an alt of Technology
imgEl.alt  =  "Technology";

// Append that image to the wrapper
divEl.appendChild(imgEl);

// with HTML string, make a div, with two paragraphs inside of it
const  content  =  `
<div class="content">
<p>Para one</p>
<p>Para two</p>
</div>
`;

// put this div before the unordered list from above
const  ulEl  =  divEl.querySelector('ul');
console.log(ulEl);

ulEl.insertAdjacentHTML("beforebegin", content);

// add a class to the second paragraph called warning
const  conetentBlock  =  divEl.querySelector('.content');

conetentBlock.children[1].classList.add('warning');

// remove the first paragraph
conetentBlock.firstElementChild.remove();

// create a function called generatePlayerCard that takes in three arguments: name, age, and height
const  generatePlayerCard  =  function(name,  age,  height){
const  html  =  `
<div class="playerCard">
<h2>${name} — ${age}</h2>
<button class="delete" type="button">&times; Delete</button>
</p>
</div>
`
return html;
}

// have that function return html that looks like this:
// <div class="playerCard">
// <h2>NAME — AGE</h2>
// <p>They are HEIGHT and AGE years old. In Dog years this person would be AGEINDOGYEARS. That would be a tall dog!</p>
// </div>

// make a new div with a class of cards
const  cardBlock=  document.createElement('div');

cardBlock.classList.add('cards');

// Have that function make 4 cards
let  cardBlockHTML  =  generatePlayerCard("Pramod",  30,  128);
cardBlockHTML  +=  generatePlayerCard("Pradeep", 31, 127);
cardBlockHTML  +=  generatePlayerCard("A. R. Rahman", 53, 125);
cardBlockHTML  +=  generatePlayerCard("Pawan Kalyan", 48, 160);

// append those cards to the div
cardBlock.innerHTML  =  cardBlockHTML;

// put the div into the DOM just before the wrapper element

divEl.insertAdjacentElement("beforebegin", cardBlock);

  

// Bonus, put a delete Button on each card so when you click it, the whole card is removed

// select all the buttons!

const  delBtn  =  document.querySelectorAll('.delete');

  

// make out delete function

const  delCardFunc  =  function(e){

const  btnThatGotClicked  =  e.currentTarget;

btnThatGotClicked.closest('.playerCard').remove();

}

// loop over them and attach a listener

let  delBtnEl;

delBtn.forEach( function(delBtnEl){delBtnEl.addEventListener("click",  delCardFunc)});
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTgxMTI5OTk4LDE3OTQ5NzU4MDcsLTExND
cwODk3NywxNjI2NDkyNjg5LC03NTY4ODE5MzksLTE3NjA5ODI0
ODYsLTE0NDk0MTQ0MDRdfQ==
-->