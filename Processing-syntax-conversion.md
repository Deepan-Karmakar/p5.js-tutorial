###Overview of changes

The Processing-JS language looks very similar to the Processing language with a few changes:
+ Variables do not have a type. Use var instead of float, int, double, long, char, String, Array, etc.
+ A var can be anything -- any of the types mentioned, but also functions.
+ Rather than specifying a return type for functions, they are assigned to vars. See the example below.

####Basic sketch

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


```java
/**
 * This example can be found in the Processing examples package.
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

###Supported functions
####[> API page](https://github.com/lmccart/processing-js/blob/master/api.md)
Currently supported functions from Processing, as well as new ones supported in Processing-JS.

####[> API progress page](https://github.com/lmccart/processing-js/blob/master/api-progress.md)
API progress and future support.