#Starting points#


##Research##

[Ruby-Processing](https://github.com/jashkenas/ruby-processing) - Ruby syntax but utilizes the ease of Processing for drawing

+ Nice workthru of learning processing examples


##js great parts##
+ Functions as first class objects
	Functions in Simplified JavaScript are lambdas with lexical scoping.
+ Dynamic objects with prototypal inheritance
	Objects are class-free. We can add a new member to any object by ordinary assign- ment. An object can inherit members from another object.
+ Object literals and array literals
	This is a very convenient notation for creating new objects and arrays. JavaScript literals were the inspiration for the JSON data interchange format.


##js messy/confusing parts##

+ global vars
+ scope
+ semicolon insertion
+ unicode
+ typeof: null (better - my_value === null), testing for objectness (use truth test)
+ parseInt use radix (maybe imply with js-processing, unless otherwise specified)
+ diff add behavior depending on type of obj (nums vs strings)
+ floating point
+ NaN (use own number test something like 
		var isNumber = function isNumber(value) { return typeof value === 'number' &&
      isFinite(value);
    })
+ fake arrs
+ falsy vals
+ hasOwnProperty
+ === !== vs == !=
+ switch fall through
+ function foo() {} vs var foo = function foo() {}, hoisting
+ new: typed wrappers (eg: new String), missing new with object creation converts to fxn call (avoid new if possible)
+ void


##Questions##

+ What is unique about javascript?
+ What are main ways it diverges/differs from java/processing?
	+ dynamic vs static
	+ loosely-typed vs strongly-typed
	+ prototypal vs classical inheritance
	+ functions as classes, constructors, methods
	+ classical objects are hard, the only way to add a new member to a hard object is to create a new class. js objects are soft, a new member can be added to a soft object by simple assignment. shallow hierarchies are efficient and expressive, deep hierarchies are often inappropriate.
	+ event driven vs linear/loop based
+ Focus on browser experience? What about node, etc.
+ Network connectivity, manipulating dom, interfacing with other elts outside canvas, user interface built-on elts that processing doesn't have, multiple drawing surfaces, interfaces with other libraries / also spec for other - maybe IDE adds in auto (like import library feature).


##Keep same##
+ primitives


##IDE##
+ web developer tools
+ processing-js as entry point to web development
+ more transparent, more standard web structure
+ standard javascript - quasi auto complete, strict mode, viz of var scope, sequence
+ live, quasi-live coding environment, dev tools built in
+ standard javascript - quasi auto complete, strict mode, viz of var scope, sequence
+ standard javascript - quasi auto complete, strict mode, viz of var scope, sequence
+ also use processing methods
+ visually represent what's going on, in terms of inheritance
+ find in reference
+ not too cluttered
+ all the benefits, but executes like it's in the browser


##Considerations##

+ Prototypal inheritance vs emulating classical inheritance.
	+  tool to make it more clear
+ Optimization
	+  Embed instead of having to learn speed tricks?
+ Callbacks/async
	+ helper fxn like newThread() method
	+ identify what sync/async, async ones have callback methods. if you have your own, here's how, and how to specify callback or not
	+ start everything with a
	+ use async module
+ Library spec
+ IDE - http://js.processing.org/learning/ide


##Core classes##
PImage, PFont, PShape and PShader, PGraphics (needed to create offscreen drawing surfaces), and PVector.


##What js things could be improved?##
	+ libraries - documentready annoying, processing-js handles loading order for you (modernizer.js, queue.js), waits to execute
	+ (controlled loading and execution built-in)
	+ canvas/error handling
+ Library spec?
+ IDE
+ live-coding
+ dynamic typing - better typeof method, switch statement
+ strict typeof
+ enforce a type of code, scope
+ jslint strict mode
+ pokeyoke
+ easy way to define your own events, bind listeners



+ question - limited to canvas?

+ what would be gained/lost by js, removing java altogether
+ processing-lite, js syntax
+ processing-js bridge to c++ compiles
+ installations without c++
+ processing as web dev

+ a bunch of different scenarios - writing out what code for that would look like
+ speculative source code - examples or hack usable

+ processing identity - running in browser, barrier to entry low
+ primary audience - hard-core programmers, 19yr old design students

+ system+api
+ as a library, focus what processing does and doesn’t do


+ https://github.com/daniellmb/JavaScript-Scope-Context-Coloring
+ http://codemirror.net/
+ http://www.jslint.com/
