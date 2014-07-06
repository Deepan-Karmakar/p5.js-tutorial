A p5.js library can be any JavaScript code that extends or adds to the p5.js core functionality. There are two categories of libraries. Core libraries (DOM and Sound) are part of the p5.js distribution, while contributed libraries are developed, owned, and maintained by members of the p5.js community.

###Adding a library to your project

Two libraries are included with the p5.js download, [p5.dom.js](http://localhost/p5js.org/site/reference/#/libraries/dom) and [p5.sound.js](http://localhost/p5js.org/site/reference/#/libraries/sound). Other contributed libraries can be found on the [libraries page](http://p5js.org/libraries/). 

To include a library in your sketch, link it into your HTML file, after you have linked in p5.js. An example HTML file might look like this:
```html
<head>
  <script type="text/javascript" src="p5.js"></script>
  <script type="text/javascript" src="p5.sound.js"></script>
  <script type="text/javascript" src="sketch.js"></script>
</head>

<body>
</body>
```

###Creating a new library

There are a lot of different ways to write and use JavaScript, so we leave this up to you. What follows are some notes about having your library work well with p5.js.

#### Code
* You can extend p5 core functionality by adding methods to p5.prototype. For example, the following code in p5.dom.js extends p5 to add a `createDiv()` method that adds an HTML image element to the DOM. 

  ```javascript
  p5.prototype.createImg = function(src) {
    var elt = document.createElement('img');
    elt.src = src;
    return addElement(elt);
  };
  ```

code
- extend p5
- extend p5 classes
- don't overwrite p5 functions
- don't overwrite global functions, or be clear if you do
- _registerPreloadFunc

naming
- classes no p5.
- library p5.lowercase.js

packaging
- single file
- create documentation
- create examples
