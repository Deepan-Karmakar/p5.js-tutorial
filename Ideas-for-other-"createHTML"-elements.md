I'm working on several examples for ITP's "Creative JavaScript" class where I'm having to break into the Document object directly.

* [Button and Slider](https://github.com/lmccart/itp-creative-js/tree/master/week3/button_slider)
* [Text input](https://github.com/lmccart/itp-creative-js/tree/master/week3/wordscrambler)
* [Removing DOM elements no longer necessary](https://github.com/lmccart/itp-creative-js/tree/master/week4/11_external_API_weather2_14day_forecast)

### Links?

```
var link = createLink("blah blah");
// <a href="#">blah blah</a>
```

### Buttons?

```
var button = createButton("blah blah");
// <button type="button">blah blah</button>

button.mousePressed(clicky);
var clicky = function() {
};
```

### Input elements?

```
var input = createInput(TEXT,"age");
// <input type="text" name="age"></input>

input.text("Enter your age here");

input.keyPressed(typing);
var typing = function() {
};

var theusertyped = input.getText();
```

or

```
var input = createTextInput("age");
```

```
var range = createInput(RANGE,"size",10,100);
//<input type="range" name="size" min="10" max="100">
r val = range.getValue();
```

or

```
var range = createRange("size",10,100);
```


