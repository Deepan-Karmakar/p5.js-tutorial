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
* **You can extend p5 core functionality by adding methods to `p5.prototype`.** For example, the following code in p5.dom.js extends p5 to add a `createImg()` method that adds an HTML image element to the DOM. 

  ```javascript
  p5.prototype.createImg = function(src) {
    var elt = document.createElement('img');
    elt.src = src;
    return addElement(elt);
  };
  ```
  When the DOM library is included in a project, `createImg()` can be called just like `createCanvas()` or `background()`.

* **Use private functions for internal helpers**, functions not intended to be called by users. In the example above `addElement()` is function in p5.dom.js, it is not bound to `p5.prototype`.

* **You can extend p5.js classes as well, by adding methods to their prototypes.** In the example below, `p5.Element.prototype` is extended with the `html()` method, that sets the inner html of the element.
  ```javascript
  p5.Element.prototype.html = function(html) {
    this.elt.innerHTML = html;
  };
  ```
* **Use `registerPreloadMethod()` to register names of methods with p5 that may be called in `preload()`.** Typically, with some asynchronous functions (like loading a sound, image, or other external file), there are both synchronous and asynchronous options offered. For example, `loadStrings(path, [callback])` accepts an optional second callback argument - a function that is called after the loadStrings function completes. However, a user may also call loadStrings in `preload()` without a callback, and the p5.js will wait until everything in `preload()` completes before moving on to `setup()`. If you would like to register a method of your own call `registerPreloadMethod()` with the name of the method to register. The example below shows a line in the Sound library that registers `loadSound()`.

  ```javascript
  p5.prototype.registerPreloadMethod('loadSound');
  ```
  
* **Use `registerMethod()` to register functions with p5 that should be called at various times.** 

  ```javascript
  p5.prototype.doRemoveStuff = function() { 
  	// library cleanup stuff
  }
  p5.prototype.registerMethod('remove', p5.prototype.doRemoveStuff);
  ```

      * **remove** Called when `remove()` is called.


* **You can also create your own classes.** Your library may not extend p5 or p5 classes at all, but instead just offer extra classes that can be instantiated and used in conjunction with the library. Or it may do some mix of both.

### Naming
* **Don't overwrite p5 functions or properties.** When you are extending p5.prototype, be careful not to use the names of existing properties or functions. You can use [hasOwnProperty](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty) to test names. For example, the following line placed at the top of your library file will print true because the `rect()` method exists:

  ```javascript
  console.log(p5.prototype.hasOwnProperty('rect'));
  ```

* **Similarly, don't overwrite p5 class functions or properties.** If you are extending p5.Image, p5.Vector, p5.Element, etc, follow the same protocol as above.

* p5.js has two modes, global mode and instance mode. In global mode, all p5 properties and methods are bound to the window object, allowing users to call methods like `background()` without having to prefix it with anything. However, this means you need to be careful not to overwrite native JavaScript functionality. You can test existing JS names by typing them into console or with a quick google search.

* **Classes are typically capitalized, and methods and properties begin with lowercase.** Classes in p5 are prefixed with p5. We would like to keep this namespace for p5 core classes only, so when you create your own, **do not include the p5. prefix for class names**. You are welcome to create your own prefix, or just give them non-prefixed names.

* **p5.js library filenames are also prefixed with p5, but the next word is lowercase**, to distinguish them from classes. For example, p5.dom.js and p5.sound.js. You are encouraged to follow this format for naming your file.


### Packaging
* **Create a single JS file that contains your library.** This makes it easy for users to link it into their projects. You might also think about having options for both the normal JS file and a [minified](http://jscompress.com/) version for faster loading.

* **Contributed libraries are hosted, documented, and maintained by their creators.** This could be on github, on a separate website, or somewhere else.

* **Documentation is key!** The documentation for your library should be in some place easy to find for users that download and use your library. The documentation for contributed libraries will not be included in the main p5.js reference, but you may want to follow a similar format. See these examples of a [library overview page](http://localhost/p5js.org/site/reference/#/libraries/sound), [class overview page](http://localhost/p5js.org/site/reference/#p5.Vector), and [method page](http://localhost/p5js.org/site/reference/#p5/arc).

* **Examples are great, too!** They show people what your library can do. Because this is all JavaScript, people can see them running online before they download anything. [jsfiddle](http://jsfiddle.net/) and [codepen](http://codepen.io) are two great easy options for hosting examples.

* **Let us know!** Once your library is ready for distribution, send an email to [hello@p5js.org](mailto:hello@p5js.org) with a link and some info. We'll include it on the [libraries page](http://p5js.org/libraries/)!