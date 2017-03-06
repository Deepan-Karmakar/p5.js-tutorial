###Resumen de diferencias

El lenguaje p5.js es muy similar al lenguaje Processing, con unas pocas discrepancias:

+ Como puedes pensar en tu bosquejo como más que solo el lienzo para dibujar, `size()` (tamaño) ha sido reemplazado por `createCanvas()` (crear lienzo), para sugerir la posibilidad de crear otros elementos.
+ `frameRate(num)` define la tasa de cuadros, pero la variable `frameRate`ha sido removida. Para obtener la actual tasa de cuadros, llama a la función `frameRate()` sin argumentos.
+ JavaScript no siempre carga todo de forma síncrona, existen algunas opciones para lidiar con esto:
     + Todos los métodos de carga (load) poseen un argumento opcional de callback (llamada). Esto es, una función que es llamada luego de que el archivo ha sido cargado. 
     + De forma alternativa, puedes ubicar todas las llamadas de carga (load) en un método `preload()` (precarga) que ocurre antes de `setup()` (configuración). Si existe un método preload, setup espera hasta que todo esté cargado, ver este [ejemplo con imagen](http://p5js.org/es/examples/image-alpha-mask.html).
+ La variable `mousePressed` ha sido reemplazada por `mouseIsPressed`.
+ Además de los eventos de ratón (mouse), existen eventos de toque (touch), cuya correspondencia es la siguiente:
     + `mouseX` ~ `touchX`
     + `mouseY` ~ `touchY`
     + `mousePressed()` ~ `touchStarted()`
     + `mouseDragged()` ~ `touchMoved()`
     + `mouseReleased()` ~ `touchEnded()`
     + Existe un arreglo `touches[]` (toques) que contiene una serie de objetos con propiedades x e y correspondientes a las posiciones de cada dedo.
+ `push/popMatrix()`, y `push/popStyle()` han sido reemplazados con `push()` y `pop()`, el equivalente de llamar tanto a los métodos de matriz (matrix) y estilo (style) de forma conjunta.
+ Por defecto, todo está en el espacio de nombres global, y puedes crear tus bosquejos como lo haces en Processing. Sin embargo, existe algo que llamamos modo instancia (instance mode) para crear un bosquejo p5 que se comporta bien con el resto del código corriendo en tu página. Revisa este  [ejemplo del modo instancia](http://p5js.org/es/examples/instance-mode-instantiation.html) y este [tutorial de modo global vs instancia](https://github.com/processing/p5.js/wiki/Modos-Global-e-Instance).
+ En el modo global, la variable p5 y los nombres de funciones no están disponibles fuera de `setup()`, `draw()`, `mousePressed()`, etc. (Excepto en el caso donde están ubicadas dentro de funciones que son llamadas por uno de estos métodos.) Esto significa que que cuando se declaran variables antes de `setup()`, necesitarás asignarles valores dentro de `setup()` si quieres usar estas funciones de p5. Por ejemplo:

  ```javascript
  var n;
  function setup() {
    createCanvas(100, 100);
    n = random(100);
  }
  ```

+ No todas las características de Processing están implementadas en p5.js, ¡pero estamos trabajando en eso! En este momento no existe un equivalente de PShape. El modelo de cámara en p5js sigue siendo muy básico, con solo una posición del ojo y sin un eje de dirección de "hacia donde mirar". Revisa la [referencia](http://p5js.org/es-reference/) para buscar documentación al día sobre las funciones.
 
###Notas sobre JavaScript
+ Las variables no tienen un tipo. Usa var en vez de float, int, double, long, char, String, Array, etc. No necesitas especificar valores de retorno o tipos de parámetros de las funciones.
+ Una var puede ser cualquier cosa -- cualquiera de los tipos mencionados, pero también funciones.
+ Los arreglos son construidos de forma muy simple (no se necesita ArrayList de Processing) e incluyen muchas características, revisa este [ejemplo de arreglo](http://p5js.org/es/examples/arrays-array.html) y más sobre arreglos de JavaScript [aquí](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array)
+ JavaScript usa algo llamado prototype (prototipo) para construir algo similar a los objetos a partir de clases de Java. Revisa este [ejemplo de objetos](http://p5js.org/es/examples/objects-objects.html) y más sobre objetos JavaScript [aquí](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Trabajando_con_objectos).

###Ejemplos de conversión

####Bosquejo básico

Esta es la configuración básica de un bosquejo en Processing y uno en p5.js. Observa que p5.js también requiere un archivo HTML en blanco que enlaza la biblioteca p5.js y tu archivo de bosquejo (sketch) en el encabezado(header (ver [Empezar](http://p5js.org/es/get-started/)).

```java
void setup() {
  // contenidos de setup()
}

void draw() {
  // contenidos de draw()
}
```


```javascript
function setup() {
  // contenidos de setup()
}

function draw() {
  // contenidos de draw()
}
```

####Converit un bosquejo de Processing a p5.js

Aquí se presentan dos ejemplos de bosquejos que han sido convertidos de Processing a p5.js. Los cambios hechos son señalados en los comentarios, todas las otras líneas quedan igual.

```javascript
/**
 * This example can be found in the Processing examples package
 * that comes with the Processing PDE.
 * Processing > Examples > Basics > Form > Bezier
 * Adapted by Evelyn Eastmond
 */

function setup() {           // **change** void setup() to function setup()
  createCanvas(640, 360);    // **change** size() to createCanvas()
  stroke(255);               // stroke() is the same
  noFill();                  // noFill() is the same
}

function draw() {                         // **change** void draw() to function draw()
  background(0);                          // background() is the same
  for (var i = 0; i < 200; i += 20) {     // **change** int i to var i
    bezier(mouseX-(i/2.0), 40+i, 410, 20, 440, 300, 240-(i/16.0), 300+(i/8.0)); // bezier() is the same
  }
}

```

```javascript

/**
 * This example can be found in the Processing examples package
 * that comes with the Processing PDE.
 * Processing > Examples > Topics > Interaction > Follow3
 * Adapted by Evelyn Eastmond
 */

var x = new Array(20);  // **change** float[] x = new float[20] to new Array(20)
var y = new Array(20);  // **change** float[] y = new float[20] to new Array(20)
var segLength = 18;                                 // **change** float to var

function setup() {                          // **change** void setup() to function setup()
  createCanvas(640, 360);                   // **change** size() to createCanvas()
  strokeWeight(9);                          // strokeWeight() is the same
  stroke(255, 100);                         // stroke() is the same
  for(var i=0; i<x.length; i++) {         // initialize the array
    x[i]=0;
    y[i]=0;
  }
}

function draw() {                           // **change** void draw() to function draw()
  background(0);                            // background() is the same
  drawSegment(0, mouseX, mouseY);           // functions calls, mouseX and mouseY are the same
  for(var i=0; i<x.length-1; i++) {         // **change** int i to var i
    drawSegment(i+1, x[i], y[i]);           // function calls are the same
  }
}

function drawSegment(i, xin, yin) {         // **change** void drawSegment() to function drawSegment(), remove type declarations
  var dx = xin - x[i];                      // **change** float to var
  var dy = yin - y[i];                      // **change** float to var
  var angle = atan2(dy, dx);                // **change** float to var, atan2() is the same
  x[i] = xin - cos(angle) * segLength;      // cos() is the same
  y[i] = yin - sin(angle) * segLength;      // sin() is the same
  segment(x[i], y[i], angle);               // function calls are the same
}

function segment(x, y, a) {                 // **change** void segment() to function segment(), remove type declarations
  push();                            		// pushMatrix() becomes push()
  translate(x, y);                          // translate() is the same
  rotate(a);                                // rotate() is the same
  line(0, 0, segLength, 0);                 // line() is the same
  pop();                              		// popMatrix() becomes pop()
}
```

####Converting a p5.js sketch to Processing

Here are two examples of sketches that have been converted from p5.js to Processing. The changes made are shown in the comments, all the other lines remained the same.

```java
/**
 * This example can be found in the Processing examples package
 * that comes with the Processing PDE.
 * Processing > Examples > Basics > Form > Bezier
 */

void setup() {                         // **change** function setup() to void setup()
  size(640, 360);                      // **change** createCanvas() to size()
  stroke(255);
  noFill();
}

void draw() {                          // **change** function draw() to void draw()
  background(0);
  for (int i = 0; i < 200; i += 20) {  // **change** var i to int i
    bezier(mouseX-(i/2.0), 40+i, 410, 20, 440, 300, 240-(i/16.0), 300+(i/8.0));
  }
}
```

```java
/**
 * This example can be found in the Processing examples package
 * that comes with the Processing PDE.
 * Processing > Examples > Topics > Interaction > Follow3
 * Based on code from Keith Peters. 
 */

float[] x = new float[20];                       // **change** array of 0's to be float[] x = new float[20]
float[] y = new float[20];                       // **change** array of 0's to be float[] x = new float[20]
float segLength = 18;                            // **change** var to float

void setup() {                                   // **change** function setup() to void setup() 
  size(640, 360);                                // **change** createCanvas() to size()
  strokeWeight(9);
  stroke(255, 100);
}

void draw() {                                    // **change** function draw() void draw()
  background(0);
  dragSegment(0, mouseX, mouseY);
  for(int i=0; i<x.length-1; i++) {              // **change** int i to var i
    dragSegment(i+1, x[i], y[i]);
  }
}

void dragSegment(int i, float xin, float yin) {  // **change** function drawSegment() to void drawSegment(). add type delcarations.
  float dx = xin - x[i];                         // **change** var to float
  float dy = yin - y[i];                         // **change** var to float
  float angle = atan2(dy, dx);                   // **change** var to float
  x[i] = xin - cos(angle) * segLength;
  y[i] = yin - sin(angle) * segLength;
  segment(x[i], y[i], angle);
}

void segment(float x, float y, float a) {        // **change** function segment() to void segment(). add type delcarations.
  pushMatrix();
  translate(x, y);
  rotate(a);
  line(0, 0, segLength, 0);
  popMatrix();
}
```

####About variables

In p5.js, all variables (whether they are numbers, strings, arrays, functions, objects, whatever!) are declared using the symbol "var". In Processing, you must specify the variable type. 

For example, instead of:

```javascript
boolean button = false;
```

you'd write
```javascript
var button = false;
```

or 

instead of:

```javascript
float x = 100.3;
```

you'd write
```javascript
var x = 100.3;
```

Here is a summary of the supported Processing data types (table borrowed from [Getting Started with Processing](http://shop.oreilly.com/product/0636920000570.do)).

Name | Description | Range of values
--- | --- | ---
int | Integers (whole numbers) | -2,147,483,648 to 2,147,483,647
float | Floating-point values | -3.40282347E+38 to 3.40282347E+38
boolean | Logical value | true or false
char | Single character | A-z, 0-9, and symbols
String | Sequence of characters | Any letter, word, sentence, and so on
PImage | PNG, JPG, or GIF image | N/A
PFont | VLW font; use the Create Font tool to make | N/A
PShape | SVG file | N/A



###What next?

+ Check out the [p5.js reference](http://p5js.org/reference/) for up to date documentation.
+ Play with the examples and demos on the [tutorials page](http://p5js.org/tutorials).