### What is a library?
A library is an extension of capabilities to a programming language that do some tedious work for you. For example, in the English language there are letters and words, and the words are sometimes grouped together in articles, books and novels that contain core concepts and ideas that can be re-used. Libraries of code work the same way, a library is a collection of code that already does some higher level things for you so you don’t have to reinvent the wheel. There might be libraries that make it easy to draw to the screen, libraries that parse large amounts of data, libraries that display 3D, etc...

p5.js is a library itself! But there are other libraries we can integrate to help us extend our capabilities in JavaScript.

### How to find and choose a JS library?
Google searches are the best way to find JS libraries
+ “[capability you need]” + “JS”
+ “[capability you need]” + “JS” + “library”
+ “3D” + “JS”
+ “leapmotion” + “JS”

Here are some interesting libraries to check out:
+ [Buzz](http://buzz.jaysalvat.com/) - web audio
+ [two.js](http://jonobr1.github.io/two.js) - two dimensional drawing
+ [three.js](http://threejs.org) - three dimensional graphics
+ [d3.js](http://d3js.org) - data visualization
+ [boxbox](http://incompl.github.io/boxbox) - physics engine

Important note: web browsers, JS versions, etc, will matter. We will not go into specifics here, but know that this will be an issue. Most libraries will state in their documentation minimum requirements your browser or hardware must meet.

### How to download and include a JS library?
1. When you finally find a library, go to the project’s download page and look for a download to a .js file that contains all the library code, this file is usually not very big and not meant for editing.  It’s just meant to be included in your web project as extra capabilities.  Think of it like adding reinforcements to your structure.

2. Download the .js file and put it in the same folder as your .html file.

3. Add a ```<script>``` tag to the ```<head>``` section of the HTML to link to the library. That’s it!



Example download: Buzz audio download button at http://buzz.jaysalvat.com/
How to read documentation
Documentation makes or breaks a good code library.  Libraries code is often dense and difficult to read.  Good documentation is any accompanying text/images, tutorials, examples and descriptions of how to use the library.  Before deciding to use a library, do a quick sanity check that the webpage has seemingly good documentation to go along with it, because that will be your compass as you try to use the new library.
Example documentation: http://buzz.jaysalvat.com/documentation/buzz/
How to use library
Example 1: Buzz audio play a sound within setup()
Example 2: Buzz audio play a sound within setup() plus draw image
Example 3: Buzz audio play, loop and stop a sound
Example 4: (at 4pm): LeapJS by Chen Sun
Example 5: (at 4pm): ubidisplays by Kendall Gremillion
How to use libraries in traditional Processing
http://processing.org/reference/libraries/
