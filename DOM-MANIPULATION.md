# JavaScript DOM - Manipulating HTML elements using JavaScript (Actual Programming)

HTML document is structured as a JavaScript Object. Every HTML element has different properties which can help to manipulate it. It is possible to get, create, append or remove HTML elements using JavaScript. Selecting HTML element using JavaScript is similar to selecting them using CSS. To select an HTML element, we use tag name, id, class name or other attributes.

## Getting HTML elements into JavaScript

We can access already created element(s) using JavaScript. To access or get elements we use different methods. Let us see the different methods to access the h1 elements.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Document Object Model</title>
  </head>
  <body>
    <h1 class="title" id="first-title">First Title</h1>
    <h1 class="title" id="second-title">Second Title</h1>
    <h1 class="title" id="third-title">Third Title</h1>
    <h1></h1>
  </body>
</html>
```

### Getting elements by tag name

**getElementsByTagName():** Think of _getElementsByTagName()_ as a way to find and collect all HTML elements that share the same tag name on a webpage or web project. It's like asking your browser: "Hey, find me ALL the paragraph tags" or "Get me ALL the div tags."

**How it works:**

```js
// Find all paragraph elements
const allParagraphs = document.getElementsByTagName("p");

// Find all div elements
const allDivs = document.getElementsByTagName("div");

// Find all images
const allImages = document.getElementsByTagName("img");
```

**What you get back:**

When you use _getElementsByTagName()_, you don't get a regular JavaScript array or a single element as seen in class when we console log the element we brought into JavaScript. Instead, you get something called an `HTMLCollection`. Think of it as a special container that holds HTML elements.

Here's what makes `HTMLCollection` different from regular arrays:

HTMLCollection characteristics:

- It's "array-like" - meaning it has numbered positions (indexes) and a length property
- It's "live" - if new elements are added to the page that match your search, they automatically appear in your collection
- It doesn't have all the handy array methods like forEach(), map(), for loop or filter()

**Example**

```js
const paragraphs = document.getElementsByTagName("p");

// Check how many paragraphs we found
console.log(paragraphs.length); // Shows the count

// Access individual elements using index numbers (starts at 0)
console.log(paragraphs[0]); // First paragraph
console.log(paragraphs[1]); // Second paragraph

// Loop through all paragraphs using a regular for loop
for (let i = 0; i < paragraphs.length; i++) {
  console.log(paragraphs[i].textContent);
}
```

**Real World Example**

```js
// Let's say you want to change the color of all headings
const allHeadings = document.getElementsByTagName("h2");

// Loop through and style each heading
for (let i = 0; i < allHeadings.length; i++) {
  allHeadings[i].style.color = "blue";
  allHeadings[i].style.fontSize = "24px";
}
```

### Getting elements by class name

**getElementsByClassName()**: Think of getElementsByClassName() as your way to find all HTML elements that share the same CSS class name. It's like telling your browser: "Find me ALL elements that have the class `'button'`" or "Get me ALL elements with the class `'special_icons'`."

**How it works:**

```js
// Find all elements with class "button"
const allButtons = document.getElementsByClassName("button");

// Find all elements with class "highlight"
const specialIcons = document.getElementsByClassName("special_icons");

// Find all elements with class "card"
const allCards = document.getElementsByClassName("card");
```

NB: You also get back an HTMLCollection for this method coz it's intent is to send back an array of values. For arrays in JavaScript we know now that you must loop through it

**Example**

```js
const buttons = document.getElementsByClassName("buttons");

// Check how many buttons we found
console.log(buttons.length); // returns a number (remember the length method on strings and arrays ?)

// Access individual elements using index numbers
console.log(buttons[0]); // First button
console.log(buttons[1]); // Second button

// Loop through all buttons using a regular for loop
for (let i = 0; i < buttons.length; i++) {
  console.log(buttons[i].textContent); // printing all the text content of the elements with the class "buttons" in their attributes
  buttons[i].style.backgroundColor = "blue"; // styles all of them as blue
}
```

**Real World Example 1**

```html
<div class="card">Card 1</div>
<div class="card featured">Card 2</div>
<div class="card">Card 3</div>
<p class="card">This paragraph also has card class</p>
```

```js
// This will find ALL elements with class "card" (including the paragraph)
const cards = document.getElementsByClassName("card");
console.log(cards.length); // Will show 4

// Loop through and style each card
for (let i = 0; i < cards.length; i++) {
  cards[i].style.border = "2px solid green";
  cards[i].style.padding = "10px";
}
```

**Real World Example 2**

```html
<img src="pic1.jpg" class="gallery_image" alt="Picture 1" />
<img src="pic2.jpg" class="gallery_image" alt="Picture 2" />
<img src="pic3.jpg" class="gallery_image" alt="Picture 3" />
```

```js
const galleryImages = document.getElementsByClassName("gallery_image");

