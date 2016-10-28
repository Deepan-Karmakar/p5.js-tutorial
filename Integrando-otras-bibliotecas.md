### ¿Qué es una biblioteca?

Una biblioteca es una extensión de las capacidades de un lenguaje de programación, que hace el trabajo tedioso por ti. Por ejemplo, en español existen letras y palabras, y las palabras son a veces agrupadas en artículos, libros y novelas que contienen conceptos fundamentales e ideas que pueden ser reutilizadas. Las bibliotecas de código funcionan de la misma manera, una biblioteca es una colección de código que ya existe y que hace cosas a alto nivel por ti para que tú no tengas que reinventar la rueda. Pueden existir bibliotecas que te hacen más fácil dibujar en la pantalla, bibliotecas que pueden procesar grandes cantidades de datos, bibliotecas que tienen capacidad 3D, etc...

¡p5.js es una biblioteca! No obstante, existen otras bibliotecas que podemos integrar para ayudar a extender nuestras capacidades en JavaScript.

### Cómo encontrar y escoger una biblioteca JS
Búsquedas en Google son la mejor manera de encontrar bibliotecas JS
+ “[utilidadd que necesitas]” + “JS”
+ “[utilidadd que necesitas]” + “JS” + “library”
+ “3D” + “JS”
+ “leapmotion” + “JS”

Aquí va una lista de algunas bibliotecas interesantes para que revises:
+ [list of creative coding libraries](http://www.wholepixel.com/libs)
+ [Buzz](http://buzz.jaysalvat.com/) - web audio
+ [two.js](http://jonobr1.github.io/two.js) - two dimensional drawing
+ [three.js](http://threejs.org) - three dimensional graphics
+ [d3.js](http://d3js.org) - data visualization
+ [boxbox](http://incompl.github.io/boxbox) - physics engine
+ [hammerjs](http://eightmedia.github.io/hammer.js/) - multi touch support

Nota importante: navegadores web, versiones de JS, etc, sí importarán. No mencionaremos detalles específicos, pero ten en cuenta que puede ser un problema. La mayoría de las bibliotecas indican en su documentación los requerimientos mínimos de tu navegador o hardware que necesitarán.

### Cómo leer documentación
One last criteria for choosing a library is documentation. Documentation makes or breaks a good code library.  Library code is often dense and difficult to read. Good documentation is any accompanying text/images, tutorials, examples and descriptions of how to use the library. Before deciding to use a library, do a quick sanity check that the webpage has seemingly good documentation to go along with it, because that will be your compass as you try to use the new library.

### How to download and include a JS library
1. When you finally find a library, go to the project’s download page and look for a download to a .js file that contains all the library code, this file is usually not very big and not meant for editing.  It’s just meant to be included in your web project as extra capabilities.  Think of it like adding reinforcements to your structure.

2. Download the .js file and put it in the same folder as your .html file.

3. Add a ```<script>``` tag to the ```<head>``` section of the HTML to link to the library. That’s it!


### Example: using Buzz

Buzz is a web audio library, download it at http://buzz.jaysalvat.com/. Browse the documentation at http://buzz.jaysalvat.com/documentation/buzz/. (See example [Integrating-other-libraries/0](https://github.com/processing/p5.js/tree/master/examples/tutorials/Integrating-other-libraries/0).)

In this first example, we play a sound within ```setup()```.
```javascript
var mySound = new buzz.sound("rhodes_loop.wav");

function setup() {
  mySound.play();
}
```

In the next example, you see we can also draw an image into canvas in the same sketch. The audio playing does not conflict with the drawing, but works side by side. The audio file is loaded in setup, then triggered to play on mousePressed. (See example [Integrating-other-libraries/1](https://github.com/processing/p5.js/tree/master/examples/tutorials/Integrating-other-libraries/1).)

```javascript
var mySound = new buzz.sound('rhodes_loop.wav');
var myImage;

function setup() {
  createGraphics(300, 300);
  myImage = loadImage('red.jpg');
}

function draw() {
  // Draw graphics as normal
  background(255, 200, 200);
  image(myImage, 20, 20, 150, 150);
}

function mousePressed() {
  // Using the third-party library to call play() on the buzz object
  mySound.play();
}
```

Finally, let's integrate the canvas and audio. Only when you click directly on the image does the audio start; it is stopped on keyPressed. (See example [Integrating-other-libraries/2](https://github.com/processing/p5.js/tree/master/examples/tutorials/Integrating-other-libraries/2).)
 
```javascript
// Initializing a variable using the third-party library buzz object
var mySound = new buzz.sound('rhodes_loop.wav');
var myImage;

function setup() {
  createGraphics(300, 300);
  myImage =  loadImage('red.jpg');
};

function draw() {
  background(255, 200, 200);
  image(myImage, 20, 20, 150, 150);
};

function mousePressed() {
  // Check to see if mouse press is on top of image
  if (mouseX > 20 && mouseX < 170 && mouseY > 20 && mouseY < 170) {
    mySound.play(); // Start playing the sound
    mySound.loop(); // Loop the sound once it's playing
  }
}

function keyPressed() {
  mySound.stop(); // Stop the sound
}
```