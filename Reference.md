###Basics

The Processing-JS language looks very similar to the Processing language with a few changes:
+ Variables do not have a type. Use var instead of float, int, double, long, char, String, Array, etc.
+ A var can be anything -- any of the types mentioned, but also functions.
+ Rather than specifying a return type for functions, they are assigned to vars. See the example below.
+ Currently, not all Processing functionality is supported in Processing-JS, and the syntax for a few have changed slightly. See [API](https://github.com/lmccart/processing-js/blob/master/api.md) and [API progress](https://github.com/lmccart/processing-js/blob/master/api-progress.md) for up-to-date documentation of all supported functions and future plans.

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

###Supported functions
####[> API page](https://github.com/lmccart/processing-js/blob/master/api.md)
Currently supported functions from Processing, as well as new ones supported in Processing-JS.

####[> API progress page](https://github.com/lmccart/processing-js/blob/master/api-progress.md)
API progress and future support.