Implementing autocomplete in the p5.js web editor was a 2017 Google Summer of Code project. This wiki page outlines the progress made as of August 2017. 

## Background
Here's an excerpt of the GSOC proposal: 

> The p5 web editor is currently in development, with plans to launch in time for fall semester classes. Currently, there’s no autocomplete code functionality and it’s not possible to access documentation from within the editor. We could use tern.js to solve both of these problems. Tern.js is a code analysis engine for Javascript that works with CodeMirror, the code editor behind the p5 web editor. In addition to autocomplete, tern.js supports shortcuts to documentation and the ability to easily rename all occurrences of a variable. 

The p5.js web editor uses React for the front-end and is built on top of CodeMirror, an open source code editor for the browser.

The project was to hook up Tern.js—”a standalone Javascript analysis engine”—to implement autocomplete.
Tern relies on a JSON file called a Tern definition file in order to “specify the types of things” you code and trigger different autocomplete functions accordingly. You can read more about that file [here](http://ternjs.net/doc/manual.html#typedef).

Part of getting Tern working with p5.js is creating a Tern definition file for the p5.js library so that, when you’re writing in the web editor, Tern can analyze what you’re writing. Tern has [a utility to create a definition file from a given library](http://ternjs.net/doc/manual.html#utils), but the utility didn’t work with the p5.js library.

As a hacky workaround, some scripts were adapted that convert YUIDoc documentation into Tern definition files. Repos are linked below. Because p5.js documentation is generated with YUI/YUIDoc, this "p5.js to YUIDoc to Tern file" process sort of worked: it's possible trigger links to the p5 reference on p5 functions, and it's also possible autocomplete p5 function names.

But there are still several problems that make autocomplete unusable, including a scoping problem where methods and variables that should not be available to certain p5 functions still appear as autocomplete options.

## Repositories
* Fork of [p5 web editor connected to Tern](https://github.com/kaganjd/p5.js-web-editor/tree/autocomplete). To get it up and running, you’d follow the steps in the README.
* Fork of [p5 main project](https://github.com/kaganjd/p5.js/tree/master) with a Grunt task to generate the Tern definition file to be used with the web editor
* [Module](https://github.com/processing/p5-tern.yuidoc) that generates the Tern definition file for the p5.js library from YUIDoc. This is set up to be a dependency of the main p5.js repository and executed with a Grunt task from there. It is not meant to be used independently.
* [Documentation re: errors when generating and using the Tern definition file](https://gist.github.com/kaganjd/32c87c49fda5f61b78aa2b88993daca4)
* [Some suggested next steps](https://gist.github.com/kaganjd/1e033541fa00af3e760c0acddf6fc197)

## Workflow in the wild
1. Generate Tern definition file from the main p5.js project by running `grunt tern`
1. Put the file output of that process, which should be a JSON file and must be named `p5.json`, into the p5.js web editor project—specifically `p5.js-web-editor/node_modules/tern/defs`
1. Use autocomplete with the web editor!

## Additional docs and repos
* [Sandboxed example of CodeMirror, React, and Tern](https://github.com/kaganjd/codemirror-react-tern)
* As mentioned above, you have to generate a Tern definition file for the p5.js library. If you want to just get to working on autocomplete without thinking about the Tern file generator part, you can use [this](https://gist.github.com/kaganjd/c1c88b17063cf53651b0f2c42218de5c). Download the JSON, make sure it’s named `p5.json` and put it in `p5.js-web-editor/node_modules/tern/defs`
* [Tern docs](http://ternjs.net/doc/manual.html)
* [CodeMirror docs](https://codemirror.net/)
* [p5.js](https://github.com/processing/p5.js)
* [p5.js web editor](https://github.com/processing/p5.js-web-editor)
