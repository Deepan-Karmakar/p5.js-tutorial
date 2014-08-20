##Using iframes

The simplest solution is to use iframes. In the past I've had students host their work and submit a link to running sketches as turn in. Then I can embed their sketches or examples I create in iframes on a wordpress blog or class site.

For example, here is the sketch running:<br>
http://lauren-mccarthy.com/test/p5.js/

And here it is embedded in wordpress using the code below:<br>
http://lauren-mccarthy.com/inmotion/2014/08/test-post-1/

Embed code for the iframe:
```html
<iframe src="http://lauren-mccarthy.com/test/p5.js" width="600px" height="400px"></iframe>
```

and styling for the iframe (this could directly into a wordpress post or in a stylesheet):
```html
<style> iframe{ border: none; } </style>
```

Only trick here is you need to manually set the size of the iframe, so it works best of things are a standard size.


##Using render.js

You can also use the [render.js](https://github.com/lmccart/p5js.org/blob/master/js/render.js) script, see this [wordpress post example](http://lauren-mccarthy.com/inmotion/2014/08/test-post-2/). This is used for the editable examples in the reference, see this [reference example](http://p5js.org/reference/#p5/colorMode). 

In the header of your page you will need to link in a few files in addition to render.js (all files can be found [here](https://github.com/lmccart/p5js.org/tree/master/js)):

```html
<!-- p5.js library -->
<script type="text/javascript" src="path/to/p5.min.js"></script>
<!-- optional addons for sound/dom examples -->
<script type="text/javascript" src="path/to/p5.sound.js"></script>
<script type="text/javascript" src="path/to/p5.dom.js"></script>
<!-- scripts for rendering -->
<script type="text/javascript" src="path/to/jquery.min.js"></script>
<script type="text/javascript" src="path/to/render.js"></script>
```

You can embed a live sketch like this:
```html
<div class="example">
<pre>
<code class="language-javascript">
function setup() {
  createCanvas(600, 400);
}
 
function draw() {
  background(0);
}
</code>
</pre>
</div>

<script>renderCode()</script>
```

The key parts are the layout of the HTML (div.example > pre > code), and the renderCode() call at the end. 

Note that this script also will support sketches with no setup or draw, though the p5.js library on it's own will not. This hack is just for the purposes of showing simple snippets, like in the reference.
```html
<div class="example">
<pre>
<code class="language-javascript">
background(100);
</code>
</pre>
</div>

<script>renderCode()</script>
```

####Customizing

If you include [prism](http://prismjs.com/) you can add code highlighting, too. You will need to link to both [prism.js](https://github.com/lmccart/p5js.org/blob/master/js/vendor/prism.js) and [prism.css](https://github.com/lmccart/p5js.org/blob/master/css/prism.css) in the header of your page. The CSS file can be modified to highlight and color as you wish.

```html
<!-- code highlighting -->
<script type="text/javascript" src="path/to/prism.js"></script> 
<link rel="stylesheet" href="path/to/prism.css" type="text/css"/>
```

If you want to hide the code and just show the sketch, you could add a line like this:
```html
<style> .example{ display: none; } </style>
```

If you want to show the code but hide just the buttons to edit the code displayed, you could add a line like this:
```html
<style> .edit_space{ display: none; } </style>
```

##Using ace editor

The examples on the [learn page](http://p5js.org/learn/#examples) use [ace editor](http://ace.c9.io/#nav=about) rather than the render.js script because it's less hacky and has better support for editing (it includes linting, dynamic code highlighting, etc). This one requires a little custom configuration, there is a tutorial to get you started here: http://ace.c9.io/#nav=howto. 
