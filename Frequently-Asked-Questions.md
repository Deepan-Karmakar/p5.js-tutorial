#Goals

###How is this different than Processing.js?

The main goal of Processing.js is to execute Processing files in HTML5, but not necessarily to write native HTML5. It supports a mixed syntax of Processing and JavaScript, where the JavaScript is not really meant to be consumed by the end-user. Processing.js is a port of Processing to JS, using regex to convert Java into JS. It is a good tool for those that want to run simple sketches on the web, however, it is quite opaque. It can be difficult for someone to understand how it works, how to fix things when it doesn't work, or how to modify or extend the library. As Processing.js says on their website, "it's not magic, but almost."

In contrast, with p5 we are reimagining Processing's original goals in native JavaScript, in a way that is intended to be transparent and intuitive. It is easy to translate a sketch from Processing to p5 and the process of doing so begins to teach people the basics of JS. From there, they are able to begin writing native JS using a syntax that feels familiar but appropriate for the context. We are closely studying the decisions Processing has made, but also always questioning to see if there are design decisions that would make the library cleaner, stronger, and more intuitive. 

Additionally, p5.js extends beyond canvas drawing to allow people to create, access and manipulate other HTML elements. Through this framework beginners begin to explore and understand HTML, JavaScript, and CSS, and the way they work together in the browser. p5.js will also have a system for people to contribute addon modules to deal with things like audio, video, various input devices, and data. There is also an option to use p5 globally or instantiated within a namespace, so it can be compatible with other JS libraries. 

Most importantly, this project is in active development, with enthusiastic support and contributions from around the world. We have begun working with various schools and institutions to teach workshops and classes, in hopes of integrating it into curricula as a tool for understanding the web.

We are also putting a lot of energy into making the documentation clear, for developers as well as users. We'd like this to be a project that anyone feels welcome and empowered to be a part of, whether that's contributing documentation, writing code, teaching with it, or using it to create.


### How did this project originate?

This project developed out of a Fellowship with the Processing Foundation exploring the future of Processing with JavaScript. Documentation of research in process and references is [here](https://github.com/processing/p5.js/wiki/Research-Documentation).

# Programming questions

### Do all the variables have to be in the global namespace? Can I run multiple sketches on one page?

By default, all p5.js functions are in the global namespace (i.e. bound to the window object), meaning you can call them simply `ellipse()`, `fill()`, etc. However, this might be inconvenient if you are mixing with other JS libraries or writing long programs of your own. To solve this problem, there is something we call "instance mode", where all p5 functions are bound up in a single variable instead of polluting your global namespace. [See more info here.](https://github.com/processing/p5.js/wiki/p5.js-overview#instantiation--namespace)

### Why can't I assign variables using p5 functions and variables before `setup()`?

Well, technically, you can by using on-demand global mode. But that's a less common use of p5, so we'll explain that later and talk about the more common case first. In regular global mode, p5 variable and function names are not available outside `setup()`, `draw()`, `mousePressed()`, etc. (Except in the case where they are placed inside functions that are called by one of these methods.) What this means is that when declaring variables before `setup()`, you will need to assign them values inside `setup()` if you wish to use p5 functions. For example:

```javascript
var n;
function setup() {
  createCanvas(100, 100);
  n = random(100);
}
```

The explanation for this is a little complicated, but it has to do with the way the library is setup in order to support both global and instance mode. To understand what's happening, let's first look at the order things happen when a page with p5 is loaded (in global mode).

1. Scripts in <head> are loaded.
2. <body> of HTML page loads (when this is complete, the onload event fires, which then triggers step 3).
3. p5 is started, all functions are added to the global namespace.

So the issue is that the scripts are loaded and evaluated before p5 is started, when it's not yet aware of the p5 variables. If we try to call them here, they will cause an error. However, when we use p5 function calls inside setup() and draw() this is ok, because the browser doesn't look inside functions when the scripts are first loaded. This is because the setup() and draw() functions are not called in the user code, they are only defined, so the stuff inside of them isn't run or evaluated yet.

It's not until p5 is started up that the setup() function is actually run (p5 calls it for you), and at this point, the p5 functions exist in the global namespace.

We mentioned on-demand global mode earlier. This mode is most useful when you're building a program that uses other libraries and you want to control how p5 is loaded on the page with the others. You can read more about it [here](https://github.com/processing/p5.js/wiki/p5.js-overview#instantiation--namespace). But another interesting use of on-demand global mode is the ability to call p5 explicitly and then use p5 functions outside of `setup()`. Here's an example:
```javascript
new p5();

var boop = random(100);

function setup() {
    createCanvas(100, 100);
}

function draw() {
    background(255, 0, boop);
}
``` 

### How can I specify the HTML node where I want my canvas?

Use the `.parent()` function, [see more info here](https://github.com/processing/p5.js/wiki/p5.js-overview#createcanvas).

### Is setup() and draw() required? What is the page load order?

To load p5 onto the page, either `setup()` or `draw()` is required (but not both), *or* you may use [instance mode](https://github.com/processing/p5.js/wiki/p5.js-overview#instantiation--namespace) to have more control over when and how your sketch gets loaded. 

In global mode (non-instance mode), the order of page loading is as follows:

1. window `onload` event fires.
2. `preload()` is called (if included in the sketch), p5 waits for all loading functions within it to complete.
3. `setup()` is called (if included in the sketch). Note that p5 will not wait to go onto draw if there are loading methods in `setup()`.
4. `draw()` is called (if included in the sketch). It continues to be called based on variables set by `noLoop()/loop()` and `frameRate()`.

In instance mode, the order is the same but the user decides when to call `new p5(...)` rather than it happening automatically with the window `onload` event.

