###Using iframes

The simplest solution is to use iframes. In the past I've had students host their work and submit a link to running sketches as turn in. Then I can embed their sketches or examples I create in iframes on a wordpress blog or class site.

For example, here is the sketch running:
http://lauren-mccarthy.com/test/p5.js/

And here it is embedded in wordpress using the code below:
http://lauren-mccarthy.com/inmotion/2014/08/test-post-1/

Embed code for the iframe:

`<iframe src="http://lauren-mccarthy.com/test/p5.js" width="600px" height="400px"></iframe>`

and styling for the iframe:

`<style>iframe { border: none; }</style>`

Only trick here is you need to manually set the size of the iframe, so it works best of things are a standard size.


###Using render.js

If you want to use the render script, you can embed a live sketch like this:
https://gist.github.com/lmccart/77b004bd0455a246c7d2
The key parts are the layout of the HTML (div.example > pre > code), and the renderCode() call at the end.
http://lauren-mccarthy.com/inmotion/2014/08/test-post-2/

Note that you will also need jquery (you can grab this one http://p5js.org/js/vendor/jquery-1.9.1.min.js), and I recommend using this updated render.js that I just tweaked a little (https://gist.github.com/lmccart/b3242051abafd660f4a3). If you include prism.js and prism.css you get code highlighting, too. Here's a snippet of the header I'm using on my blog:
https://gist.github.com/lmccart/69586b68a9c505222d15


###Using ace

I am using the render.js script for the reference examples because it is lighter and lets me hack to make things work with examples with no setup/draw. I am using ace editor on the learn/examples pages because it's less hacky and has better editing support. This one would require a little custom configuration, you could start with this tutorial here: http://ace.c9.io/#nav=howto. 