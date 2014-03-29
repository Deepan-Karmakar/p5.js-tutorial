[THIS IS A ROUGH DRAFT]

This extended guide doesn't assume familiarity with concepts like unit testing, inline documentation, Javascript deployment workflows or specific tools like grunt or mocha. If you are comfortable with these and are looking for a quick start guide, please see [this page](https://github.com/lmccart/p5.js/wiki/Development).

The development of P5 is collaborative: we encourage you to participate and help us shape it. Here are some ways to contribute:

- **Help us document.** P5's main documentation is generated automatically based on structured comments written in the code describing classes, functions and their parameters. Browsing the files in the `src` folder and adding documentation where it's missing is a great way to get familiarized with p5. See syntax details [below].
- **Help us test.** P5 is tested using a unit testing framework. This means that for each feature there should be a test that asserts whether it does what it's supposed to do. Each time we generate a distribution of p5, all unit tests are run. This allows us to make changes more confidently: if all tests pass, we know we didn't break anything; if some tests fail, we know exactly what did. You can take a look at the existing tests in the `tests` folder. Adding tests to functions that don't have them is also a great way to get started. See how to do this in the [testing section].
- **Fix a bug.** Explain how Issues list is used in this project. 
- **Add a feature.**

Setting up: 
- start from beginning: fork repo and add upstream remote (and link to tutorial).
- explain why distribution needed: p5 runs in browser. browser gets library from server. can’t start running until all files have been transferred —> distribution. p5.js: all files combined into one. p5-min.js: one file w/o unnecessary spaces and line breaks. not readable, but faster download. 
- explain why grunt: javascript is interpreted, not compiled. but because p5 fairly big project still need a series of steps to generate distribution and also do some quality control: syntax checking (and good practices? check what lint does), running tests. repetitive task, so automated. task runner: grunt. to install grunt: package manager.

- specific setup instructions will be the same, but adding details like ‘Open Terminal’. 

Writing code:
- **Code Style.** "All code in any code-base should look like a single person typed it, no matter how many people contributed."
We recommend looking at [idiomatic.js](https://github.com/rwaldron/idiomatic.js/) for a JS style guide. Here is some sample code for quick reference: ///I'd want to be able to take a quick look: have to do a lot of scrolling before getting this on the idiomatic page. Should see what else to include though 
```
var i = 0,
      length = 100;

    for ( ; i < length; i++ ) {
      // statements
    }

    if ( true ) {
      // statements
    } else {
      // statements
    }

```
 
- **Inline Documentation.** Please add inline documentation to your code. This will allow us to generate a complete HTML documentation website automatically. We use [JSDoc](http://usejsdoc.org/); here is some example syntax: 
```
/**
   * Create a new empty PImage object.
   * @param  {Integer} width
   * @param  {Integer} height
   * @return {PImage}
   */
function Book(title, author) {
}
```

Testing:
- explain what the tools are before going over specific steps.
- include test snippet.

