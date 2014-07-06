A p5.js library can be any JavaScript code that extends or adds to the p5.js core functionality. There are two categories of libraries. Core libraries (DOM and Sound) are part of the p5.js distribution, while contributed libraries are developed, owned, and maintained by members of the p5.js community.

##Adding a library to your project

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
##Creating a new library

There are a lot of different ways to write and use JavaScript, so we leave this up to you. What follows are some notes about having your library work well with p5.js.

###Code
* You can extend p5 core functionality by adding methods to `p5.prototype`. For example, the following code in p5.dom.js extends p5 to add a `createDiv()` method that adds an HTML image element to the DOM. 

  ```javascript
  p5.prototype.createImg = function(src) {
    var elt = document.createElement('img');
    elt.src = src;
    return addElement(elt);
  };
  ```
  When the DOM library is included in a project, `createImg()` can be called just like `createCanvas()` or `background()`.

* Use private functions for internal helpers, functions not intended to be called by users. In the example above `addElement()` is function in p5.dom.js, it is not bound to `p5.prototype`.

* You can extend p5.js classes as well, by adding methods to their prototypes. In the example below, `p5.Element.prototype` is extended with the `html()` method, that sets the inner html of the element.
  ```javascript
  p5.Element.prototype.html = function(html) {
    this.elt.innerHTML = html;
  };
  ```
* Use `_registerPreloadFunc()` to register functions with p5 that may be called in `preload()`. Typically, with some asynchronous functions (like loading a sound, image, or other external file), there are both synchronous and asynchronous options offered. For example, `loadStrings(path, [callback])` accepts an optional second callback argument - a function that is called after the loadStrings function completes. However, a user may also call loadStrings in `preload()` without a callback, and the p5.js will wait until everything in `preload()` completes before moving on to `setup()`. If you would like to register a method of your own call `_registerPreloadFunc()` with the name of the method to register. The example below shows a line in the Sound library that registers `loadSound()`.

  ```javascript
  p5.prototype._registerPreloadFunc('loadSound');
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
