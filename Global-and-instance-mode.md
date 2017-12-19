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


## Other JS libraries

* [The p5.js repo includes tutorial re: integrating other JS libraries](https://github.com/lmccart/p5.js/wiki/Integrating-other-libraries)


## HTML5 Video

p5.js will likely include features for video playback and capture in the future, but it is currently not a capability.  However given that HTML5 supports video and capture (via [WebRTC](http://www.webrtc.org/)) it is fairly easy for us to integrate these features into a p5 sketch.

To embed a video on a web page, it's as easy as creating a video element.

```html
<video><source src="file.mov"></video>
```

You can set various properties of the video via attributes.

```html
<video loop="true" autoplay="true"><source src="fingers.mov"></video>
```

We could, of course, type the HTML directly into index.html, but we can also create it dynamically via p5.

```javascript
video = createHTML('<video id=\'vid\'><source src=\'fingers.mov\'></video>');
video = document.getElementById('vid');  // Grab the dom element itself
video.play();                            // We can call methods on that element like play()
video.setAttribute('loop', true);        // We can also set attributes
video.setAttribute('controls',true);
```

[More about HTML5 audio and video](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Using_HTML5_audio_and_video).

If we want to draw on top of the video we could create a transparent canvas element.  However, in some projects it may be advantageous to copy the pixels of a video into a canvas rather than display the video element itself on the page.  This can be accomplished but first setting the video element's display style to none.

```javascript
video.style.display = 'none';
```

We can then draw the video to the canvas using `drawImage()`.  It should be noted that `drawImage()` is [part of the HTML5 Canvas API](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D).  While used behind the scenes in p5, it's not something we've used directly ourselves.  It's most likely this wiki will become quickly out of date if/when p5 integrates video drawing, but for now we'll have to grab our canvas graphics context and manually draw the video.  The code looks like this:

```javascript
// Video
var video;

// Drawing context
// Temporary as eventually p5 may support drawing video into canvas directly?
var context;

function setup() {
  video = createHTML('<video id=\'vid\'><source src=\'fingers.mov\'></video>');
  video = document.getElementById('vid');
  video.play();

  var canvas = createCanvas(640, 360);
  // need to keep track of the context to draw the video
  context = canvas.elt.getContext('2d');
}

function draw() {
  background(51);
  // Draw video into canvas
  context.drawImage(video,0,0,width,height);
};
```

## Capture with WebRTC

Now that we have recorded video working, we can take a few extra steps and get live capture from a user.  First we make an empty video element.

```javascript
// Make an invisible video DOM element
video = createHTML('<video id=\'vid\'></video>');
video = document.getElementById('vid');
video.setAttribute('autoplay',true);
video.style.display = 'none';
```

Now instead of saying `<source src="file.mov">` we need to assign the video's source to a live capture stream.  To do this, we are going to use [navigator.getUserMedia()](https://developer.mozilla.org/en-US/docs/Web/API/Navigator.getUserMedia).  This navigator object is a property of window that provide additional browser functionality.   It is not consistently available across all browsers, however.  We can get a little bit of cross-browser support by checking to see if it is available and if not, trying a different, analogous method.

```javascript
navigator.getUserMedia = navigator.getUserMedia || 
                         navigator.webkitGetUserMedia || 
                         navigator.mozGetUserMedia || 
                         navigator.msGetUserMedia;
```

`getUserMedia()` takes three arguments.  

The first argument is an object with a video and audio property.  This indicates whether we want to capture from a camera, microphone, or both.  For example: `{ video: true, audio: false }` gives us video stream only.

The second argument is a function that is triggered when getUserMedia() has been successful (note a user has to approve access to capture device).  What we'll do here is take the argument to that function (a media stream) and assign it to our video element, i.e.

```javascript
function(stream) {
  video.src = window.URL.createObjectURL(stream);
}
```

The last argument is a function that is triggered if the user rejects our request to capture. 

```javascript
function(e) {
  console.log('User said no!', e);
} 
```

Putting it all together, it looks like so:

```javascript
// Make an invisible video DOM element
video = createHTML('<video id=\'vid\'></video>');
video = document.getElementById('vid');
video.setAttribute('autoplay',true);
video.style.display = 'none';

// For cross-browser support
navigator.getUserMedia  = navigator.getUserMedia || navigator.webkitGetUserMedia || navigator.mozGetUserMedia || navigator.msGetUserMedia;

// Get a stream of video from the user
navigator.getUserMedia(
  // First argument is an object that tells us if we want audio and/or video
  { video: true, audio: false }, 
  // Second argument is a function that assigns a 'stream' to the video's source
  function(stream) {
    video.src = window.URL.createObjectURL(stream);
  }, 
  // Third argument is the callback if the user rejected
  rejected
);  

var rejected = function(e) {
  // The user rejected capturing
  // We could handle this however we want
  console.log('User said no!', e);
};
```

Notice how we are using an anonymous function for the second argument and a function stored in a variable for the third one.  This is arbitrary and is just meant to demonstrate both possibilities.



