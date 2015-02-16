## Current DOM API documentation 
(more or less)
* https://github.com/lmccart/itp-creative-js/wiki/Week-3#html-manipulation-with-p5js
* [tutorial](https://github.com/processing/p5.js/wiki/DOM-Extensions)
* [ITP creative-js examples](https://github.com/lmccart/itp-creative-js/tree/master/week3)
* [p5.js workshop (see examples 9)](http://p5js.org/workshop/)

## Current DOM issues open

* [Fullscreen API and presentation mode](https://github.com/processing/p5.js/issues/197)
* [specifying DIV ID with global mode, remove support of canvas ID/node specification?](https://github.com/processing/p5.js/issues/201)
* [multi-argument createHTML methods](https://github.com/processing/p5.js/issues/202)
* [other create methods (see below for more notes)](https://github.com/processing/p5.js/issues/192)
* [bonzo](https://github.com/ded/bonzo)?

## Other HTML elements to address 

(From @shiffman)
I'm working on several examples for ITP's "Creative JavaScript" class where I'm having to break into the Document object directly.

* [Button and Slider](https://github.com/lmccart/itp-creative-js/tree/master/week3/button_slider)
* [Text input](https://github.com/lmccart/itp-creative-js/tree/master/week3/wordscrambler)
* [Removing DOM elements no longer necessary](https://github.com/lmccart/itp-creative-js/tree/master/week4/11_external_API_weather2_14day_forecast)

### Links?

```
var link = createLink("blah blah");
// <a href="#">blah blah</a>

// an event for when the link is clicked
button.mousePressed(clicky);

var clicky = function() {};
```

### Buttons?

```
var button = createButton("blah blah");
// <button type="button">blah blah</button>

// an event for when the button is clicked
button.mousePressed(clicky);

var clicky = function() {};
```

### Input elements?

```
var input = createInput(TEXT,"age");
// <input type="text" name="age"></input>

input.text("Enter your age here");

// An event for when the user types into the text field?
input.keyPressed(typing);

var typing = function() {};

var s = input.getInput(); // what the user has entered
```

or

```
var input = createTextInput("age");
```

```
var range = createInput(RANGE,"size",10,100);
//<input type="range" name="size" min="10" max="100">

range.moved(itmoved);  // an event for when the user changes the slider?

var itmoved = function() {};

var val = range.getValue(); // the current value of the slider
```

or

```
var range = createRange("size",10,100);
```


