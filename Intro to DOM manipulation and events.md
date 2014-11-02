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


##Reference
* [W3Schools DOM tutorial](http://www.w3schools.com/js/js_htmldom.asp)
* [Mozilla DOM tutorial](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)