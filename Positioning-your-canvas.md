<!--
  Hello editor!

  For more background on this tutorial, or to leave comments on it, see:

  https://github.com/processing/p5.js/issues/1333
-->

By default, your p5 sketch's canvas is added to the end of the web page it's in, and no styling is applied to it.

However, it's possible to position and style it any way you want with a bit of [HTML and CSS](Intro-to-HTML-and-CSS).

Let's start with a simple sketch:

```html
<!DOCTYPE html>
<meta charset="utf-8">
<title>My Sketch</title>
<body>
<script src="http://cdnjs.cloudflare.com/ajax/libs/p5.js/0.4.23/p5.js"></script>
<script>
function setup() {
  background('pink');
}
</script>
</body>
```

This will display a 100x100 pink square at the top-left of your browser window.

## Centering the sketch on the page

We can add a `<style>` tag containing some CSS that uses [flexible box layout](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) to vertically and horizontally center our sketch on the page:

```html
<!DOCTYPE html>
<meta charset="utf-8">
<style>
html, body {
  height: 100%;
}

body {
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
<title>My Sketch</title>
<body>
<script src="http://cdnjs.cloudflare.com/ajax/libs/p5.js/0.4.23/p5.js"></script>
<script>
function setup() {
  background('pink');
}
</script>
</body>
```

Note that flexible box layout (or "flexbox", as it's often called) is a relatively new feature in CSS. As such, the above CSS will work on the latest browsers, but older browsers may not position it accurately. To fully support older browsers, you may want to use [vendor prefixing](http://shouldiprefix.com/#flexbox) in your CSS.

## Relocating the canvas

Alternatively, you may want to position your canvas in the midst of other information on your page. This can be done by using p5's [`p5.Element.parent()`](http://p5js.org/reference/#/p5.Element/parent) function to move our sketch inside an existing HTML element on our page, rather than leaving it at the very end of the page:

```html
<!DOCTYPE html>
<meta charset="utf-8">
<title>My Sketch</title>
<body>
<p>Here is my sketch:</p>
<div id="holder">
  <!-- Our sketch will go here! -->
</div>
<p>Pretty cool, eh?</p>
<script src="http://cdnjs.cloudflare.com/ajax/libs/p5.js/0.4.23/p5.js"></script>
<script>
function setup() {
  var canvas = createCanvas(100, 100);
  canvas.parent('holder');
  background('pink');
}
</script>
</body>
```
