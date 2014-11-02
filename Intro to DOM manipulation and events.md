##The Document Object Model (DOM)

The Document Object Model (DOM) is a programming interface for HTML documents. Meaning, it provides a way to use code (JavaScript, for example) to access and modify the structure, style, and content of an HTML page.

In the DOM, all HTML elements are defined as objects. Each of these objects has a set of properties and methods. A property is a value that you can get or set (like changing the content of an HTML element). A method is an action you can do (like add or deleting an HTML element). A few of the most common methods and properties follow.

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

##Reference
* [W3Schools DOM tutorial](http://www.w3schools.com/js/js_htmldom.asp)
* [Mozilla DOM tutorial](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)