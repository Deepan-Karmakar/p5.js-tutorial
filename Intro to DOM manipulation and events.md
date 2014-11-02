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

You could type this JS code directly into console and see the result. You could also put it directly into the HTML page using the `<script>` tag. Note that this script is placed in the body of the page, rather than the head. This has to do with the order that things are loaded and run when you open a page. More on this in the [window.onload]() section.

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

In order to make your code respond to an event, you register an _event handler_, a function that is called when a particular event happens. The simplest way to do this is by setting an element's attribute for the corresponding event.

```html
<html>
  <head></head>
  <body>
    <p id="gargoyle">I <b>love</b> pandas.</p>

    <script type="text/javascript">
      var elt = document.getElementById("gargoyle");
      elt.onclick = function() {
        alert("clicked!");
      }
    </script>
  </body>
</html>
```

By assigning the "onclick" attribute of the element, an alert will be fired every time that element is clicked. You could also modify the element when the click event happens. Within an event handler function, the variable "this" is automatically assigned to the element that received the event.

```javascript
var elt = document.getElementById("gargoyle");
elt.onclick = function() {
  this.innerHTML = "I was clicked.";
  // the line above could also be written as
  // elt.innerHTML = "I was clicked.";
}
```


##Reference
* [W3Schools DOM tutorial](http://www.w3schools.com/js/js_htmldom.asp)
* [Mozilla DOM tutorial](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)