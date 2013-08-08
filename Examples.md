Examples coming soonish.

### Goal: 10+ examples demonstrating:
+ Basic graphics drawing in canvas (translating from current processing to js version).
+ Drawing with multiple canvases.
+ Creating additional DOM elements (createElement, createImage).
+ Handling input for multiple elements, attaching listeners.
+ Setting style (with links to good CSS references).
+ Mixing in native JS and including other libraries (with links to good JS references).
+ Console / debugging, how to print and inspect an object.


#### Basic Processing
1. Basic structure

##### Statements and Comments

    var setup = function(){
      // The size function is a statement that tells the computer 
      // how large to make the window.
      // Each function statement has zero or more parameters. 
      // Parameters are data passed into the function
      // and are used as values for telling the computer what to do.
      createCanvas(640, 360);
    }

    var draw = function(){
      // The background function is a statement that tells the computer
      // which color (or gray value) to make the background of the display window 
      background(204, 153, 0);
    }

![Statement and Comments](http://i.imgur.com/x1evK7y.png)



2. Form
3. Data
4. Arrays
5. Control
6. Image
7. Shape
8. Color
9. Math
10. Input
11. Transform

#### Using the rest of the DOM
12. Multiple canvases, switching contexts.
13. createImage
14. createElement -- links to html references.
15. Modifying elements -- id, class, size, position.
16. style() -- links to css references.
17. Element specific input.
18. Accessors