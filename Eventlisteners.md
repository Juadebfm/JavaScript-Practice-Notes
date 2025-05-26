# JavaScript - Manipulating HTML elements by triggering events or actions

## Eventlisteners

Common HTML events:`onclick`, `onchange`, `onmouseover`, `onmouseout`, `onkeydown`, `onkeyup`, `onload`. We can add event listener method to any DOM object. We use `addEventListener()` method to listen to different event types on HTML elements. The addEventListener() method takes two arguments, an `event` and a `callback function`.

```js
selectedElement.addEventListener("event", function (e) {
  // the activity you want to occur after the event will be in here
});
// or

selectedElement.addEventListener("event", (e) => {
  // the activity you want to occur after the event will be in here
});
```

### Click

To attach an event listener to an element, first we select the element, then we attach the addEventListener method. The event listener takes event type and callback functions as argument.

The following is an example of click type event.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model</title>
  </head>

  <body>
    <button id="button">Click Me</button>
  </body>
</html>
```

```js
const button = document.getElementById("button");

button.addEventListener("click", (e) => {
  console.log("e gives the event listener object:", e);

  console.log("e.target gives the selected element: ", e.target);

  console.log(
    "e.target.textContent gives content of selected element: ",
    e.target.textContent
  );
});
```

**NB: An event can be also attached directly to the HTML element as inline script.**

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model</title>
  </head>

  <body>
    <button onclick="clickMe()">Click Me</button>
  </body>
</html>
```

```js
const clickMe = () => {
  alert("We can attach event on HTML element");
};
```

### Examples of other events

- `click` - when the element clicked
- `dblclick` - when the element double clicked
- `mouseenter` - when the mouse point enter to the element
- `mouseleave` - when the mouse pointer leave the element
- `mousemove` - when the mouse pointer move on the element
- `mouseover` - when the mouse pointer move on the element
- `mouseout` -when the mouse pointer out from the element
- `input` -when value enter to input field
- `change` -when value change on input field
- `blur` -when the element is not focused
- `keydown` - when a key is down
- `keyup` - when a key is up
- `keypress` - when we press any key
- `onload` - when the browser has finished loading a page

### Getting value from an input element

We usually fill forms and inputs inside forms and forms accept data. Form fields are created using input HTML element.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model</title>
  </head>

  <body>
    <h1>Data Binding using input or change event</h1>

    <input type="text" placeholder="say something" />
    <p></p>

    <script>
      const input = document.querySelector("input");
      const p = document.querySelector("p");

      input.addEventListener("input", (e) => {
        p.textContent = e.target.value;
      });
    </script>
  </body>
</html>
```

### keypress, keydow and keyup

We can access all the key numbers of the keyboard using different event listener types. Let us use keypress and get the keyCode of each keyboard keys.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model:30 Days Of JavaScript</title>
  </head>

  <body>
    <h1 id="keyPressed">Key events: Press any key</h1>

    <script>
        const keyPressed = document.getElementById("keyPressed")
      document.body.addEventListener("keypress", (e) => {
    keyPressed.textContent=e.target.value
      });
    </script>
  </body>
</html>
```
