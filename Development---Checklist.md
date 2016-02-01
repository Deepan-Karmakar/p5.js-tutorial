Example code, sketches, and snippets working as of version 0.3.9. 
Examples and features that are completed have been crossed out. 
An asterisk (*) denotes that the example is not working for the version listed above.

This list is simply being provided as an easy way to see what example/tutorial code has already been created and what still needs being created.

See the [development page](https://github.com/processing/p5.js/wiki/Development) for more details on how to contribute.

### Features

* PDF Support [#373](https://github.com/processing/p5.js/issues/373)
* Read local files [#370](https://github.com/processing/p5.js/issues/370)
* ~~Incorporate WebGL [#321](https://github.com/processing/p5.js/issues/321)~~
* Implement preload() [#317](https://github.com/processing/p5.js/issues/317)
* Implement PFont [#60](https://github.com/processing/p5.js/issues/60)
* Implement File I/O [#40](https://github.com/processing/p5.js/issues/40)
* Implement PShape [#37](https://github.com/processing/p5.js/issues/37)
* Implement Curves [#25](https://github.com/processing/p5.js/issues/25)

*** 

### Reference Sketches

#### Color - Creating & Reading
* ~~alpha()~~
* ~~blue()~~
* ~~brightness()~~
* ~~color()~~
* ~~green()~~
* ~~hue()~~
* ~~lerpColor()~~
* ~~red()~~
* ~~saturation()~~

#### Color - Setting
* ~~background()~~
* ~~clear()~~
* ~~colorMode()~~
* ~~fill()~~
* ~~noFill()~~
* ~~noStroke()~~
* ~~stroke()~~

#### Constants
* ~~HALF_PI~~
* ~~PI~~
* ~~QUARTER_PI~~
* ~~TAU~~
* ~~TWO_PI~~

#### Data - Array Functions
* ~~append()~~
* ~~arrayCopy()~~
* ~~concat()~~
* ~~reverse()~~
* ~~shorten()~~
* ~~sort()~~
* ~~splice()~~
* ~~subset()~~

#### Data - Conversion
* ~~float()~~
* ~~int()~~

#### Data - String Functions
* ~~join()~~
* ~~match()~~
* ~~matchAll()~~
* ~~nf()~~
* ~~nfc()~~
* ~~nfp()~~
* ~~nfs()~~
* ~~split()~~
* ~~splitTokens()~~
* ~~trim()~~

#### Data - Table
* p5.Table
* p5.TableRow

#### Data - Output
* ~~save()~~

#### DOM
* p5.Element
* ~~parent()~~
* id()
* class()
* ~~mousePressed()~~
* mouseWheel()
* mouseReleased()
* mouseClicked()
* mouseMoved()
* mouseOver()
* mouseOut()
* addClass()
* removeClass()
* child()
* html()
* position()
* style()
* attribute()
* value()
* show()
* hide()
* size()
* remove()

#### Environment
* ~~frameCount~~
* ~~focused~~
* ~~cursor()~~
* ~~frameRate()~~
* ~~noCursor()~~
* ~~displayWidth~~
* ~~displayHeight~~
* ~~windowWidth~~
* ~~windowHeight~~
* ~~windowResized~~
* ~~width~~
* ~~height~~
* ~~fullscreen()~~

#### Image
* ~~createImage()~~
* p5.Image
    * loadPixels()
    * updatePixels()
    * get()
    * ~~set()~~
    * resize()
    * copy()
    * mask()
    * filter()
    * blend()
    * save()

#### Image - Loading & Displaying
* ~~loadImage()~~
* ~~image()~~
* ~~tint()~~
* ~~noTint()~~
* ~~imageMode()~~

#### Image - Pixels
* ~~pixels[]~~
* ~~blend()~~
* ~~copy()~~
* ~~filter()~~
* ~~get()~~
* ~~loadPixels()~~
* ~~set()~~
* ~~updatePixels()~~

#### Input - Files
* ~~loadJSON()~~
* ~~loadStrings()~~
* ~~loadTable()~~
* loadXML()

#### Input - Keyboard
* ~~keyIsPressed~~
* ~~key~~
* ~~keyCode~~
* ~~keyPressed()~~
* ~~keyReleased()~~
* ~~keyTyped()~~

#### Input - Mouse
* ~~mouseX~~
* ~~mouseY~~
* ~~pmouseX~~
* ~~pmouseY~~
* ~~winMouseX~~
* ~~winMouseY~~
* ~~pwinMouseX~~
* ~~pwinMouseY~~
* ~~mouseButton~~
* ~~mouseIsPressed~~
* ~~mouseMoved()~~
* ~~mouseDragged()~~
* ~~mousePressed()~~
* ~~mouseReleased()~~
* ~~mouseClicked()~~
* ~~mouseWheel()~~

#### Input - Time & Date
* ~~day()~~
* ~~hour()~~
* ~~minute()~~
* ~~millis()~~
* ~~month()~~
* ~~second()~~
* ~~year()~~

#### Input - Touch
* touchX
* touchY
* ptouchX
* ptouchY
* touches[]
* ~~touchStarted()~~
* ~~touchMoved()~~
* ~~touchEnded()~~

#### Math
* ~~createVector()~~
* ~~p5.Vector~~
    * ~~set()~~
    * ~~add()~~
    * ~~sub()~~
    * ~~mult()~~
    * ~~div()~~
    * ~~mag()~~
    * ~~magSq()~~
    * ~~dot()~~
    * ~~cross()~~
    * ~~dist()~~
    * ~~normalize()~~
    * ~~limit()~~
    * ~~setMag()~~
    * ~~heading()~~
    * ~~rotate()~~
    * ~~lerp()~~
    * ~~array()~~
    * ~~equals()~~
    * ~~fromAngle()~~
    * ~~random2D()~~
    * ~~random3D()~~

#### Math - Calculation
* ~~abs()~~
* ~~ceil()~~
* ~~constrain()~~
* ~~dist()~~
* ~~exp()~~
* ~~floor()~~
* ~~lerp()~~
* ~~log()~~
* ~~mag()~~
* ~~map()~~
* ~~max()~~
* ~~min()~~
* ~~norm()~~
* ~~pow()~~
* ~~sq()~~
* ~~sqrt()~~

#### Math - Noise
* ~~noise()~~
* ~~noiseDetail()~~
* ~~noiseSeed()~~

#### Math - Trigonometry
* ~~acos()~~
* ~~asin()~~
* ~~atan()~~
* ~~atan2()~~
* ~~cos()~~
* ~~sin()~~
* ~~tan()~~
* ~~degrees()~~
* ~~radians()~~
* ~~angleMode()~~

#### Math - Random
* ~~randomSeed()~~
* ~~random()~~
* ~~randomGaussian()~~

#### Output - Text Area
* ~~print()~~

#### Rendering
* ~~createCanvas()~~
* ~~noCanvas()~~
* ~~createGraphics()~~
* ~~blendMode()~~

#### Shape - 2D Primatives
* ~~arc()~~
* ~~ellipse()~~
* ~~line()~~
* ~~point()~~
* ~~quad()~~
* ~~rect()~~
* ~~triangle()~~

#### Shape - Attributes
* ~~ellipseMode()~~
* ~~noSmooth()~~
* ~~rectMode()~~
* ~~smooth()~~
* ~~strokeCap()~~
* ~~strokeJoin()~~
* ~~strokeWeight()~~

#### Shape - Curves
* ~~bezier()~~
* ~~bezierDetail()~~
* ~~bezierPoint()~~
* ~~bezierTangent()~~
* ~~curve()~~
* ~~curveDetail()~~
* ~~curvePoint()~~
* ~~curveTangent()~~

#### Shape - Vertex
* ~~beginContour()~~
* ~~beginShape()~~
* ~~bezierVertex()~~
* ~~curveVertex()~~
* ~~endContour()~~
* ~~endShape()~~
* ~~quadraticVertex()~~
* ~~vertex()~~

#### Structure
* ~~preload()~~
* ~~setup()~~
* ~~draw()~~
* ~~remove()~~
* ~~noLoop()~~
* ~~loop()~~
* ~~push()~~
* ~~pop()~~
* ~~redraw()~~

#### Transform
* applyMatrix()
* resetMatrix()
* ~~rotate()~~
* ~~scale()~~
* ~~shearX()~~
* ~~shearY()~~
* ~~translate()~~

#### Typography - Attributes
* ~~textAlign()~~
* textLeading() *
* ~~textSize()~~
* ~~textStyle()~~
* ~~textWidth()~~

#### Typography - Loading & Displaying
* ~~text()~~
* ~~textFont()~~

***

### Tutorial Sketches

#### Structure
* ~~Coordinates~~
* ~~Width/Height~~
* ~~Setup/Draw~~
* ~~No Loop~~
* ~~Loop~~

#### Form
* ~~Points/Lines~~
* ~~Shape Primitives~~
* ~~Pie Chart~~
* ~~Regular Polygon~~
* ~~Star~~
* ~~Triangle Strip~~
* ~~Bezier~~

#### Data
* ~~Variables~~
* ~~True/False~~
* ~~Variable Scope~~

#### Arrays
* ~~Array~~
* ~~Array 2D~~
* ~~Array Objects~~

#### Control
* ~~Iteration~~
* ~~Embedded Iteration~~
* ~~Conditionals 1~~
* ~~Conditionals 2~~
* ~~Logical Operators~~

#### Image
* ~~Load/Display Image~~
* ~~Background Image~~
* ~~Transparency~~
* ~~Alpha Mask~~
* ~~Create Image~~
* ~~Pointillism~~

#### Color
* ~~Hue~~
* ~~Saturation~~
* ~~Brightness~~
* ~~Color Variables~~
* ~~Relativity~~
* ~~Linear Gradient~~
* ~~Radial Gradient~~

#### Math
* ~~Increment Decrement~~
* ~~Operator Precedence~~
* ~~Distance 1D~~
* ~~Distance 2D~~
* ~~Sine~~
* ~~Sine Cosine~~
* ~~Sine Wave~~
* ~~Additive Wave~~
* ~~PolarToCartesian~~
* ~~Double Random~~
* ~~Random~~
* ~~Noise1D~~
* ~~Noise Wave~~

#### Simulate
* ~~Forces~~
* ~~Particle System~~
* ~~Flocking~~
* ~~Wolfram CA~~
* ~~Game of Life~~

#### Objects
* ~~Objects~~
* ~~Multiple Objects~~
* ~~Array of Objects~~
* ~~Objects 2~~

#### Instance Mode
* ~~Instantiation~~

#### DOM
* ~~Input/Button~~
* ~~Slider~~
* ~~Modifying the DOM~~
* ~~Video~~
* ~~Video Canvas~~
* ~~Video Pixels~~
* ~~Video Capture~~

#### Sound
* ~~Load/Play Sound~~
* ~~Preload SoundFile~~
* ~~soundFormats~~
* ~~Play Mode~~
* ~~Pan Sound~~
* ~~Sound Effect~~
* ~~Playback Rate~~
* ~~Amplitude Analysis~~
* ~~Noise Drum Envelope~~
* ~~Note Envelope~~
* ~~Amplitude (Volume)~~
* ~~Oscillator Frequency~~
* ~~Mic Input~~
* ~~Frequency Spectrum~~
* ~~Mic Threshold~~
* ~~Filter LowPass~~
* ~~Filter BandPass~~
* ~~Delay~~
* ~~Reverb~~
* ~~Convolution Reverb~~
* ~~Record Save Audio~~
* ~~Frequency Modulation~~
* ~~Amplitude Modulation~~

#### Hello P5
* ~~Simple Shapes~~
* ~~Interactivity 1~~
* ~~Interactivity 2~~
* ~~Animation~~
* ~~Flocking~~
* ~~Weather~~
* ~~Drawing~~
* ~~Song~~