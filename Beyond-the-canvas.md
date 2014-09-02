**This tutorial is not entirely up to date, though it will be soon! The best place to look right now is the [p5.dom library reference page](http://p5js.org/reference/#/libraries/p5.dom).**

As you have seen, createCanvas creates an HTML5 Canvas, a special element you can draw graphics into. However, using the p5.dom add-on library, p5.js can also be used to create and interact with HTML elements outside of the graphics canvas. This tutorial will explain more about how to use p5.dom.

First, you will need to include the p5.dom.js file in your html. If you are using the example project it should already be there, you just need to uncomment the line in index.html that links to it. Otherwise, [download](https://github.com/lmccart/p5.js/blob/master/lib/addons/p5.dom.js) the file and add this line to your HTML header:

```html
<script type='text/javascript' src='relative/path/to/your/p5.dom.js'>
```

## Storing pointers and calling methods

When you call ```createCanvas(w, h)``` you create a graphics canvas to draw into with the specified width and height. However, you can also store the canvas you create in a variable, this is called a pointer. With this pointer we can call methods of the element itself, to set the position, id or class, for instance. 

```javascript
var canvas;

function setup() {

  // We are still calling createCanvas like in the past, but now we are storing the result as a variable.
  // This way we can call methods of the element, to set the position for instance.
  canvas = createCanvas(600, 400);

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

### Using .parent()

When a new element is added using one of the create methods (either a canvas, div, img, etc), you may notice that it doesn't show up in the upper left corner (0,0), but instead appends to the end of the page. The elements are also affected by any existing CSS styling you may have set for the page. The guiding idea here is that p5 does as little as possible to mess with your page, so elements follow the flow of the page rather than disrupting anything. Then, if you'd like to arrange things differently, you can use p5 methods or CSS styling.

If you would like to specify a location for the element, rather than appending directly to the end, you can use the `.parent()` method. In the `<body>` of your html file, create a container where you would like your canvas to get inserted, with ID of your choice:

```html
<div id='myContainer'></div>
```

Then use a variable to store a pointer to the element you created, and call `.parent()` on this variable:

```javascript
function setup() {
  var myCanvas = createCanvas(600, 400);
  myCanvas.parent('myContainer');
}
```


### Using .position()

Maybe you don't care which div container your elements end up in, but just want to set their position on the page. In this case you could use `.position(x, y)`. Calling this method overrides the default positioning of the element (by applying a CSS style `position:absolute`), allowing you to give it a position relative to the upper left of the window (0,0). The example below creates a div element and positions it at (100,100).

```javascript
function setup() {
  var myCanvas = createCanvas(600, 400);
  myCanvas.position(100, 100);
}
```

Note that the examples above refer to createCanvas(), but they work the same for any of the createXX() methods.


## Creating other HTML elements

In addition to ```createCanvas(w, h)```, there are a number of other methods like `createDiv()`, `createP()`, `createA()`, etc (see the [reference](http://p5js.org/reference/#/libraries/p5.dom) for full listing). In the example below, a div with text is created, in addition to the graphics canvas, and the position is set for each.

```javascript
var text;
var canvas;

function setup() {
  text = createDiv("This is an HTML string!");
  canvas = createCanvas(600, 400);
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

In the previous example we are just placing a text string into the element, but the element can really contain any HTML. Try replacing this line and notice how some of the text becomes clickable.

```javascript
var text = createDiv("Here is some text and <a href='http://i.imgur.com/WXaUlrK.gif'>this is an HTML link</a>!");
```

## Creating HTML images

If want to create an image specifically you can use createImg(src). An HTML image differs from one drawn in the canvas using `image()`. You don't need to use `loadImage()`, and you don't need to draw it every frame; once you create it, the image exists on the page until you remove it. Also note that this image is a single element in itself, and if you drag your mouse over it you will notice that it's highlightable. This means that you can attach handlers for mouse events directly to this element, but more on that later. In the example below we create an image and a canvas, setting the position and size for each. 

```
var img;
var canvas;

function setup() {

  img = createImg("http://th07.deviantart.net/fs70/PRE/i/2011/260/3/5/dash_hooray_by_rainbowcrab-d49xk0d.png");
  canvas = createCanvas(400, 400);

  img.position(190, 50);
  img.size(200, AUTO); // Use AUTO to have the height or width auto scale. 
  canvas.position(300, 50);
}

function draw() {
  noStroke();
  background(220, 180, 200);
  fill(180, 200, 40);
  strokeWeight(6);
  stroke(180, 100, 240);
  for (var i=0; i<width; i+=15) {
    line(i, 0, i, height);
  }
}
```
![screenshot](http://imgur.com/fqk89sj.png)


## Creating HTML media elements



## Using createElement()

The [p5.dom API](http://p5js.org/reference/#/libraries/p5.dom) supports a subset of all the HTML elements possible. If you'd like to add an element that does not have a specific create method, you can use the general `createElement()` method. The first argument to createElement is the tag name, and the second, optional argument is the content to be placed within the element. In the example before, an H1 heading element is created.

```
var h1;
var canvas;

function setup() {
  h1 = createElement('h1', 'this is some heading text');
  canvas = createCanvas(400, 400);
}
```

See [this page](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5/HTML5_element_list) for a full list of HTML elements you can create.


## Element specific listeners

Every elements has it's own `mouseOver()`, `mouseOut()` methods that get called when you move the mouse over or off of the individual element. To program a specific action to happen when one of these events occurs, you pass in either a function or the name of a function as the argument to these methods. 

In the example below, we are attaching a behavior that hides the uniforn image when you mouse over the canvas, and shows it again when you mouse out (off of) the canvas.

```javascript
var img;
var canvas;

function setup() {
  canvas = createCanvas(400, 400);
  img = createImg("http://th07.deviantart.net/fs70/PRE/i/2011/260/3/5/dash_hooray_by_rainbowcrab-d49xk0d.png");

  img.position(190, 50);
  img.size(200, AUTO);

  canvas.position(300, 50);
  // Attach listeners for mouse events related to canvas
  canvas.mouseOver(uniHide);
  canvas.mouseOut(uniShow);
}

function draw() {
  // All drawing happens in the canvas.
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

In the example above, we pass in the function names uniHide and uniShow. You could achieve the same result by passing in a whole function without a name, this nameless function is known as an "anonymous function".

```javascript
canvas.mouseOver(function() {
	img.hide();
})
```

###Element vs global listeners

Elements also have `mousePressed()` methods that let you connect functions to the mousePressed event on a per element level. Important: this is different than using the global `mousePressed()` method, which gets triggered anytime the mouse is clicked anywhere. With these element specific handlers, the function is __only__ called when you click directly on the element.

```javascript
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

// Create functions for hiding and showing uni image. 
// These will be hooked into mouse events related to canvas above.
function uniHide() {
  img.hide();
}

function uniShow() {
  img.show();
}

// Define global keyPressed behavior. This one doesn't need to be hooked in, it's a global listener, automatically fired on key press.
function keyPressed() {
  uniShow();
}
```

Here is one more example illustrating the difference between global and element specific listeners. In this example, every click on the page anywhere makes the background lighter. However, only clicks directly on the canvas change the size of the ellipse.

```javascript
var gray = 0;
var diameter = 5;

function setup(){
  var canvas = 	createCanvas(200, 200);
  canvas.mousePressed(incDiameter);
}

function draw() {
  background(gray);
  ellipse(width/2, height/2, diameter, diameter);
}

function mousePressed() {
  gray = gray + 10;
}

function incDiameter() {
	diameter = diameter + 5;
}

```


Here are some more resources for looking up and learning about CSS:
+ [CSS basics overview](http://html.net/tutorials/css/lesson2.php)
+ [W3Schools CSS overview](http://www.w3schools.com/css/css_howto.asp)
+ [W3Schools CSS reference](http://www.w3schools.com/cssref/default.asp)
+ [HTML & CSS book](http://htmlandcssbook.com/)
  