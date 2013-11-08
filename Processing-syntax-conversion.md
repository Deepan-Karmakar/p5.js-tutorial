###Overview of changes

The Processing-JS language looks very similar to the Processing language with a few changes:
+ Variables do not have a type. Use var instead of float, int, double, long, char, String, Array, etc.
+ A var can be anything -- any of the types mentioned, but also functions.
+ Rather than specifying a return type for functions, they are assigned to vars. See the example below.
+ Currently, not all Processing functionality is supported in Processing-JS, and the syntax for a few have changed slightly. See [API](https://github.com/lmccart/processing-js/blob/master/api.md) and [API progress](https://github.com/lmccart/processing-js/blob/master/api-progress.md) for up-to-date documentation of all supported functions and future plans.

###Conversion examples

####Basic sketch

This is the basic setup for a Processing and Processing-JS sketch. Note that Processing-JS will also require an empty HTML file that links to the Processing-JS library and your sketch file in the header (see [getting started](https://github.com/lmccart/processing-js/wiki/Getting-Started)).

```java
void setup() {
  // setup stuff
}

void draw() {
  // draw stuff
}
```


```javascript
var setup = function() {
  // setup stuff
};

var draw = function() {
  // draw stuff
};
```

####Converting a Processing sketch to Processing-JS

Here are two examples of sketches that have been converted from Processing to Processing-JS. The changes made are shown in the comments, all the other lines remained the same.

```javascript
/**
 * This example can be found in the Processing examples package
 * that comes with the Processing PDE.
 * Processing > Examples > Basics > Form > Bezier
 * Adapted by Evelyn Eastmond
 */

var setup = function() {     // **change** void setup() to var setup = function()
  createGraphics(640, 360);  // **change** size() to createGraphics()
  stroke(255);               // stroke() is the same
  noFill();                  // noFill() is the same
}

var draw = function() {                   // **change** void draw() to var setup = draw()
  background(0);                          // background() is the same
  for (var i = 0; i < 200; i += 20) {     // **change** int i to var i
    bezier(mouseX-(i/2.0), 40+i, 410, 20, 440, 300, 240-(i/16.0), 300+(i/8.0)); // bezier() is the same
  }
}

```

```javascript

/**
 * This example can be found in the Processing examples package
 * that comes with the Processing PDE.
 * Processing > Examples > Basics > Form > Bezier
 * Adapted by Evelyn Eastmond
 */

var x = [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0];  // **change** float[] x = new float[20] to array of 20 0's
var y = [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0];  // **change** float[] y = new float[20] to array of 20 0's
var segLength = 18;                                 // **change** float to var

var setup = function() {                    // **change** void setup() to var setup = function()
  createGraphics(640, 360);                 // **change** size() to createGrphics()
  strokeWeight(9);                          // strokeWeight() is the same
  stroke(255, 100);                         // stroke() is the same
}

var draw = function() {                     // **change** void draw() to var draw = function()
  background(0);                            // background() is the same
  dragSegment(0, mouseX, mouseY);           // functions calls, mouseX and mouseY are the same
  for(var i=0; i<x.length-1; i++) {         // **change** int i to var i
    dragSegment(i+1, x[i], y[i]);           // function calls are the same
  }
}

var dragSegment = function(i, xin, yin) {   // **change** void drawSegment() to var drawSegment() = function, remove type declarations
  var dx = xin - x[i];                      // **change** float to var
  var dy = yin - y[i];                      // **change** float to var
  var angle = atan2(dy, dx);                // **change** float to var, atan2() is the same
  x[i] = xin - cos(angle) * segLength;      // cos() is the same
  y[i] = yin - sin(angle) * segLength;      // sin() is the same
  segment(x[i], y[i], angle);               // function calls are the same
}

var segment = function(x, y, a) {           // **change** void segment() to var segment = function(), remove type declarations
  pushMatrix();                             // pushMatrix() is the same
  translate(x, y);                          // translate() is the same
  rotate(a);                                // rotate() is the same
  line(0, 0, segLength, 0);                 // line() is the same
  popMatrix();                              // popMatrix() is the same
}
```

####Converting a Processing-JS sketch to Processing

Here are two examples of sketches that have been converted from Processing-JS to Processing. The changes made are shown in the comments, all the other lines remained the same.

```java
/**
 * This example can be found in the Processing examples package
 * that comes with the Processing PDE.
 * Processing > Examples > Basics > Form > Bezier
 */

void setup() {                         // **change** var setup = function() to void setup()
  size(640, 360);                      // **change** createGraphics() to size()
  stroke(255);
  noFill();
}

void draw() {                          // **change** var setup = draw() to void draw()
  background(0);
  for (int i = 0; i < 200; i += 20) {  // **change** var i to int i
    bezier(mouseX-(i/2.0), 40+i, 410, 20, 440, 300, 240-(i/16.0), 300+(i/8.0));
  }
}
```

```java
/**
 * This example can be found in the Processing examples package
 * that comes with the Processing PDE.
 * Processing > Examples > Topics > Interaction > Follow3
 * Based on code from Keith Peters. 
 */

float[] x = new float[20];                       // **change** array of 0's to be float[] x = new float[20]
float[] y = new float[20];                       // **change** array of 0's to be float[] x = new float[20]
float segLength = 18;                            // **change** var to float

void setup() {                                   // **change** var setup = function() to void setup() 
  size(640, 360);                                // **change** createGraphics() to size()
  strokeWeight(9);
  stroke(255, 100);
}

void draw() {                                    // **change** var draw = function() void draw()
  background(0);
  dragSegment(0, mouseX, mouseY);
  for(int i=0; i<x.length-1; i++) {              // **change** int i to var i
    dragSegment(i+1, x[i], y[i]);
  }
}

void dragSegment(int i, float xin, float yin) {  // **change** var drawSegment() = function to void drawSegment(). add type delcarations.
  float dx = xin - x[i];                         // **change** var to float
  float dy = yin - y[i];                         // **change** var to float
  float angle = atan2(dy, dx);                   // **change** var to float
  x[i] = xin - cos(angle) * segLength;
  y[i] = yin - sin(angle) * segLength;
  segment(x[i], y[i], angle);
}

void segment(float x, float y, float a) {        // **change** var segment = function() to void segment(). add type delcarations.
  pushMatrix();
  translate(x, y);
  rotate(a);
  line(0, 0, segLength, 0);
  popMatrix();
}
```

####About variables

In Processing-JS, all variables (whether they are numbers, strings, arrays, functions, objects, whatever!) are declared using the symbol "var". In Processing, you must specify the variable type. Here is a summary of the supported Processing data types (table borrowed from [Getting Started with Processing](http://shop.oreilly.com/product/0636920000570.do)).

Name | Description | Range of values
--- | --- | ---
int | Integers (whole numbers) | -2,147,483,648 to 2,147,483,647
float | Floating-point values | -3.40282347E+38 to 3.40282347E+38
boolean | Logical value | true or false
char | Single character | A-z, 0-9, and symbols
String | Sequence of characters | Any letter, word, sentence, and so on
PImage | PNG, JPG, or GIF image | N/A
PFont | VLW font; use the Create Font tool to make | N/A
PShape | SVG file | N/A


###Supported functions

Currently, not all Processing functionality is supported in Processing-JS, and the syntax for a few have changed slightly, refer to the API pages for further documentation.

####[> API page](https://github.com/lmccart/processing-js/blob/master/api.md)
Currently supported functions from Processing, as well as new ones supported in Processing-JS.

####[> API progress page](https://github.com/lmccart/processing-js/blob/master/api-progress.md)
API progress and future support.