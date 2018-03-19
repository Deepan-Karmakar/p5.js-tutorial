Until now, we've been declaring everything in the "global" context (note the global context is actually the [window object](https://developer.mozilla.org/en-US/docs/Web/API/Window)).  In p5 lingo, we refer to this as "global mode".

```javascript
var x = 100;
var y = 100;

function setup() {
  createCanvas(200,200);
}

function draw() {
  background(0);
  fill(255);
  ellipse(x,y,50,50);
}
```

While this is convenient (and friendlier) it's important to note that this can lead to problems and confusion down the road when mixing other JS libraries or trying to embed multiple p5 sketches on the same page.  A safer, more advanced methodology is to create a p5 sketch as an object "instance".  This "namespaces" your sketch under a particular variable. In other words, we'll have an object (called say `myp5`) that stores a reference to a p5 sketch.  Anything related to that sketch can therefore be called with dot syntax, i.e. `myp5.background(0);`.   This is referred to as p5 "instance mode".

The syntax for instance mode looks like the following (the sketch below is identical to the above example):

```javascript
var s = function( sketch ) {

  var x = 100; 
  var y = 100;

  sketch.setup = function() {
    sketch.createCanvas(200, 200);
  };

  sketch.draw = function() {
    sketch.background(0);
    sketch.fill(255);
    sketch.rect(x,y,50,50);
  };
};

var myp5 = new p5(s);
```

The above might seem a bit confusing, but let's break it down into smaller elements.

```
var myp5 = new p5(s);
```

This should make sense to us.  We're making a new object called `myp5` (that's our made up variable name).  We call it via constructor `new p5()`.  The code for `function p5()` can be [found in the p5.js source](https://github.com/lmccart/p5.js/blob/master/src/core/core.js#L28).  But we're not just making a "blank" sketch, we're passing in an argument called `s` that will serve as the basis for the code of that sketch. 

And what is `s`?

```javascript
var s = function( sketch ) {

};
```

`s` the seed that will spawn our p5 sketch.  It is a function that takes one argument, a `sketch` object and attaches properties to that `sketch`.   The properties are things we will need for a p5 sketch, functions like `setup()` and `draw()`.

```javascript
var s = function( sketch ) {
  sketch.setup = function() {
  };
};
```

Those functions have their own context, yet have access to anything declared around them as well.

```javascript
var s = function( sketch ) {
  var x = 100; 
  var y = 100;

  sketch.draw = function() {   // draw() is an inner function, a "closure"
    sketch.rect(x,y,50,50);    // draw() uses variables (x,y) declared in the parent function s
  };
};
```

This is what is known as a [closure](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Closures), one of the more powerful features of functional programming languages like JavaScript. 

You can think of the purpose of s as initializing everything we need for a p5 sketch. Once it's all ready to go, it's passed to the `new p5()` constructor and our variable `myp5` takes over keeping track of everything that was originally attached to the `sketch` argument.  Since `myp5` is p5 object instance (and therefore inherits everything we need from the p5 prototype), all of the stuff we wrote into sketch will work. 


## Anonymous Instance

As we've seen with JavaScript, anytime we pass a function into another function is an opportunity to declare that function anonymously.  Here is how we wrote it above.

```javascript
var s = function( sketch ) {
   // empty
};
var myp5 = new p5(s);
```

And now without a separate variable holding onto `s` for us.

```javascript
var myp5 = new p5( function( sketch ) {
  // empty
});
```

Now with everything filled in, it looks like:

```javascript
var myp5 = new p5( function( sketch ) {

  var x = 100; 
  var y = 100;

  sketch.setup = function() {
    sketch.createCanvas(200, 200);
  };

  sketch.draw = function() {
    sketch.background(0);
    sketch.fill(255);
    sketch.rect(x,y,50,50);
  };
});
```

If you find this syntax confusing, congratulations you are a human being.  Yes, less typing is involved, but for clarity, you'll see all of the examples written the slightly more long-form way.

One final note: when creating a p5 instance, you can specify a second argument (HTML element id) which acts the parent for all elements created by the sketch.  For example, let's say you have:

```html
<body>
  <div id = "p5sketch">
  </div>

  <p>Some other HTML</p>
</body>
```

You can now say:

```javascript
var myp5 = new p5(s,'p5sketch');
```

And all elements will be created inside that div.
