### Download / File Setup

Download the p5.js file and create a new index.html file and a new sketch.js file. You want to link to p5.js and your sketch.js file in the head of the html file.  Make sure all three files are in the same folder.

Example index.html file:
```
<!doctype html>
<html>
  <head>
    <script src="p5.js"></script>
    <script src="sketch.js"></script>
  </head>
  <body>
  </body>
</html>
```

Alternatively, you can [download the whole project](https://github.com/lmccart/p5.js/archive/master.zip) and copy the example folder to any location you like and edit the sketch.js file.


### Environment

You can use the code editor of your choice. Instructions for getting set up with [Sublime Text 2](http://www.sublimetext.com/) are included below.

**Getting Started with Sublime Text 2**

1. 
2. Open Sublime. Go to the File menu and choose Open... and choose the folder that your html and js files are located in. On the left sidebar, you should now see the folder name at the top, with a list of the files contained in the folder directly below.
3. Click on your sketch.js file and it will open on the right where you can edit it.

![Sublime Text](http://i.imgur.com/6eSgLGu.png)

4. Open a web browser and type localhost/path/to/your/index.html file in the address bar to view your sketch.


### Your First Sketch

In your editor, type the following:
```
function setup() {

}

function draw() {
     ellipse(50, 50, 80, 80);
}
```
This line of code means "draw an ellipse, with the center 50 pixels over from the left and 50 pixels down from the top, with a width and height of 80 pixels." 

Refresh your page view in your browser, if you've typed everything correctly, you'll see this appear in the Display Window:



If you didn't type it correctly, the Message Area will turn red and complain about an error. If this happens, make sure that you've copied the example code exactly: the numbers should be contained within parentheses and have commas between each of them, and the line should end with a semicolon.

One of the most difficult things about getting started with programming is that you have to be very specific about the syntax. The Processing software isn't always smart enough to know what you mean, and can be quite fussy about the placement of punctuation. You'll get used to it with a little practice.

Next, we'll skip ahead to a sketch that's a little more exciting. Delete the text from the last example, and try this:
```
function setup() {
  createGraphics(480, 120);
}

function draw() {
  if (isMousePressed()) {
    fill(0);
  } else {
    fill(255);
  }
  ellipse(mouseX, mouseY, 80, 80);
}
```
This program creates a window that is 480 pixels wide and 120 pixels high, and then starts drawing white circles at the position of the mouse. When a mouse button is pressed, the circle color changes to black. We'll explain more about the elements of this program in detail later. For now, run the code, move the mouse, and click to experience it.

### Getting started for Processing users

####[> Processing syntax conversion](https://github.com/lmccart/p5.js/wiki/Processing-syntax-conversion)
Learn how to convert from Processing to p5.js.

### Examples and Reference

####[> Tutorials](https://github.com/lmccart/p5.js/wiki/Tutorials)
Short, prototypical programs exploring the basics of programming with p5.js.

####[> Reference](https://github.com/lmccart/p5.js/wiki/Reference)
The functionality supported by p5.js.