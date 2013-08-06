###Basics

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

###Supported Functions
See the [API page](https://github.com/lmccart/processing-js/blob/master/api.md) for currently supported functions from Processing, as well as new ones supported in Processing-JS.

See the [API progress page](https://github.com/lmccart/processing-js/blob/master/api-progress.md) for API progress and future support.