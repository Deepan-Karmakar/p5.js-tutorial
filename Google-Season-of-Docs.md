Welcome! This page contains a list of ideas and how you can help contribute to the [Processing Foundation's](https://processingfoundation.org/) work on [Processing](https://processing.org), [p5.js](http://p5js.org), [Processing for Android](http://android.processing.org/), [processing.py](http://py.processing.org), and [Processing for ARM](https://pi.processing.org).

For all of our projects, it's incredibly important that things are kept as simple and user-friendly as possible. Our work is not for developers, it's for people who are less familiar with code, and/or just want to get things done. We're far less interested in features to make the environments more powerful for advanced users than we are in features that make it easier to handle tasks that are common for a wide range of our audience.

In addition to this list, we track specific bugs and enhancements via github issues:
* [Processing](https://github.com/processing/processing/issues) / [Processing documentation](https://github.com/processing/processing-docs/issues)
* [p5.js](https://github.com/processing/p5.js/issues) / [p5.js documentation](https://github.com/processing/p5.js-website/issues), [p5.js web editor](https://github.com/processing/p5.js-web-editor)
* [Processing for Android](https://github.com/processing/processing-android/issues)
* [processing.py](https://github.com/jdf/processing.py/issues) / [processing.py documentation](https://github.com/kazimuth/processing-py-site/issues)

In particular, you might take a look through all of the [issues tagged enhancement](https://github.com/processing/processing/issues?labels=enhancement&page=1&state=open) as well as those [tagged help](https://github.com/processing/processing/issues?q=is%3Aopen+is%3Aissue+label%3Ahelp) in any of our repos.

## Summer 2019

The Processing Foundation works each summer with students who are interested in contributing to open source. Processing is participating again in [Google Summer of Code](https://summerofcode.withgoogle.com/) for 2019. Here is how to apply.
* [Google Summer of Code website](https://summerofcode.withgoogle.com/)
* [Processing Foundation GSoC Page](https://summerofcode.withgoogle.com/organizations/5693461928345600/)
* [Processing Forum](https://discourse.processing.org/c/summer-of-code) for guidance on developing proposals
* [Application and Eligibility](https://summerofcode.withgoogle.com/get-started/) - Applications open March 25, 2019 at 14:00 (Eastern Daylight Time). 

_**If you have questions about an idea or need guidance on forming your proposal, please post to the [Processing Forum](https://discourse.processing.org/c/summer-of-code). This is the best way to get feedback and develop your idea. This makes it possible for everyone to learn from your questions and contribute their thoughts.**_

### Previous year GSOC reports
The Processing Foundation participated in GSoC from 2011-2015 and 2017-2018. To get a sense of the kinds of project we work on via GSOC, take a look at these reports.

* [All Processing Foundation articles about GSoC](https://medium.com/processing-foundation/pfgsoc/home)
* [GSOC 2018 wrap-up post](https://medium.com/processing-foundation/2018-google-summer-of-code-grand-wrap-up-post-c13a5ea449e8)
* [GSOC 2017 wrap-up post](https://medium.com/@ProcessingOrg/2017-google-summer-of-code-grand-wrap-up-post-16680b1438db)
* [Processing Foundation GSOC Page](https://processingfoundation.org/advocacy/google-summer-of-code)
* [Archived GSOC 2014](http://shiffman.net/2014/11/01/gsoc-2014/)
* [Archived GSOC 2013](http://shiffman.net/2013/09/24/gsoc/)

## p5.js

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

### + Update p5.js library to ES6
We have removed this project from the list because, after further consideration, we didn't feel it was the right scope for a Google Summer of Code project. We apologize for any confusion this may have caused!

## p5.js Web Editor

The [p5.js Web Editor](editor.p5js.org) is an online platform for creating, editing, and sharing p5.js sketches. It was created three years ago, with a public release the fall of 2018, and currently in active development. [Here is the p5.js web editor github repository.](https://github.com/processing/p5.js-web-editor)

### + Add ability to make sketches private
Captured as [processing/p5.js-web-editor#91](https://github.com/processing/p5.js-web-editor/issues/91). Currently, all projects are public. This project would allow users to make sketches private if they chose. A possible advanced feature could authorize certain users to see a sketch.
* Expected Outcomes: a public/private switch for all sketches
* Skills Required: JavaScript, HTML, CSS, Github
* Possible Mentors: Cassie Tarakajian
* Difficulty: Easy

### + Adding Test Coverage
Currently the framework exists for adding tests, using [Enzyme](https://airbnb.io/enzyme/) and [Jest](https://jestjs.io/). This is a great project as it would make contributing to the web editor easier, and is self-contained and modular, which makes it easy for a variety of skill levels to work on it.
* Expected Outcomes: Testing files added to web editor repository
* Skills Required: JavaScript, HTML, CSS, Github
* Possible Mentors: Cassie Tarakajian
* Difficulty: intermediate

### + Internationalization
Currently the p5.js website supports translations for Spanish and Simplified Chinese; however, the web editor includes no translations. This project would add the framework for adding internationalization, and add the mostly finished translations for Spanish.
* Expected Outcomes: Integration of a React internationalization library, and addition of one translation
* Skills Required: JavaScript, HTML, React, Github
* Possible Mentors: Cassie Tarakajian
* Difficulty: intermediate

### + Mobile/Responsive Design Implementation
Currently, there exists [designs](https://scene.zeplin.io/project/55f746c54a02e1e50e0632c3) for mobile/responsive views that have not yet been implemented. This project would consist of implementing a subset of these views.
* Expected Outcomes: Improved functionality of web editor on tablets and phones
* Skills Required: JavaScript, HTML, React, CSS, Github
* Possible Mentors: Cassie Tarakajian
* Difficulty: intermediate

### + Asset Uploading Improvements
The web editor supports the usage of images, videos, and other assets. There are a few open tickets to improve this workflow:
* [p5.js-web-editor#375](https://github.com/processing/p5.js-web-editor/issues/375) - upload files by dragging them anywhere in the editor
* [p5.js-web-editor#673](https://github.com/processing/p5.js-web-editor/issues/673) - upload a folder of assets
* [p5.js-web-editor#387](https://github.com/processing/p5.js-web-editor/issues/387) - upload files by entering a url
* bugfixes, including [p5.js-web-editor#377](https://github.com/processing/p5.js-web-editor/issues/377), [p5.js-web-editor#403](https://github.com/processing/p5.js-web-editor/issues/403), [p5.js-web-editor#496](https://github.com/processing/p5.js-web-editor/issues/496), [p5.js-web-editor#645](https://github.com/processing/p5.js-web-editor/issues/645)
* Expected Outcomes: Improved asset uploading workflow
* Skills Required: JavaScript, HTML, React, CSS, Github
* Possible Mentors: Cassie Tarakajian
* Difficulty: intermediate

### Search in Sketch List
Captured as [p5.js-web-editor#231](https://github.com/processing/p5.js-web-editor/issues/231), the ability to search though a list of sketches via a text input.
* Expected Outcomes: An implemented sketch search feature.
* Skills Required: JavaScript, HTML, React, CSS, Github
* Possible Mentors: Cassie Tarakajian
* Difficulty: easy

### Library Management
One of the oldest tickets, [p5.js-web-editor#4](https://github.com/processing/p5.js-web-editor/issues/4) allows users to upload and manage different libraries as part of their sketches.
* Expected Outcomes: A UI for managing library dependencies
* Skills Required: JavaScript, HTML, React, CSS, Github
* Possible Mentors: Cassie Tarakajian
* Difficulty: advanced

### + Other Ideas
- code refactoring and clean up
- public/private sketches
- implementing design changes

## Processing

The desktop version of Processing has ~250,000 unique users. Daily, there are 25-30,000 people who make use of the PDE. We want to improve the experience those people have with the software, and need far more people than just the tiny team of contributors.

### + Video (Priority)
The video library for Processing uses an engine built on top of [GStreamer](http://gstreamer.freedesktop.org/). During the previous years there have been different efforts to update GStreamer to more contemporary (1.x) versions, and we currently have a [2.0 beta version](https://github.com/processing/processing-video/releases/tag/r3-v2.0-beta1) of the video library that uses the stable versions of GStreamer 1.x and the [gst1-java-core](https://github.com/gstreamer-java/gst1-java-core) Java-GStreamer bindings, based on this [fork](https://github.com/gohai/processing-video) from [Gottfried Haider](https://github.com/gohai). Even though this beta version of the library works on Linux, macOS, and Windows, it still need some work to become the default. The [2.0 milestone](https://github.com/processing/processing-video/) aggregates all the issues that should be addressed for this release.
* Expected Outcomes: Updated stable 2.0 release of the Video library
* Skills Required: Java, GStreamer, java bindings for GStreamer, JNA
* Possible Mentors: Gottfried Haider, Andres Colubri
* Difficulty: intermediate, advanced

### + New OpenGL Renderer (Priority)
JOGL's development [has slowed down](https://github.com/sgothel/jogl/commits/master) considerably during the last few years, so it may be a good idea to work on a [LWJGL](https://www.lwjgl.org/)-based renderer, even as a contributed library at first. We have created a LWJGL-based [rendering library](https://github.com/codeanticode/processing-lwjgl/), it runs but it is not yet completely functional, but could serve as a starting point.
* Expected Outcomes: New library using LWJGL that can later be integrated into the core renderer
* Skills Required: Java, OpenGL
* Possible Mentors: Andres Colubri
* Difficulty: advanced

### + Development Environment: Processing Language Server
The Processing Development Environment (PDE) is currently built in Java, using custom components that make use of Java's “Swing” library, which is even more outdated now than when it was first released. Long-term we are considering moving to a JavaScript-based solution that would 1) allow more people to contribute to its further development, 2) provide better support for building the UI, 3) have more visually consistent cross-platform results, and 4) potentially open up other ways to distribute the PDE. In order for this to happen, we would like to first create a Processing "[Language Server](https://langserver.org/)" In addition to a new PDE itself, this would allow for more sophisticated integration with existing code editors like Visual Studio Code, Atom, and more.
* Expected Outcomes: Working Processing/Java Language Server ~Working prototype of a JavaScript IDE for Processing~
* Skills Required: Java Development
* Possible Mentors: Manindra Moharana, Casey Reas
* Difficulty: advanced

### + Analytical Visualization Tools
Implement a better way to understand how people use Processing. We collect stats on the number of people using Processing, what version they're on, what OS, etc. We also collect stats for what people have installed so that we know where to put our efforts for Libraries, Modes, and Tools. At the moment, these are looked at manually when we're trying to make decisions ([documentation of how to access the data](https://github.com/processing/processing/wiki/Usage-Statistics)).  But it'd be great to have a better way to share these with the community in an ongoing basis (Scratch does a [nice job](https://scratch.mit.edu/statistics/) with this), and also for us to keep an eye on how things are going.
* Expected Outcomes: Series of scripts and web visualizations
* Skills Required: JavaScript, HTML/CSS
* Possible Mentors: Casey Reas
* Difficulty: beginner tech / advanced design

### + Library Development
Is there something you think Processing should do, but it currently doesn't?  Processing can be extended through [libraries](https://processing.org/reference/libraries/) and we're always looking for contributions.  Instructions for building libraries are here on the [GitHub wiki](https://github.com/processing/processing/wiki). Past GSoC library projects include an [Image Processing Library to Ease Differentiation of Colors for People with Colorblindness](https://medium.com/@ProcessingOrg/image-processing-library-to-ease-differentiation-of-colors-for-people-with-colorblindness-cc550f0670e0) and [Kinect v2 Processing library for Windows](http://codigogenerativo.com/kinectpv2/).
* Expected Outcomes:
   * A github repository with library code, examples, and documentation.
   * Packaging and release of library via the Processing contributions manager 
* Skills Required: Java Development
* Possible Mentors: Daniel Shiffman
* Difficulty: intermediate


## Processing for Android

### + Maintenance of Android mode: SDK downloader/updater, emulator, library structure (Priority)
The Android mode has grown into a complex code base that supports several kinds of Android apps (normal fragment-based apps, live wallpapers, watch faces, VR and AR apps). There is also a [library template](https://github.com/processing/processing-android-library-template) that contributors can use to create Processing libraries with Android-specific functionality. In order to ease the maintenance of the mode and facilitate contributions, there are a number of areas that need to be improved:
  * SDK downloader/updater: The Android mode downloads and installs the SDK and emulator files automatically, however, due to Google's continuous updates, we need to make sure that we are using the up-to-date repositories. Using a newer version of the Android platform (currently the mode downloads Android 26) while ensuring that the mode works well with is an important task. There are some issues already documented: ([#362](https://github.com/processing/processing-android/issues/362), [#523](https://github.com/processing/processing-android/issues/523), [#524](https://github.com/processing/processing-android/issues/524)
  * Emulator: Fixing current issues: [#467](https://github.com/processing/processing-android/issues/467), [#474](https://github.com/processing/processing-android/issues/474), and maybe adding some useful new features such as the possibility to set some emulator parameters more easily (i.e.: resolution, etc).
  * Structure of the core library and contributed library template: The organization of the core library for Android largely follows that of the core library in the Java mode, however, this structure does not follow the current Android conventions for library projects, thus making it harder for Android developers to contribute to the project. Some steps have been taken to address this issue, such as the use of Gradle to build the core library and the mode, and the inclusion of a "debug" Android Studio project that allows debugging the core library from Android Studio. However, this organization is not typical of Android library projects, and could be made more standarized. Same issues affect the Processing library template for Android, which has been recently updated to be compatible with Gradle and Android Studio but still uses a non-standard structure.
* Expected Outcomes: Up-to-date SDK and emulator installer/updater, more standarized code structure of core library and library template.
* Skills Required: Github, Android development
* Possible Mentors: Cristian Mosquera, Sarah Lensing, Andres Colubri
* Difficulty: intermediate, advanced

### + Update OpenGL renderer to use OpenGL ES 3.0 and GLSL 3.0
Currently the OpenGL renderer in the Android mode uses OpenGL ES 2.0 and GLSL 2.0. With OpenGL ES 3.0 support at [over 70%](https://developer.android.com/about/dashboards/#OpenGL) across devices, this is a good time to update ([issue #515](https://github.com/processing/processing-android/issues/515)).
* Expected Outcomes: Updated core OpenGL library in Android mode
* Skills Required: Android development, OpenGL ES, GLSL
* Possible Mentors: Andres Colubri
* Difficulty: advanced

## Processing Python

### + Native Python and Processing (Priority)
We have started work on [a native (C Python) version of Processing](https://github.com/p5py/p5). While it doesn't have the advantage of library support that we get from the current Jython-based implementation, it opens up other ways to extend Processing with Python's syntax, features (numpy, scipy), and considerable base of support. This has been developed by Abhik Pal during Summer of Code 2017 and 2018 as [p5py](https://p5py.github.io/). We hope to make additional progress in this exciting work in 2019.
* Expected Outcomes: Add missing features to bring it on par with Processing (Java) API, performance improvements and optimizations especially on Mac/Linux, code examples and documentation. 
    * Improve OpenGL Rendering to support high res displays [#19](https://github.com/p5py/p5/issues/19) - Explore moving tessellation of shapes to OpenGL (similar to Processing Java)
    * Improve Shape class to support `beginContour()`, `endContour()`, SVG support, etc to bring it up to par with Processing Java
    * Add support for `smooth()`, `stroke_cap()`, `stroke_join()`, etc. Will require knowledge of OpenGL shaders.
    * Improve font support and build on the prototype from last year. Large parts will have to be rewritten as last year's prototype was not very efficient.
    * Add video and sound support.
    * Investigate porting popular Processing libraries to p5py
    * Any other new ideas welcome!

* References:
    * [p5py](https://github.com/p5py/p5)
    * [GSoC 2018 Work Report Report(release notes)](https://p5.readthedocs.io/en/latest/releasenotes/0.5.0.html)
    * [Abhik Pal's GSoC 2017 blog post](https://abhikpal.github.io/blog/2017/08/27/p5-google-summer-of-code-progress-report)
    * [GSoC 2017 API Progress (Google Sheets)](https://docs.google.com/spreadsheets/d/1kFdCCZfsZJ1BB84zwK0Q4CP2GZavBVxGdVjhQUG5Hpw/edit?usp=sharing)

* Skills Required: Python, OpenGL
* Possible Mentors: Abhik Pal, Manindra Moharana
* Difficulty: advanced

# Ongoing Projects

## Processing

### OpenGL Ideas
* Right now, editing of GLSL shaders is not supported by the PDE. An external tool allowing to code shaders side by side with the sketch code could be very useful and cool.
* Central repository of shaders, ideally linked with the editor. We could also incorporate support for a shader interoperability spec, such as the [Interactive Shader Format](https://www.interactiveshaderformat.com/), which would allow Processing users to share shaders with other applications for creation of interactive graphics. 
* An advanced shader tutorial following the introductory one [here](http://processing.org/tutorials/pshader/) is needed.
* A library for advanced shaders (lighting, geometry, tessellation), that handles the low-level stuff. Right now it is possible to create geometry or tessellation shaders by using the [GL3/GL4 API](https://github.com/codeanticode/pshader-experiments/blob/master/TerrainTess/GL4Shader.pde), but would be nice if that could be handled automatically by this hypothetical library. Also integration with the repository suggested above would be neat.
* A library to do calculations on the GPU using the OpenCL API. This library could work in coordination with the OpenGL renderers to allow handling large particles systems, very complex dynamic meshes, etc. A prototype OpenCL library for an early Processing 2.0 alpha release, which implemented traer.physics solvers with OpenCL kernels, is available [here](https://code.google.com/p/clphysics/).

### Libraries
* Is there something you think Processing should do, but it currently doesn't?  Processing can be extended through [Libraries](http://processing.org/reference/libraries/) and we're always looking for contributions.  Instructions for building libraries are here on the [GitHub wiki](https://github.com/processing/processing/wiki).
* The libraries that allow Processing to communicate with the MS Kinect could use work and updating. See: includes [openkinect](https://github.com/shiffman/OpenKinect-for-Processing).
* The [Toxiclibs](https://github.com/shiffman/toxiclibs) has been updated for Processing 3, but there is work that could be done to fix bugs, improve documentation and examples, and keep aligned with [toxiclibs.js](http://haptic-data.com/toxiclibsjs/).

### Tools for the Processing Development Environment (PDE)
* There's an [extensive list of potential tools](https://github.com/processing/processing/wiki/Tool-Ideas) on the Processing Wiki that are waiting to be programmed. Instructions for building tools are here on the [GitHub wiki](https://github.com/processing/processing/wiki/Tool-Overview).
    
### Smaller, Isolated Projects and Fixes
There are a number of smaller projects that could be handled by someone who doesn't necessarily want to dive all the way in to the code. Often these are isolated things that we've just never had the time to get around to. We track many of these with the [help label](https://github.com/processing/processing/issues?q=is%3Aopen+is%3Aissue+label%3Ahelp). Please help!

## Processing for Android

### Android Ideas
* Incorporate support for the Kotlin language, which is very popular among Android developers, either as part of the Android mode, or as a new mode.
* Translations: The Processing for Android [website](https://android.processing.org/) is available at this moment in Spanish and English, so translations into other languages are needed. The Android mode's UI is in English, but recent work has been made recently to put all the message strings in a [separate language file](https://github.com/processing/processing-android/blob/android-0274-v4.1.0-beta3/mode/languages/mode.properties) to facilitate translation of the UI into other languages.
* New tutorials: Currently, the website includes a number introductory tutorials on a range of topics (installation, sensors, VR), but we need new tutorials bridging the gap from simple applications to more advanced topics.
* Video/Media library for Processing Android? This would probably wrap the [media engine](http://developer.android.com/reference/android/media/package-summary.html) and [player](http://developer.android.com/reference/android/media/MediaPlayer.html) already available in Android. A former GSoC student developed a [video library](https://github.com/omerjerk/processing-video-android) for the Android mode, supports video playback and camera capture through OpenGL textures for good performance. Perhaps it can be continued/expanded. 

## Processing for iOS

### Kotlin Native
Jetbrains is putting a significant amount of energy into this project which allows developers to compile Kotlin not only to the JVM but also to [LLVM-based backends](https://kotlinlang.org/docs/tutorials/native/mpp-ios-android.html). The Android community has already accepted [Kotlin](https://en.wikipedia.org/wiki/Kotlin_(programming_language)) as the defacto language to develop in and major libraries are being ported to be multiplatform. Processing could be amongst those early adopters. The first step would be to migrate the Processing Android library to Kotlin. Then split the Android specific logic from plain Java. Next, restructure to a ["multiplatform" library](https://kotlinlang.org/docs/tutorials/multiplatform-library.html) with one platform implementation (JVM) and a common Kotlin interface. After that is done, an iOS platform implementation with stubbed methods could be added and gradually built out. This is a big project with risk involved using features that are still considered "experimental". The following code templates can be useful to get started with this project:

Kotlin Multiplatform Project (MPP) Processing library: https://github.com/sarahlensing/kotlin-mpp-processing-lib

Kotlin Multiplatform Project (MPP) Processing app: https://github.com/sarahlensing/kotlin-mpp-processing-app

* Expected Outcomes: Kotlin multiplatform implementation of Processing for Android with some reasonable percentage of the APIs implemented on iOS 
* Skills Required: Kotlin, iOS development 
* Possible Mentors: Sarah Lensing, Andres Colubri
* Difficulty: advanced technical