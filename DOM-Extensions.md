You likely started out with p5.js drawing graphics using the HTML5 canvas, a special element you can draw graphics into. However, p5.js can also be used to create and interact with HTML elements outside of the graphics canvas.

When you call ```createGraphics(w, h)``` you create a graphics canvas to draw into with the specified width and height. However, you can also keep a pointer to this canvas by storing it in a variable. With this pointer we can call methods of the element itself, to set the position, id or class, for instance.

```javascript
function setup() {

  // We are still calling createGraphics like in the past, but now we are storing the result as a variable.
  // This way we can call methods of the element, to set the position for instance.
  var canvas = createGraphics(600, 400);

  // Here we call methods of each element to set the position and id, try changing these values.
  // Use the inspector to look at the HTML generated from this code when you load the sketch in your browser.
  text.position(50, 50);
  text.id("apple");
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
elements can have position() and id() (id is unique, only one element)
draw methods happen on whichever element was most recently created
17-1
can embed HTML within createHTML(), such as links
17-2
createHTMLImage() creates an <img>
context() tells p5.js which element to draw to
17-3
elements have mouseOver() and mouseOut() methods that let you bind functions to these events per element (these are not global now)
elements have hide() and show() methods
17-4
elements have mousePressed() methods that let you bind functions to this event per element
keyPressed() does not need to be bound, it’s global
17-5
you can make more than one canvas!
use context() to switch which one you are drawing to
17-6
you can use context() and then call custom functions
17-7
elements can have a class() (multiple elements can share a class)
var donkeys = find('donkey')
find() finds all the elements with a class and returns them into an array
17-8
just like the inline CSS we showed you last week, you can use a style() function on any element and pass it an inline CSS string programmatically




### Multiple canvases, switching contexts.

### createImage

### createElement -- links to html references.

### Modifying elements -- id, class, size, position.

### style() -- links to css references.

### Element listeners.

### Accessors