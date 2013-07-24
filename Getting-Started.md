### Download / File Setup

Download the processing.js file and create a new index.html file and a new sketch.js file. You want to link to pjs.js and your sketch.js file in the head of the html file.

Example index.html file:
```
<!doctype html>
<html>
  <head>
    <script src="pjs.js"></script>
    <script src="sketch.js"></script>
  </head>
  <body>
  </body>
</html>
```

Alternatively, you can [download the whole project](https://github.com/lmccart/processing-js/archive/master.zip) and copy the example folder to any location you like and edit the sketch.js file.


### Environment

You can use the code editor of your choice. Instructions for getting set up with [Sublime Text 2](http://www.sublimetext.com/) or [Light Table](www.lighttable.com) are included below.

**Getting Started with Sublime Text 2**

1. Download and install [Sublime Text 2](http://www.sublimetext.com/).
2. Open Sublime. Go to the File menu and choose Open... and choose the folder that your html and js files are located in. On the left sidebar, you should now see the folder name at the top, with a list of the files contained in the folder directly below.
3. Click on your sketch.js file and it will open on the right where you can edit it.
4. Open a web browser and type localhost/path/to/your/index.html file in the address bar to view your sketch.


**Getting Started with Light Table**

1. Download and install [Light Table](www.lighttable.com).


### Your First Sketch

[PEND: rewrite for pjs]
You're now running the Processing Development Environment (or PDE). There's not much to it; the large area is the Text Editor, and there's a row of buttons across the top; this is the toolbar. Below the editor is the Message Area, and below that is the Console. The Message Area is used for one line messages, and the Console is used for more technical details.

In your editor, type the following:
```
ellipse(50, 50, 80, 80);
```
This line of code means "draw an ellipse, with the center 50 pixels over from the left and 50 pixels down from the top, with a width and height of 80 pixels." If you are using Light Table, your sketch should automatically update. If not, refresh your page view in your browser.

If you've typed everything correctly, you'll see this appear in the Display Window:



If you didn't type it correctly, the Message Area will turn red and complain about an error. If this happens, make sure that you've copied the example code exactly: the numbers should be contained within parentheses and have commas between each of them, and the line should end with a semicolon.

One of the most difficult things about getting started with programming is that you have to be very specific about the syntax. The Processing software isn't always smart enough to know what you mean, and can be quite fussy about the placement of punctuation. You'll get used to it with a little practice.

Next, we'll skip ahead to a sketch that's a little more exciting. Delete the text from the last example, and try this:
```
var setup = function() {
  createCanvas(480, 120);
}

var draw = function() {
  if (isMousePressed()) {
    fill(0);
  } else {
    fill(255);
  }
  ellipse(mouseX, mouseY, 80, 80);
}
```
This program creates a window that is 480 pixels wide and 120 pixels high, and then starts drawing white circles at the position of the mouse. When a mouse button is pressed, the circle color changes to black. We'll explain more about the elements of this program in detail later. For now, run the code, move the mouse, and click to experience it.