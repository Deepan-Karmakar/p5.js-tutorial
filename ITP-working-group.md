##Meeting 3: Mar 28

###Projects list

1. DOM manipulation. The intention with this library is not to limit to the canvas, and to allow access to DIVs and other elements. It's not meant to replace jQuery, but to give some basic access to the DOM in a way that is intuitive and useful. This [tutorial](https://github.com/lmccart/p5.js/wiki/DOM-Extensions) describes the current functionality. This area of functionality is just a first draft, and some further thought in terms of functionality and syntax would be really useful.

2. Touch interactions. Examples 5-0 through 5-3 here http://p5js.org/workshop/, demonstrate the current supported touch functionality. However, there are a few more questions to think about.
     * Should there be some notion of a touch id for the touches[] array? This could be useful for persistently tracking touches.
     * [Example 5-2](http://p5js.org/workshop/examples/example_5-2/sketch.js) demonstrates how to write your sketch to support both touch and mouse depending on device, but maybe we want a smart function or wrapper that automatically returns mouseX/Y or touchX/Y depending on device.
     * Right now there is `touchStarted`, `touchMoved`, and `touchEnded`. Should there be more functions to support touch?

3. Developer page, extended version. This could be a great task for someone less experienced with JS or JS development. You could start by copying the current developer page into a new wiki page, then working through each step of the development setup process, and add a few sentences/paragraphs of lay mans explanation anywhere you would have liked to see it.

4. Short tutorial for writing unit tests. This tutorial could include:
     * A little background on what is unit testing -- what is it and why do it? (Some of this could probably be pulled from a general tutorial on unit testing.)
     * Short explanation of the tools: [mocha](visionmedia.github.io/mocha/), [chai](chaijs.com).
     * How to figure out which tests to write, and how many? (This could probably be pulled from a general tutorial on unit testing.)
     * TDD assertion style, and how to actually write the tests (syntax).
     * How to add your tests and run them (test.html, `grunt`).

5. Short tutorial for writing JSDoc inline comments.

6. Tutorial for sketch instantiation -- global and instance modes. This functionality was recently added! Now we need some explanation:
     * Why use global vs instance mode?
     * Explanation of syntax for each setup. For instance mode, some explanation of closures, scope.
     * What are the different options for using each?
The [global](https://github.com/lmccart/p5.js/tree/master/examples/instantiation-global) and [instance](https://github.com/lmccart/p5.js/tree/master/examples/instantiation-instance) example cases are a good place to start.

7. Unit tests for [time and date functions](https://github.com/lmccart/p5.js/wiki/API#time--date).

8. Unit tests for [trig functions](https://github.com/lmccart/p5.js/wiki/API#trigonometry).

9. Unit tests for [environment functions](https://github.com/lmccart/p5.js/wiki/API#environment).

10. Something else you are excited about?