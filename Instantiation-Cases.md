**Global Mode**

```javascript
// API
preload(): runs once, first
setup(): runs once, second
draw(): loops, indefinitely
createCanvas(w, h): creates a canvas element at the 0,0 with input size

// CASE 0
// No setup() and draw().
// createCanvas() gets called automatically behind the scenes and creates a default
// canvas at 0,0 with a default size and background color.
fill(255, 0, 0);
ellipse(10, 10, 50, 50);

// CASE 1
// Only setup().
// setup() runs once and createCanvas() gets called automatically with defaults.
function setup() {
  background(255, 0, 0);
  noStroke();
  ellipse(0, 0, 50, 50);
}

// CASE 2
// Only setup() and createCanvas().
// setup() runs once and createCanvas() returns a pointer to the canvas created
// with the input size, at 0,0.  Holding the pointer is optional.
function setup() {
  createCanvas(400, 400); 
  background(255, 0, 0);
  noStroke();
  ellipse(0, 0, 50, 50);
}

// CASE 3
// Only draw().
// createCanvas() is called automatically with defaults.
function draw() {
  ellipse(random(0, 400), random(0, 400), 50, 50);
}

// CASE 4
// setup() and draw() without createCanvas().
// createCanvas() is called automatically with defaults.
function setup() {
  background(255, 0, 0);
}
function draw() {
  ellipse(random(0, 400), random(0, 400), 50, 50);
}

// CASE 5
// setup() and draw() with createCanvas().
function setup() {
  createCanvas(400, 400);
  background(255, 255, 0);
}
function draw() {
  ellipse(random(0, 400), random(0, 400), 50, 50);
}

// CASE 6
// setup() and draw() with createCanvas(), holding pointer
var canvas;
function setup() {
  canvas = createCanvas(400, 400);
  canvas.position(100, 50); // allows you to set position, id, etc
  background(255, 255, 0);
}
function draw() {
  ellipse(random(0, 400), random(0, 400), 50, 50);
}

// CASE 7
// holding pointer, calling methods explicitly on that object
function setup() {
  var cnv = createCanvas(400, 400); 
  cnv.background(255, 0, 0);
  cnv.noStroke();
  cnv.ellipse(0, 0, 50, 50);
}
```

**Instance Mode**

```javascript
// CASE 0: no node specified
// Canvas is auto-generated and appended to body.
var sketch = function(p) {
  var gray = 0; 

  p.setup = function() {
    p.createCanvas(600, 400);
    p.background(gray);
  };

  p.draw = function() {
    p.rect(p.width/2, p.height/2, 200, 200);
  }

  p.mousePressed = function() {
    gray += 10;
  }
};

new p5(sketch);

// CASE 1: node specified
// Node is either a canvas element or any generic element.
// If it is a canvas, P5 will attach to it.
// If it is another type of element, a canvas with P5 attached will be inserted inside of it.
// Note that "sketch" is arbitrary and a user may replace it any variable name.

var sketch = function(p) {
  var gray = 0;

  p.setup = function() {
    p.createCanvas(600, 400);
    p.background(gray);
  };

  p.draw = function() {
    p.rect(p.width/2, p.height/2, 200, 200);
  }

  p.mousePressed = function() {
    gray += 10;
  }
};

new p5(sketch, node);
```

Note that the above is functionally equivalent to below, either may be used, but the above will be the recommended syntax for beginners as we feel it's clearer.

```javascript
p5(function(p) {
  var gray = 0;

  p.setup = function() {
    p.createCanvas(600, 400);
    p.background(gray);
  };

  p.draw = function() {
    p.rect(p.width/2, p.height/2, 200, 200);
  }

  p.mousePressed = function() {
    gray += 10;
  }
}, node);
```

Still have to think about whether to use 'new' or capitalize the constructor.
Tip from @gnarf: `function p5(opts) { if (!(this instanceof p5)) { return new p5(opts); } }`