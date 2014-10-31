####[DEVELOPER DOC](https://github.com/lmccart/p5.js/wiki/Development)
####[INLINE DOCS GUIDE](https://github.com/lmccart/p5.js/wiki/Inline-documentation)

**If you are working on one of these things, create an issue on github and place your github username in brackets in the title, so others can collaborate rather than duplicate!**

###Projects list

1. **DOM manipulation.** The intention with this library is not to limit to the canvas, and to allow access to DIVs and other elements. It's not meant to replace jQuery, but to give some basic access to the DOM in a way that is intuitive and useful. This [tutorial](https://github.com/lmccart/p5.js/wiki/DOM-Extensions) describes the current functionality. This area of functionality is just a first draft, and some further thought in terms of functionality and syntax would be really useful.
* https://github.com/lmccart/p5.js/issues/389
* https://github.com/lmccart/p5.js/issues/391
* https://github.com/lmccart/p5.js/issues/395
* https://github.com/lmccart/p5.js/issues/394


2. **Touch interactions.** Examples 5-0 through 5-3 here http://p5js.org/workshop/, demonstrate the current supported touch functionality. However, there are a few more questions to think about.
     * Should there be some notion of a touch id for the touches[] array? This could be useful for persistently tracking touches.
     * [Example 5-2](http://p5js.org/workshop/examples/example_5-2/sketch.js) demonstrates how to write your sketch to support both touch and mouse depending on device, but maybe we want a smart function or wrapper that automatically returns mouseX/Y or touchX/Y depending on device.
     * Right now there is `touchStarted`, `touchMoved`, and `touchEnded`. Should there be more functions to support touch?


4. Some file I/O stuff to finish up: https://github.com/lmccart/p5.js/issues/40

5. Thinking about text:
* https://github.com/lmccart/p5.js/issues/60
* https://github.com/lmccart/p5.js/issues/356

6. Thinking about svgs and pdf export:
https://github.com/lmccart/p5.js/issues/37

7. Various [bugs and issues](https://github.com/lmccart/p5.js/issues).

6. **Tutorial for sketch instantiation** -- global and instance modes. This functionality was recently added! Now we need some explanation:
     * Why use global vs instance mode?
     * Explanation of syntax for each setup. For instance mode, some explanation of closures, scope.
     * What are the different options for using each?
The [global](https://github.com/lmccart/p5.js/tree/master/examples/instantiation-global) and [instance](https://github.com/lmccart/p5.js/tree/master/examples/instantiation-instance) example cases are a good place to start.

3. **Developer page, extended version. [LUISA]** This could be a great task for someone less experienced with JS or JS development. You could start by copying the [current developer page](https://github.com/lmccart/p5.js/wiki/Development) into a new wiki page, then working through each step of the development setup process, and add a few sentences/paragraphs of lay mans explanation anywhere you would have liked to see it.

8. Other documentation currently needed: https://github.com/lmccart/p5.js/issues/346

10. **Something else you are excited about?**
     * Sound module, data module, module template. And what is a "module" called anyway? Extension, addon, module?
     * IDE
     * WebGL 
     * Node.js + Websockets + p5.js
     * Arduino or Physical stuff + p5.js
