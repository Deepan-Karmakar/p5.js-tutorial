You likely started out with p5.js drawing graphics using the HTML5 canvas, a special element you can draw graphics into. However, p5.js can also be used to create and interact with HTML elements outside of the graphics canvas.

### Storing pointers and calling methods

When you call ```createGraphics(w, h)``` you create a graphics canvas to draw into with the specified width and height. However, you can also keep a pointer to this canvas by storing it in a variable. With this pointer we can call methods of the element itself, to set the position, id or class, for instance. The position is relative to the upper left of the window. (See [DOM-extensions/0](https://github.com/lmccart/p5.js/tree/master/examples/tutorials/DOM-extensions/0).)

```javascript
var canvas;

function setup() {

  // We are still calling createGraphics like in the past, but now we are storing the result as a variable.
  // This way we can call methods of the element, to set the position for instance.
  canvas = createGraphics(600, 400);

  // Here we call methods of each element to set the position and id, try changing these values.
  // Use the inspector to look at the HTML generated from this code when you load the sketch in your browser.
  canvas.position(300, 50);
  canvas.class("lemon");

}


function draw() {

  // These commands are applied to the graphics canvas as normal.
  background(220, 180, 200);
  ellipse(width/2, height/2, 100, 100);
  ellipse(width/4, height/2, 50, 50);

}
```

In addition to ```createGraphics(w, h)```, you can also add HTML elements directly using ```createHTML(html)```, which creates a DIV on the page with the given HTML. In the example below, a DIV with text is created, in addition to the graphics canvas, and the position is set for each.

```javascript
var text;
var canvas;

function setup() {
  text = createHTML("This is an HTML string!");
  canvas = createGraphics(600, 400);
  text.position(50, 50);
  canvas.position(300, 50);
}

function draw() {
  // These commands are applied to whichever element was most recently created.
  background(220, 180, 200);
  ellipse(width/2, height/2, 100, 100);
  ellipse(width/4, height/2, 50, 50);
}
```
![screenshot](http://i.imgur.com/VqFxvTU.png)

In the previous example we are just placing a text string into the element, but the element can really contain any HTML.  (See [DOM-extensions/0](https://github.com/lmccart/p5.js/tree/master/examples/tutorials/DOM-extensions/1).) Try replacing the line:
```
var text = createHTML("Here is some text and <a href='http://i.imgur.com/WXaUlrK.gif'>this is an HTML link</a>!");
```



### Setting draw context

Try switching the order of the createHTML and createGraphics lines. You notice that it breaks when you put them the other way. This is because the most the program tries to draw into the most recently created element. If you create the HTML element second, it doesn't make work to draw background and ellipse into it because drawing only works with graphics elements. In order to tell the program to draw into the canvas element, use the ```context(elt)``` function in draw, passing in the pointer to the element you want to draw into.

```javascript
var text;
var canvas;

function setup() {
  canvas = createGraphics(600, 400);
  text = createHTML("This is an HTML string!");

  text.position(50, 50);
  canvas.position(300, 50);
}

function draw() {
  // The program is set to draw into text because it was created last
  // but calling context tells the program to draw into canvas instead.
  context(canvas);
  background(220, 180, 200);
  ellipse(width/2, height/2, 100, 100);
  ellipse(width/4, height/2, 50, 50);
}
```

### Creating HTML images
17-2
createHTMLImage() creates an <img>
context() tells p5.js which element to draw to

### Element specific listeners
17-3
elements have mouseOver() and mouseOut() methods that let you bind functions to these events per element (these are not global now)
elements have hide() and show() methods
17-4
elements have mousePressed() methods that let you bind functions to this event per element
keyPressed() does not need to be bound, it’s global

### Using multiple canvases

17-5
you can make more than one canvas!
use context() to switch which one you are drawing to
17-6
you can use context() and then call custom functions


### Using find

You can use ```find()``` to search for all elements with a particular class or id.

```javascript
// We define the canvas variables outside of setup so we can access them from anywhere in the sketch.
var canvas0;
var canvas1;
var canvas2;

function setup() {

  // We are still calling createGraphics like before, but now we are storing a pointer to each one.
  canvas0 = createGraphics(200, 200);
  canvas1 = createGraphics(200, 200);
  canvas2 = createGraphics(200, 200);

  // Here we call methods of each element to set the position and class.
  // Let's give the first two canvases class donkey, and the third class yogurt.
  canvas0.position(50, 50);
  canvas0.class('donkey');
  canvas1.position(300, 50);
  canvas1.class('donkey');
  canvas2.position(550, 50);
  canvas2.class('yogurt');
}


function draw() {

  // Tell the program to draw into canvas0.
  context(canvas0);
  background(50, 120, 80);

  // Tell the program to draw into canvas1.
  context(canvas1);
  background(120, 180, 200);

  // Tell the program to draw into canvas1.
  context(canvas2);
  background(220, 180, 200);
  
}

// On key press, hide all elements with class donkey.
function keyPressed() {
  // The find command returns an array of elements with class donkey. 
  // If none are found, it returns an empty array [].
  var donkeys = find('donkey');
  // We can then iterate through the array and hide all the elements.
  for (var i=0; i<donkeys.length; i++) {
    donkeys[i].hide();
  }
}
```


### Setting style

You can use a ```style()``` method on any element and pass it an inline CSS string programmatically to be applied to that element.

```javascript
var text;
var canvas;

function setup() {

  text = createHTML("This is an HTML string with style!");
  canvas = createGraphics(600, 400);

  text.position(50, 50);
  text.style("font-family: monospace; background-color: #FF0000; color: #FFFFFF; font-size: 18pt; padding: 10px;");
  canvas.position(150, 150);
  canvas.class("lemon");

}

function draw() {

  background(220, 180, 200);
  ellipse(width/2, height/2, 100, 100);
  ellipse(width/4, height/2, 50, 50);

}
```


Here are some more resources for looking up and learning about CSS:
+ [CSS basics overview](http://html.net/tutorials/css/lesson2.php)
+ [W3Schools CSS overview](http://www.w3schools.com/css/css_howto.asp)
+ [W3Schools CSS reference](http://www.w3schools.com/cssref/default.asp)
+ [HTML & CSS book](http://htmlandcssbook.com/)
  