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

### Creating other HTML elements

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

In the previous example we are just placing a text string into the element, but the element can really contain any HTML.  (See [DOM-extensions/1](https://github.com/lmccart/p5.js/tree/master/examples/tutorials/DOM-extensions/1).) Try replacing the line:
```
var text = createHTML("Here is some text and <a href='http://i.imgur.com/WXaUlrK.gif'>this is an HTML link</a>!");
```

### Creating HTML images

createHTML(html) can be used to create any HTML element, but if want to create an image specifically you can use createHTMLImage(src). In the example below we create an image and a canvas, setting the position and size for each. 

```
var img;
var canvas;

var setup = function() {

  img = createHTMLImage("http://th07.deviantart.net/fs70/PRE/i/2011/260/3/5/dash_hooray_by_rainbowcrab-d49xk0d.png");
  canvas = createGraphics(400, 400);

  img.position(190, 50);
  img.size(200, AUTO); // Use AUTO to have the height or width auto scale. 
  canvas.position(300, 50);
};

var draw = function() {

  noStroke();
  background(220, 180, 200);
  fill(180, 200, 40);
  strokeWeight(6);
  stroke(180, 100, 240);
  for (var i=0; i<width; i+=15) {
    line(i, 0, i, height);
  }

};
```
![screenshot](http://imgur.com/fqk89sj.png)


### Setting draw context

You notice that the canvas draws on top of the image. This is because createGraphics was called after createHTMLImage. But what if we want it underneath? First, flip the two create lines in setup.
```
canvas = createGraphics(400, 400);
img = createHTMLImage("http://th07.deviantart.net/fs70/PRE/i/2011/260/3/5/dash_hooray_by_rainbowcrab-d49xk0d.png");
```

Now if you run it, you probably only see the image, and if you open console to inspect you will see an error. This is because of the commands in your draw function. Your program keeps track of which element it's working with, and when you draw something (with background(), fill(), or line(), for example), it tries to draw it into the current element. By default, your program assumes whichever element you most recently created is the current element. If you create the image element second, it doesn't work to draw background and ellipse into it because drawing only works with graphics elements. 

However, in this case, we want to switch that, to tell the program to draw into the graphics element instead of the image. In order to tell the program to draw into the canvas element, use the ```context(elt)``` function in draw, passing in the pointer to the element you want to draw into. (See [DOM-extensions/2](https://github.com/lmccart/p5.js/tree/master/examples/tutorials/DOM-extensions/2).)

At the beginning of your draw function, add the line:
```
context(canvas);
```

So your full code looks like this:
```
var img;
var canvas;

var setup = function() {

  canvas = createGraphics(400, 400);
  img = createHTMLImage("http://th07.deviantart.net/fs70/PRE/i/2011/260/3/5/dash_hooray_by_rainbowcrab-d49xk0d.png");

  img.position(190, 50);
  img.size(200, AUTO);

  canvas.position(300, 50);
};


var draw = function() {

  // The program is set to draw into text because it was created last
  // but calling context tells the program to draw into canvas instead.
  context(canvas);
  noStroke();
  background(220, 180, 200);
  fill(180, 200, 40);
  strokeWeight(6);
  stroke(180, 100, 240);
  for (var i=0; i<width; i+=15) {
    line(i, 0, i, height);
  }

};
```
![screenshot](http://i.imgur.com/DKkblHb.png)


### Element specific listeners

Every elements has it's own ```mouseOver()```, ```mouseOut()``` methods that get called when you move the mouse over or off of the individual element. Each element also has a ```hide()``` and ```show()``` method. (See [DOM-extensions/3](https://github.com/lmccart/p5.js/tree/master/examples/tutorials/DOM-extensions/3).)

```
var img;
var canvas;

function setup() {
  canvas = createGraphics(400, 400);
  img = createHTMLImage("http://th07.deviantart.net/fs70/PRE/i/2011/260/3/5/dash_hooray_by_rainbowcrab-d49xk0d.png");

  img.position(190, 50);
  img.size(200, AUTO);

  canvas.position(300, 50);
  // Attach listeners for mouse events related to canvas
  canvas.mouseOver(uniHide);
  canvas.mouseOut(uniShow);
}

function draw() {
  // Tell program to draw into canvas since img was last created element.
  context(canvas);
  noStroke();
  background(220, 180, 200);
  fill(180, 200, 40);
  strokeWeight(6);
  stroke(180, 100, 240);
  for (var i=0; i<width; i+=15) {
    line(i, 0, i, height);
  }
}

// Create functions for hiding and showing uni image. These will be hooked into mouse events related to canvas above.
function uniHide() {
  img.hide();
}

function uniShow() {
  img.show();
}
```
Elements also have ```mousePressed()``` methods that let you connection functions to the mousePressed event per element. This is different than using the global ```mousePressed()``` method, which gets triggered anytime the mouse is clicked anywhere. With these element specific handlers, the function is only called when you click directly on the element. (See [DOM-extensions/4](https://github.com/lmccart/p5.js/tree/master/examples/tutorials/DOM-extensions/4).)

```
var img;
var canvas;

function setup() {
  canvas = createGraphics(400, 400);
  img = createHTMLImage("http://th07.deviantart.net/fs70/PRE/i/2011/260/3/5/dash_hooray_by_rainbowcrab-d49xk0d.png");

  img.position(190, 50);
  img.size(200, AUTO);
  // Attach listeners for mouse events related to img.
  img.mousePressed(uniHide);

  canvas.position(300, 50);
}

function draw() {
  context(canvas);
  noStroke();
  background(220, 180, 200);
  fill(180, 200, 40);
  strokeWeight(6);
  stroke(180, 100, 240);
  for (var i=0; i<width; i+=15) {
    line(i, 0, i, height);
  }
}

// Create functions for hiding and showing uni image. These will be hooked into mouse events related to canvas above.
function uniHide() {
  img.hide();
}

function uniShow() {
  img.show();
}

// Define keyPressed behavior. This one doesn't need to be hooked in, it's automatically called on key press.
function keyPressed() {
  uniShow();
}
```

### Using multiple canvases

In addition to adding other HTML elements and images, you can make more than one canvas and draw into each of them. Use context() to switch which one you are drawing to. (See [DOM-extensions/5](https://github.com/lmccart/p5.js/tree/master/examples/tutorials/DOM-extensions/5).)

```
var canvas0;
var canvas1;

function setup() {

  canvas0 = createGraphics(200, 200);
  canvas1 = createGraphics(600, 400);

  canvas0.position(50, 50);
  canvas1.position(300, 50);
}

function draw() {

  // Tell the program to draw into canvas0.
  context(canvas0);
  background(120, 180, 200);
  ellipse(width/2, height/2, 100, 100);

  // Tell the program to draw into canvas1.
  context(canvas1);
  background(50, 120, 80);
  rect(width/4, height/4, width/2, height/2);

  // Tell the program to switch back to drawing into canvas0.
  // context(canvas0);
  // line(0, 0, width, height);
}
```
![screenshot](http://i.imgur.com/k6S4Ve9.png)

It may be useful to break out the sections of code that are intended for different canvas elements into their own functions. Try switching the placement of drawRectCanvas() and drawEllipseCanvas() lines. (See [DOM-extensions/6](https://github.com/lmccart/p5.js/tree/master/examples/tutorials/DOM-extensions/6).)

```
var canvas0;
var canvas1;

function setup() {

  canvas0 = createGraphics(200, 200);
  canvas1 = createGraphics(600, 400);

  canvas0.position(50, 50);
  canvas1.position(300, 50);
}

function draw() {

  // Tell the program to draw into canvas0.
  context(canvas0);
  // Call the method to draw the contents of the canvas.
  drawEllipseCanvas();


  // Tell the program to draw into canvas1.
  context(canvas1);
  // Call the method to draw the contents of the canvas.
  drawRectCanvas();
  
}

// Additional drawing functions.
function drawEllipseCanvas() {
  background(120, 180, 200);
  ellipse(width/2, height/2, 100, 100);
}

function drawRectCanvas() {
  background(50, 120, 80);
  rect(width/4, height/4, width/2, height/2);
}
```

### Using find

You can use ```find()``` to search for all elements with a particular class or id. find() first searches for any elements whose id match the given argument, and returns an array of them. If none are found, it searches for any elements whose class match, and returns an array of them. If none are found, it returns an empty array. (See [DOM-extensions/7](https://github.com/lmccart/p5.js/tree/master/examples/tutorials/DOM-extensions/7).)

```javascript
var canvas0;
var canvas1;
var canvas2;

function setup() {

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
![screenshot](http://i.imgur.com/IeAdO2J.png)


### Setting style

You can use a ```style()``` method on any element and pass it an inline CSS string programmatically to be applied to that element. (See [DOM-extensions/8](https://github.com/lmccart/p5.js/tree/master/examples/tutorials/DOM-extensions/8).)

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
![screenshot](http://i.imgur.com/8vujAih.png)

Here are some more resources for looking up and learning about CSS:
+ [CSS basics overview](http://html.net/tutorials/css/lesson2.php)
+ [W3Schools CSS overview](http://www.w3schools.com/css/css_howto.asp)
+ [W3Schools CSS reference](http://www.w3schools.com/cssref/default.asp)
+ [HTML & CSS book](http://htmlandcssbook.com/)
  