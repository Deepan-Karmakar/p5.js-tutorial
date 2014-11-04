This tutorial provides a general overview to HTML and CSS, no p5.js involved. If you'd like to use the p5.dom library to do some of these things, check out the [beyond the canvas](https://github.com/lmccart/p5.js/wiki/Beyond-the-canvas) tutorial.

#The Document Object Model (DOM)

The Document Object Model (DOM) is a programming interface for HTML documents. Meaning, it provides a way to use code (JavaScript, for example) to access and modify the structure, style, and content of an HTML page.

In the DOM, all HTML elements are defined as objects. Each of these objects has a set of properties and methods. A property is a value that you can get or set (like changing the content of an HTML element). A method is an action you can do (like add or deleting an HTML element). A few of the most common methods and properties follow.

##Accessing elements

###getElementById()

The getElementById method returns the element on the page with the given id. In the example below, we place a paragraph on the HTML page and give it id "gargoyle". The JS code below searches the page for an element with id "gargoyle", stores it in the variable `elt`, and then prints in to console. `getElementById` is a method of `document`, which is the variable that represents the HTML page.

```html
<html>
  <head></head>
  <body>
    <p id="gargoyle"></p>
  </body>
</html>
```

```javascript
var elt = document.getElementById("gargoyle");
console.log(elt);
```

