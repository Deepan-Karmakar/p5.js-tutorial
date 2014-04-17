```
var link = createLink("blah blah");
// <a href="#">blah blah</a>
```

```
var button = createButton("blah blah");
// <button type="button">blah blah</button>

button.mousePressed(clicky);
var clicky = function() {
};
```

```
var input = createInput("age");
input.text("Enter your age here");
// <input type="text" name="age"></input>

input.keyPressed(typing);
var typing = function() {
};

var theusertyped = input.getText();
```

