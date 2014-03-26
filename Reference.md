###Basics

The p5.js language looks very similar to the Processing language with a few changes:
+ Variables do not have a type. Use var instead of float, int, double, long, char, String, Array, etc.
+ A var can be anything -- any of the types mentioned, but also functions.
+ Rather than specifying a return type for functions, they are assigned to vars. See the example below.
+ Currently, not all Processing functionality is supported in p5.js, and the syntax for a few have changed slightly. See [API](https://github.com/lmccart/p5.js/wiki/API) and [API progress](https://github.com/lmccart/p5.js/wiki/API-Progress) for up-to-date documentation of all supported functions and future plans.

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
function setup() {
  // setup stuff
}

function draw() {
  // draw stuff
}
```

###Supported functions
####[> API page](https://github.com/lmccart/p5.js/wiki/API)
Currently supported functions from Processing, as well as new ones supported in p5.js.

####[> API progress page](https://github.com/lmccart/p5.js/wiki/API-Progress)
API progress and future support.