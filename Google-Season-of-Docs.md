Welcome! This page contains a list of ideas and how you can help contribute to the [Processing Foundation's](https://processingfoundation.org/) work on [p5.js](http://p5js.org) for Google Season of Docs.

For all of our projects, it's incredibly important that things are kept as simple and user-friendly as possible. Our work is not for developers, it's for people who are less familiar with code, and/or just want to get things done. We're especially interested in documentation projects that lower the barrier to entry for new users or contributors and make it easier for them to get started.

In addition to this list, we track specific bugs and enhancements via github issues:
* [p5.js](https://github.com/processing/p5.js/issues) / [p5.js documentation](https://github.com/processing/p5.js-website/issues)
* [p5.js web editor](https://github.com/processing/p5.js-web-editor)

## Google Season of Docs 2019

_**If you have questions about an idea or need guidance on forming your proposal, please post to the [Processing Forum](https://discourse.processing.org/c/season-of-docs). This is the best way to get feedback and develop your idea. This makes it possible for everyone to learn from your questions and contribute their thoughts.**_

## Project Ideas

[p5.js](http://p5js.org) is a JavaScript library that starts with the original goal of Processing, to make coding accessible for artists, designers, educators, beginners, and reinterprets this for today's web. Using the original metaphor of a software sketchbook, p5.js has a full set of drawing functionality. However, you’re not limited to your drawing canvas, you can think of your whole browser page as your sketch! p5.js has addon libraries that make it easy to interact with other HTML5 objects, including text, input, video, webcam, and sound. p5.js is a new interpretation of Processing, not an emulation or port, and it is in active development.

### + Internationalization improvements
Currently the p5.js website supports translations for Spanish and Simplified Chinese. Both of these could use updated translations for sections of the text. [This page gives an overview of the translation process.](https://github.com/processing/p5.js-website/blob/master/contributor_docs/i18n_contribution.md) Alternatively, a student might propose adding another language that is not currently supported.
* Expected Outcomes: Update of p5js.org translations, or addition of a new language
* Skills Required: Fluency in a second language besides English, JavaScript, familiarity with Github or version control
* Difficulty: beginner, intermediate, or advanced

### + Curate set of p5.js examples for 1.0 release
We are aiming for a 1.0 release in early 2020, see this [roadmap](https://github.com/processing/p5.js/blob/master/developer_docs/roadmap.md) for plans. As part of this release, we would like to also release a new curated set of examples on the p5.js website. This project would involve identifying and curating an artist list, finding their contact information, reaching out to them for existing examples or inviting them to make new ones, gathering and standardizing the files, and adding them to the p5.js website.
* Expected Outcomes: Updated set of p5.js examples for p5.js website for 1.0 release
* Skills Required: JavaScript, HTML, CSS, communication skills
* Possible Mentors: Lauren McCarthy, Stalgia Grigg
* Difficulty: beginner, intermediate, or advanced

### + Improving p5.js WebGL/3D functionality
This project would involve extending the 3D API and adding to the general functionality, performance, clarity of documentation, and usability for p5's 3D API. An example for a project that fits within this may be improving the lighting fidelity and options to be more in line with Processing OpenGL mode, or improving performance of the WebGL Renderer by refactoring sections of the codebase to avoid redundant WebGL function calls/expand caching. These are two possible options but you are welcome to submit project proposals that suggest alternate ideas for what might signify a major improvement to p5's 3D functionality. 
In addition to implementing the code functionality, a successful project would also address documentation, updated examples, and unit tests.
You can learn more about the current WebGl architecture [here](https://github.com/processing/p5.js/wiki/WebGL-Module-Architecture) and see all open issues [here](https://github.com/processing/p5.js/issues?utf8=%E2%9C%93&q=is%3Aissue%20is%3Aopen%20webgl).
* Expected Outcomes: Implementation of expanded functionality or performance improvement for WebGL mode, updated documentation and tests
* Skills Required: JavaScript, experience with WebGL or GL programming, familiarity with Github or version control
* Possible Mentors: Kate Hollenbach, Stalgia Grigg
* Difficulty: intermediate, advanced

### + Stabilizing and improving p5.xr during Alpha release
p5.xr is a library for p5.js that enables [WebXR](https://github.com/immersive-web/webxr) capabilities with p5 sketches. The goal of the library is to allow p5.js sketches to become multiplatform AR or VR projects with little added code. The planned initial release for the project is early summer 2019. This project would involve working alongside Stalgia Grigg to stabilize the library, develop the pre/post release roadmap, test functionality, and expand features in the time leading up to the release as well as immediately afterwards. A successful project would also need to produce clear documentation.
This project will rely heavily on the WebGL Renderer for p5.js. You can learn more about the current WebGl architecture [here](https://github.com/processing/p5.js/wiki/WebGL-Module-Architecture) and the WebXR API [here](https://immersive-web.github.io/webxr-reference/webxr-device-api/).
* Expected Outcomes: Major contributions in all or some of the following: stabilization, documentation, testing, and feature implementation for p5.xr library. The specific expectations will be developed with mentor at beginning of summer.
* Skills Required: JavaScript, experience with WebGL or GL programming, familiarity with AR/VR familiarity with Github or version control
* Possible Mentors: Stalgia Grigg
* Difficulty: intermediate, advanced

### + Improve p5.js unit tests
Currently, p5.js has a number of [unit tests](https://github.com/processing/p5.js/tree/master/developer_docs#unit-tests) that are run when the library is built. This project would start with a survey to understand which areas are in need of unit tests and which are sufficiently covered. Then the student would implement the needed tests. They may post issues for some sections of missing tests to invite the contributor community to help in completing the unit test coverage. This project would also ideally include a tutorial covering the basics of unit testing for p5.js and how to write and add them, so new contributors can learn how.
* Expected Outcomes: More complete unit test coverage, p5.js unit testing tutorial
* Skills Required: JavaScript, familiarity with Github or version control
* Possible Mentors: Evelyn Masso
* Difficulty: intermediate, advanced

### + Improve Friendly Error System (FES) and documentation
The Friendly Error System (FES) is a system designed to help new programmers with common user errors as they get started learning. It catches common beginning errors and provides clear language and links to help a user resolve the error. This project would involve improving the FES code and documentation. This might mean things like updating the [FES developer doc](https://github.com/processing/p5.js/blob/master/developer_docs/friendly_error_system.md), adding comments inline to [the code](https://github.com/processing/p5.js/blob/master/src/core/error_helpers.js), and proposing and implementing new features. Another big goal we have is to [add internationalization/localization to the FES](https://github.com/processing/p5.js/issues/3390) so error messages may be given in different languages.
* Expected Outcomes: Improvement of p5.js FES and documentation
* Skills Required: JavaScript, familiarity with Github or version control
* Possible Mentors: Evelyn Masso
* Difficulty: intermediate, advanced

### + Adding GIF support
Currently, animated .gif files loaded via `loadImage()` and displayed via `image()` will display as static images. A current workaround is to use the `createImg()` function, but this adds complexity and it would be nice for gifs to work with the core `image()` function. 
* Expected Outcomes: Implementation of GIF support in `loadImage()` and `image()` functions.
* Skills Required: JavaScript, familiarity with Github or version control
* Difficulty: intermediate, advanced

### + Utilize the Audio Worklet in [p5.Sound](https://github.com/processing/p5.js-sound/) library
[Audio Worklet](https://googlechromelabs.github.io/web-audio-samples/audio-worklet/) (now available in Chrome Beta) opens up many exciting possibilities for the Web Audio API. It allows us to process audio efficiently on the audio thread, and it will replace the deprecated ScriptProcessorNode.
* Expected Outcomes:
  - Phase out use of the ScriptProcessorNode in favor of the Audio Worklet, with a fallback for unsupported browsers
  - Creation of new custom nodes that utilize the Audio Worklet
  - Library is more efficient and reliable
* Skills Required: Audio / Digital Signal Processing, JavaScript
* Possible Mentors: Jason Sigal
* Difficulty: intermediate

### + Modernize examples and codebase of the [p5.Sound](https://github.com/processing/p5.js-sound/) library
There are several issues that a GSoC student could address, with a focus on utilizing p5.sound in modern web projects, and improving the developer experience.
* Expected Outcomes:
  - All examples  for p5.sound and MediaElements (part of p5.dom) address the [Chrome autoplay policy](https://github.com/processing/p5.js-sound/issues/249)
  - Update AudioIn for compatibility with latest mobile and desktop browsers
  - Improved experience for p5 sound developers who can use the latest JavaScript (beyond ES5)
  - Developers have sourcemaps for easier debugging
  - Our GitHub becomes focused on issues, rather than questions, because we have examples covering common usage scenarios
    - Create examples that show how to upload sound files to a server (#[211](https://github.com/processing/p5.js-sound/issues/211))
    - Create examples of importing p5.sound in Webpack module bundler; use with frameworks like [Angular](https://github.com/processing/p5.js-sound/issues/229) and React 
    - Examples of using p5.sound with other sound libraries, especially Meyda (#[228](https://github.com/processing/p5.js-sound/issues/228)) (for audio visualization)
  - Increase unit testing coverage
    - Continuous Integration with Travis CI on every pull request
  - p5.sound can be used with or without p5.js, and in combination with other Web Audio libraries like Tone.JS and Meyda
* Skills Required: JavaScript
* Possible Mentors: Jason Sigal
* Difficulty: intermediate

### + Create p5 Music examples - interactive and generative
Assist with the development of interactives and code examples for the upcoming online book The Code of Music, based on the [class taught at NYU ITP](https://luisaph.github.io/the-code-of-music-2018/)
* Expected outcomes: 
  - Develop interactives that illustrate musical concepts, and examples of how to manipulate them in code
  - Publish a subset of examples on the p5.js website under the category of Music
  - Investigate integrating Tone.js with p5 more seamlessly. This might mean creating a lightweight wrapper for Tone.
* Skills Required: JavaScript
* Possible Mentors: Luisa Pereira
* Difficulty: intermediate

### + Code Slang-p5.js library
Is a library that uses slang to code. This project is in the beginning stages of its development. You would be helping shape the beta version of this library. You can see more about the concept here: http://unoseistres.com/work/talks-and-presentations/    
* Expected Outcomes: Creating the first set of slang functions accompanied with examples. Developing the code logic for the library.
* Skills Required: JavaScript, familiarity with Github or version control
* Possible Mentors: Sharon De La Cruz
* Difficulty: intermediate

### + Addon Library Development
Is there something you think p5.js should do, but it currently doesn't?  p5.js can be extended through [add-ons](https://p5js.org/libraries/) and we're always looking for contributions. Past GSoC library projects include [extending p5 to work with maps](https://github.com/cvalenzuela/Mappa) and [interacting with  other microprocessors from within the browser](https://github.com/sarahgp/p5bots). More information on how to create addon libraries [here](https://github.com/processing/p5.js/blob/master/developer_docs/creating_libraries.md)
* Expected Outcomes: A github repository with library code, examples, and documentation. 
* Skills Required: JavaScript, HTML, CSS, Github
* Possible Mentors: Daniel Shiffman
* Difficulty: intermediate
