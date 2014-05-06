By adding inline documentation in the p5.js source code, a reference can be automatically generated. This document outlines the tags and information to include in your documentation so that it shows up in the reference, formatted properly. The reference is auto-generated from the source code periodically, so it may take a few days for your documentation to show up in the reference. If it's been longer than a few days or you're having other problems email [laurmccarthy@gmail.com](mailto:laurmccarthy@gmail.com).

See below for the basics, more specifics about yuidoc style [here](http://yui.github.io/yuidoc/syntax/index.html).
###Specify element type and description

There are 4 kinds of elements: `@class`, `@method`, `@property`, `@event`.
You must specify one of these for the element to appear in the docs, with the name of the element after it. The description should appear on top and should not be formatted with spaces, tabs, etc.

```
   /**
    * The x component of the vector
    * @property x
    * @type {Number}
    */
    this.x = x || 0;
```

```

  /**
   * Draw an arc
   *
   * If x, y, width, height, start and stop are the only params provided, draws an
   * open pie.
   * If mode is provided draws the arc either open, chord or pie, dependant
   * on the variable provided
   *
   * @param  {Number} x x-coordinate of the arc's ellipse
   * @param  {Number} y y-coordinate of the arc's ellipse
   * @param  {Number} width width of the arc's ellipse by default
   * @param  {Number} height height of the arc's ellipse by default
   * @param  {Number} start angle to start the arc, specified in radians
   * @param  {Number} stop angle to stop the arc, specified in radians
   * @param  {String} [mode] optional parameter to determine the way of drawing the arc
   */
```

```
  /**
   *
   * Calculates the magnitude (length) of the vector and returns the result
   * as a float (this is simply the equation <em>sqrt(x*x + y*y + z*z)</em>.)
   *
   * @method mag
   * @return {number} magnitude (length) of the vector
   */
   PVector.prototype.mag = function () {
    return Math.sqrt(this.magSq());
   };
```

###Specify parameters

For methods, any `@params` should be specified. They should not be formatted with spaces, tabs, etc, and should follow the standard:

```
@param {type} name Description here, no problem how long.
```

If the parameter is optional, add square brackets around the name:

```
@param {type} [name] Description here.
```

###Specify return type

The `@return` is identical to `@params`, but without the name. It should be the last element in `@method`. The JS types are: String, Number, Boolean, Object, Array, Null, and Undefined. If there is no return type, do not include `@return`. 

```
@return {type} Description of the data returned.
```

###Specify other tags

Use `@final` if a property or variable is a constant:

```
    /**
     * PI is a mathematical constant with the value 3.14159265358979323846.
     * @property PI
     * @type Number
     * @final
     */
    PI: PI
```

Use `@private` if a property or variable is a private variable (default is `@public` so no need to specify).

```
    /**
     * _start calls preload() setup() and draw()
     * 
     * @method _start
     * @private
     */
     p5.prototype._start = function () {
```

###Specify module for files

The top of each *file* should contain a `@module` tag at the top of the file. Modules should correspond to JavaScript files (or require.js modules). They can work as groups in the lists of items. see here: http://p5js.org/api/#methods (the modules are COLOR, IMAGE, PVECTOR, etc.). 

```
/**
 * @module image
 */
define(function (require) {
  // code here
};
```


###Constructors

Constructors are defined with `@class`. Each constructor should have the tag `@class` followed by the name of the class, as well as the tag `@constructor`, and any `@param` tags required.

```
  /**
   * The p5 constructor function.
   * @class p5
   * @constructor
   * @param {Object} [node] The canvas element. A canvas will be added to the DOM if not provided.
   * @param {Object} [sketch] The sketch object.
   */
   var p5 = function( node, sketch) {
     ...
   }
```

###Adding example code

Optionally, you can add examples with `@example`. Example code can be placed between `<code></code>` tags with comments included. Each `<code>` block is automatically run on a canvas of 200x200 pixels.

```
@example <code>arc(50, 50, 80, 80, 0, PI+QUARTER_PI, OPEN);</code>
<code>arc(50, 50, 80, 80, 0, PI+QUARTER_PI, CHORD);</code>
<code>arc(50, 50, 80, 80, 0, PI+QUARTER_PI, PIE);</code>
```


###Generating documentation

Run `grunt` to automatically regenerate the documentation in addition to compiling the code. You can view it locally in docs/reference (note that you need to be running a server for it to display correctly).

Run `grunt yui` to regenerate documentation without recompiling the code. If you notice the page not updating, try deleting the `reference/` folder and running the command again.

Run `grunt requirejs:yuidoc_theme` if you have made changes to the core JS files behind the yuidoc reference page (not inline documentation changes to src). This regenerates the templates, then run `grunt yui` to regenerate the referenced based on the updated theme.

Periodically, the reference folder is copied over to p5js.org.