// Add click event to all gallery images
for (let i = 0; i < galleryImages.length; i++) {
  galleryImages[i].addEventListener("click", function () {
    // Make clicked image bigger
    this.style.transform = "scale(1.2)";
    this.style.transition = "transform 0.3s ease";
  });
}
```

### Getting elements by ID

getElementsById() targets a single HTML element. We pass the id without `#` as an argument. As we've used in class

**Syntax**

```js
//syntax
document.getElementById("id");

let firstTitle = document.getElementById("first_title");
console.log(firstTitle); // <h1>First Title</h1>
```

### Getting elements using QuerySelectorMethods

The `document.querySelector` method can select an HTML or HTML elements by tag name, by id or by class name.

**querySelector()**: This can be used to select HTML element by its tag name, id or class. If the tag name is used it selects only the first element.

```js
let firstTitle = document.querySelector("h1"); // select the first available h1 element
let firstTitle = document.querySelector("#first_title"); // select id with first_title
let firstTitle = document.querySelector(".title"); // select the first available element with class title
```

**querySelectorAll()**: This can be used to select html elements by its tag name or class. It returns a nodeList which is an array like object which supports array methods. We can use for loop or forEach to loop through each nodeList elements.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Document Object Model</title>
  </head>
  <body>
    <h1 class="title" id="first-title">First Title</h1>
    <h1 class="title" id="second-title">Second Title</h1>
    <h1 class="title" id="third-title">Third Title</h1>
    <h1></h1>
  </body>
</html>
```

```js
const allTitles = document.querySelectorAll("h1"); // selects all the available h1 elements in the page

console.log(allTitles.length); // 4

for (let i = 0; i < allTitles.length; i++) {
  console.log(allTitles[i]);
}

allTitles.forEach((title) => console.log(title));

const allTitles = document.querySelectorAll(".title"); // the same goes for selecting using class
```

## Manipulating / changing the properties or nature of elements you targeted from your HTML

### Refresher - What are HTML attributes?

HTML attributes are like labels or properties you can add to HTML elements to give them extra information. They give extra informations about that tag or element

Common attributes include:

- `class` - for styling with CSS
- `id` - for unique identification
- `src` - for image sources
- `href` - for links
- `alt` - for image descriptions

### Method 1: Using setAttribute()

The _setAttribute()_ method is like a universal tool that can add ANY attribute to an element. It's very flexible and works with all HTML attributes.

**How setAttribute() works:**

```js
// Find all h1 elements
const titles = document.querySelectorAll("h1");

// Add a class attribute to the fourth title (index 3)
titles[3].setAttribute("class", "title");

// Add an id attribute to the same element
titles[3].setAttribute("id", "fourth_title");

// You can add any attribute this way
titles[3].setAttribute("data_category", "main_heading");
titles[3].setAttribute("title", "This is a tooltip text");
```

**setAttribute() syntax breakdown:**

```js
element.setAttribute("attribute-name", "attribute-value");
//                    ↑                 ↑
//                    attribute type/name         attribute value
``;
```

### Method 2: Direct Property Assignment (The Shortcut Way)

For some common attributes, JavaScript provides a shortcut. Instead of using setAttribute(), you can directly assign values like you're setting object properties.

```js
const titles = document.querySelectorAll("h1");

// These two lines do the same thing as setAttribute above
titles[3].className = "title"; // Same as setAttribute("class", "title")
titles[3].id = "fourth-title"; // Same as setAttribute("id", "fourth-title")

const image = document.querySelector("img");
const link = document.querySelector("a");
const input = document.querySelector("input");

// Direct property assignment
image.src = "photo.jpg";
image.alt = "A beautiful sunset";

link.href = "https://example.com";
link.target = "_blank";

input.placeholder = "Enter your name";
input.value = "Default text";
```

### ClassList

#### Adding class using add() method

The class list method is a good method to append additional class. It does not override the original class if a class exists rather it adds additional class for the element.

```js
titles[3].classList.add("title", "header-title");
```

#### Removing class using remove() method

Similar to adding we can also remove class from an element. We can remove a specific class from an element.

```js
//another way to setting an attribute: append the class, doesn't over ride
titles[3].classList.remove("title", "header-title");
```

#### Toggling using the toggle() method

We can combine the `add()` and the `remove()` method using the _toggle()_ method as it intermitently adds or remove classes from a particular element.

###