You could type this JS code directly into console and see the result. You could also put it directly into the HTML page using the `<script>` tag. Note that this script is placed in the body of the page, rather than the head. This has to do with the order that things are loaded and run when you open a page. More on this in the [load event](https://github.com/lmccart/p5.js/wiki/Intro-to-DOM-manipulation-and-events#load) section.

```html
<html>
  <head></head>
  <body>
    <p id="gargoyle"></p>

    <script type="text/javascript">
      var elt = document.getElementById("gargoyle");
      console.log(elt);
    </script>
  </body>
</html>
```

###getElementsByClassName(), getElementsByTagName()

getElementsByClassName and getElementsByTagName work very similar to getElementById except both return an array of elements instead of just one element. getElementsByClassName returns an array of all elements with the given class, getElementsByTagName returns an array of all elements with given tag. With either method, if none are found, an empty array ([]) is returned.

```html
<html>
  <head></head>
  <body>
    <div class="orange"></div>
    <div class="sponge"></div>
    <script type="text/javascript">
      var elt1 = document.getElementsByClassName("orange");
      console.log(elt1); // returns an array with one element
      var elt2 = document.getElementsByTagName("div");
      console.log(elt2); // returns an array with two elements
    </script>
  </body>
</html>
```

##Modifying elements

###innerHTML

The innerHTML property is a pointer to the HTML content within a particular element, allowing you to easily access or change the content. The example below is similar to the previous one, but it prints the HTML within the element.

```html
<html>
  <head></head>
  <body>
    <p id="gargoyle">I <b>love</b> pandas.</p>

    <script type="text/javascript">
      var elt = document.getElementById("gargoyle");
      console.log(elt.innerHTML); // I <b>love</b> pandas.
    </script>
  </body>
</html>
```

You can also change the content within the element, by setting the innerHTML property equal to some new value.

```javascript
var elt = document.getElementById("gargoyle");
elt.innerHTML = "Veggie burgers are<br>so tasty.";
```

#Events

Many JS applications perform _actions_ as a response to _events_. An event is a signal from the browser that something has happened. There are several different types of events:

1. DOM events, which are initiated by DOM-elements. For example, a "click" event happens when an element is clicked, a "mouseover" event happens when a mouse pointer comes over an element.
2. Window events. For example, a "resize" event happens when a browser window is resized.
3. Other events, like "load", "readystatechange". They are used in AJAX and for other needs.

##Registering an event handler

In order to make your code respond to an event, you register an _event handler_, a function that is called when a particular event happens. To do this you can use the `addEventListener(event, fxn)` function. This function takes two arguments - the name of the event to listen for, and the name of the function that gets called when the event happens (no quotes around the name, you are passing the variable pointing to the function).

The basic form is like this:

```javascript
functionToRun() {
  // code to execute
}		

element.addEventListener('event name', functionToRun);
```

Here is a working example:

```html
<html>
  <head></head>
  <body>
    <p id="gargoyle">I <b>love</b> pandas.</p>

    <script type="text/javascript">
      // define a function that can be called
      function doSomething() {
        alert("clicked!");
      }

      // grab the element you want to attach the event to
      var elt = document.getElementById("gargoyle");

      // attach the function for chosen event
      elt.addEventListener("click", doSomething);
    </script>
  </body>
</html>
```

In the example above, the `doSomething()` function will be called or "fired" every time a click event happens on that element. So every time you click on the paragraph with id "gargoyle", an alert will appear. 

##Using this

You could also modify the element when the click event happens. Within an event handler function, the variable "this" is automatically assigned to the element that received the event.

```javascript
function doSomething() {
  this.innerHTML = "I was clicked.";
  // the line above could also be written as
  // elt.innerHTML = "I was clicked.";
}

var elt = document.getElementById("gargoyle");
elt.addEventListener("click", doSomething);
```

##Input events

There are a lot of different input events detected by the browser, you can see a full list on [Mozilla event reference](https://developer.mozilla.org/en-US/docs/Web/Events). Some useful ones include:

* __mouse__ - mousedown, mousemove, mouseup, mouseover, mouseout, mousewheel
* __touch__ - touchstart, touchmove, touchend, touchenter, touchleave
* __keyboard__ - keydown, keypress, keyup

The example below attaches listeners for `mouseover` and `mouseout` to a single element.

```javascript
function showHello() {
  this.innerHTML = "hi there!";
}

function showGoodbye() {
  this.innerHTML = "goodbye :(";
}

var elt = document.getElementById("gargoyle");
elt.addEventListener("mouseover", showHello);
elt.addEventListener("mouseout", showGoodbye);
```

##Window events

All of the events so far have been element specific, that is, you attach them to a single element, and they are fired only when that element receives the event. There are also some events that happen on a global window level, two examples are `resize` and `load`. In this case, you say `window.` instead of `element.`.

###resize

The resize event happens when the browser window is resized.

```javascript
function doSomething() {
  // in this case, "this" doesn't point to an element
  // "this" refers to the window since that's where
  // the event occurred, so we have to grab it to use it
  var elt = document.getElementById("gargoyle");
  elt.innerHTML("I've been resized!");
}

window.addEventListener("resize", doSomething);
```

###load

The load event happens when the HTML page has fully loaded. It is a way to specify what to do when a document is done loading, it also signifies when it is safe to call elements on the DOM.

```javascript
function init() {
  var elt = document.getElementById('mydiv');
  alert(elt.innerHTML);
}				
window.addEventListener('load', init);			
```

Some of the examples above show some JS code in the body of the HTML. This is another way of ensuring the page loads before the JS starts to act on it, but it's not ideal. It's cleaner to have the JS code in the head of the HTML file (or in a separate JS file linked in the head). So the better way to do things is to use the load event.	

Converting this example from above:

```html
<html>
  <head></head>
  <body>
    <p id="gargoyle">I <b>love</b> pandas.</p>

    <script type="text/javascript">
      var elt = document.getElementById("gargoyle");
      console.log(elt.innerHTML);
    </script>
  </body>
</html>
```

The JS code gets wrapped in a function called init (or whatever you like), and added as the event handler for the load event using addEventListener:

```html
<html>
  <head>
    <script type="text/javascript">
      function init() {
        var elt = document.getElementById("gargoyle");
        console.log(elt.innerHTML);
      }
      window.addEventListener("load", init);
    </script>
  </head>
  <body>
    <p id="gargoyle">I <b>love</b> pandas.</p>
  </body>
</html>
```

Note that if you didn't add the function wrapper and event listener and just moved the code from the body to the head of the HTML file, it would run too soon, and the console.log message would be empty.

##Reference

__General__

* [W3Schools DOM tutorial](http://www.w3schools.com/js/js_htmldom.asp)
* [Mozilla DOM tutorial](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)

__p5.js__

* [DOM manipulation with p5.js](https://github.com/lmccart/p5.js/wiki/Beyond-the-canvas#element-specific-listeners)
* [event listeners with p5.js](https://github.com/lmccart/p5.js/wiki/Beyond-the-canvas#element-specific-listeners)