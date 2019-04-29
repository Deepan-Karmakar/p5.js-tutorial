Welcome! This page contains a list of ideas and how you can help contribute to the [Processing Foundation's](https://processingfoundation.org/) work on [p5.js](http://p5js.org) for Google Season of Docs.

For all of our projects, it's incredibly important that things are kept as simple and user-friendly as possible. Our work is not for developers, it's for people who are less familiar with code, and/or just want to get things done. We're especially interested in documentation projects that lower the barrier to entry for new users or contributors and make it easier for them to get started.

In addition to this list, we track specific bugs and enhancements via github issues:
* [p5.js](https://github.com/processing/p5.js/issues)
* [p5.js website / documentation](https://github.com/processing/p5.js-website/issues)
* [p5.js web editor](https://github.com/processing/p5.js-web-editor)

## Google Season of Docs 2019

_**If you have questions about an idea or need guidance on forming your proposal, please post to the [Processing Forum](https://discourse.processing.org/c/season-of-docs). This is the best way to get feedback and develop your idea. This makes it possible for everyone to learn from your questions and contribute their thoughts.**_

## Project Ideas

[p5.js](http://p5js.org) is a JavaScript library that starts with the original goal of Processing, to make coding accessible for artists, designers, educators, beginners, and reinterprets this for today's web. Using the original metaphor of a software sketchbook, p5.js has a full set of drawing functionality. However, you’re not limited to your drawing canvas, you can think of your whole browser page as your sketch! p5.js has addon libraries that make it easy to interact with other HTML5 objects, including text, input, video, webcam, and sound. p5.js is a new interpretation of Processing, not an emulation or port, and it is in active development.

### + New contributor onboarding experience
This project involves thinking about the experience for new contributors to the project. How can the README, developer_docs, and other documentation be improved to make it easier for new people to contribute, especially those without deep experience coding or contributing to open source? This may also involve looking at github community communications and implementing structures that enable new contributors to get help in making their first pull requests.
* Expected Outcomes: Update of contributor docs, implementation of new community practices for facilitating beginners in contributing.
* Possible Mentors: Stalgia Grigg
* Skills Required: JavaScript, GitHub, communication skills
* Difficulty: beginner, intermediate, or advanced

### + Project navigation for contributors
In 2018 working with one of our Fellows, Vijith Assar (https://medium.com/processing-foundation/a-p5-js-dissection-manual-38959ff8522e), we began to add documentation throughout the github repository to aid in project navigation. This resulted in readme files in `src/` directory folders like [this](https://github.com/processing/p5.js/tree/master/src) and [this](https://github.com/processing/p5.js/tree/master/src/core), as well as a readme in the [developer_docs/](https://github.com/processing/p5.js/tree/master/developer_docs) directory that outlines the project structure. The goal of this project would be to extend this documentation to more of the repository, so it's easier for contributors to navigate the project and understand the purpose of the various files and pieces of code.
* Expected Outcomes: Update of contributor docs, implementation of new community practices for facilitating beginners in contributing.
* Possible Mentors: Lauren McCarthy
* Skills Required: JavaScript, GitHub, communication skills
* Difficulty: intermediate or advanced


### + Internationalization improvements
Currently the p5.js website supports translations for Spanish and Simplified Chinese. Both of these could use updated translations for sections of the text. [This page gives an overview of the translation process.](https://github.com/processing/p5.js-website/blob/master/contributor_docs/i18n_contribution.md) Alternatively, a participant might propose adding another language that is not currently supported.
* Expected Outcomes: Update of p5js.org translations, or addition of a new language
* Skills Required: Fluency in a second language besides English, JavaScript, familiarity with Github or version control
* Difficulty: beginner, intermediate, or advanced

### + Improve Friendly Error System (FES) and documentation
The Friendly Error System (FES) is a system designed to help new programmers with common user errors as they get started learning. It catches common beginning errors and provides clear language and links to help a user resolve the error. This project would involve improving the FES documentation. This might mean things like updating the [FES developer doc](https://github.com/processing/p5.js/blob/master/developer_docs/friendly_error_system.md), and adding comments inline to [the code](https://github.com/processing/p5.js/blob/master/src/core/error_helpers.js). Another big goal we have is to [add internationalization/localization to the FES](https://github.com/processing/p5.js/issues/3390) so error messages may be given in different languages.
* Expected Outcomes: Improvement of p5.js FES and documentation
* Skills Required: JavaScript, familiarity with Github or version control
* Possible Mentors: Evelyn Masso
* Difficulty: intermediate, advanced
