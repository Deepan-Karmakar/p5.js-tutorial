###Using iframes

The simplest solution is to use iframes. In the past I've had students host their work and submit a link to running sketches as turn in. Then I can embed their sketches or examples I create in iframes on a wordpress blog or class site.

For example, here is the sketch running:<br>
http://lauren-mccarthy.com/test/p5.js/

And here it is embedded in wordpress using the code below:<br>
http://lauren-mccarthy.com/inmotion/2014/08/test-post-1/

Embed code for the iframe:
```html
<iframe src="http://lauren-mccarthy.com/test/p5.js" width="600px" height="400px"></iframe>
```

and styling for the iframe:
```html
<style>iframe { border: none; }</style>
```

Only trick here is you need to manually set the size of the iframe, so it works best of things are a standard size.


###Using render.js

You can also use the render.js script, see an example [here](http://lauren-mccarthy.com/inmotion/2014/08/test-post-2/). This is used for the editable examples in the reference, see [this example](http://p5js.org/reference/#p5/colorMode). You can embed a live sketch like this:
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


Note that you will also need jquery (you can grab this one http://p5js.org/js/vendor/jquery-1.9.1.min.js), and I recommend using this updated render.js that I just tweaked a little (https://gist.github.com/lmccart/b3242051abafd660f4a3). If you include prism.js and prism.css you get code highlighting, too. Here's a snippet of the header I'm using on my blog:
https://gist.github.com/lmccart/69586b68a9c505222d15


###Using ace

I am using the render.js script for the reference examples because it is lighter and lets me hack to make things work with examples with no setup/draw. I am using ace editor on the learn/examples pages because it's less hacky and has better editing support. This one would require a little custom configuration, you could start with this tutorial here: http://ace.c9.io/#nav=howto. 
