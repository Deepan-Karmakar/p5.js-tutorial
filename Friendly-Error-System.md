Let's use this space to game plan the work around friendly errors.

## Resources

* [Atul and Jess' 2016 Processing Fellowship Proposal](https://gist.github.com/toolness/d994ff777db79e493a6f)
* [#971 - friendly error system fixes, updates, and improvements](https://github.com/processing/p5.js/issues/971)

## User Research

* [p5 Debugging Tutorial](http://p5js.org/tutorials/debugging/) - Lots of types of user errors are anticipated here.
* [Processing Forum p5.js programming questions](https://forum.processing.org/two/categories/p5-js-programming-questions) - Users frequently post about their difficulties learning/using p5.js here.
* [ICM 2015 homework documentation wiki](https://github.com/ITPNYU/ICM-2015/wiki#homework-documentation) - Each teacher had their own page where users could post their questions each class. In particular, [Homework-Dano-Wednesday](https://github.com/ITPNYU/ICM-2015/wiki/Homework-Dano-Wednesday) has lots of great beginner questions.
* [Issue #903 - `PI` is not defined before `setup()`](https://github.com/processing/p5.js/issues/903) - This kind of issue is currently being addressed with [#1130](https://github.com/processing/p5.js/pull/1130).

## Ideas

* [Anonymous usage reporting](https://github.com/processing/p5.js/pull/1130#issuecomment-159911009) - I think the fancy word for this may be "telemetry" but I'm not sure.
* [#1247 - Add more friendly error help for global APIs used at top-level code](https://github.com/processing/p5.js/issues/1247)
* [Using custom YUIDoc tags to specify required browser features for p5 functionality](https://github.com/processing/p5.js/pull/1144#issuecomment-160419254)
* [#583](https://github.com/processing/p5.js/issues/583) involves using a TypeScript Definition File, which could assist with the friendly error system.

## Fellowship Workplan 

In order to immerse ourselves in the problem space we will conduct a research phase of work. We will time black about 4 weeks to the phase and then re-evaluate if this is reasonable. The goal of this research is to create a list of common errors. In this phase we will:

* Audit existing materials
  * on P5 repo
  * forums
  * ICM 2015 homework
* Plan and run a user test 
* Interview and/or send questionnaire to educators
* Write documentation with a contributor - first approach


