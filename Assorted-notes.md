#Starting points#

##Possibilities##
+ what would be gained/lost by js, removing java altogether
+ processing-lite, js syntax
+ processing-js bridge to c++ compiles
+ installations without c++
+ processing as web dev

##Approaches##
+ a bunch of different scenarios - writing out what code for that would look like
+ speculative source code - examples or hack usable

##Goals##
+ processing identity - running in browser, barrier to entry low
+ primary audience - hard-core programmers, 19yr old design students
+ system+api
+ as a library, focus what processing does and doesn’t do




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
+ question - limited to canvas?



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
+ https://github.com/daniellmb/JavaScript-Scope-Context-Coloring
+ http://codemirror.net/
+ http://www.jslint.com/


##Core classes##
PImage, PFont, PShape and PShader, PGraphics (needed to create offscreen drawing surfaces), and PVector.


##What js things could be improved?##
+ libraries - documentready annoying, processing-js handles loading order for you (modernizer.js, queue.js), waits to execute
+ (controlled loading and execution built-in)
+ canvas/error handling


##Other notes##
+ Library spec?
+ dynamic typing - better typeof method, switch statement
+ strict typeof
+ enforce a type of code, scope
+ jslint strict mode
+ pokeyoke
+ easy way to define your own events, bind listeners


##Current Processing JavaScript mode##
+ [processing.org/learning/javascript/](http://processing.org/learning/javascript/)
+ [github.com/jeresig/processing-js](https://github.com/jeresig/processing-js)
+ Processing.js is really two things: a Processing-to-JavaScript translator; and an implementation of the Processing API (e.g., functions like line(), stroke(), etc.) written in JavaScript instead of Java.
+ Nothing new to learn - Processing.js automatically converts your Processing code to JavaScript. This means that you don't have to learn JavaScript in order to run your code in a browser.
+ Does not currently support libraries.
+ Possible to write native JS code inside sketch, but not intended use.
+ Simulates synchronous I/O using Directives (preloading assets).