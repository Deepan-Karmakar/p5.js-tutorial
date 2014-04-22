## Design Principles for p5.js

- **Beginner Friendly** The p5.js API aims to be friendly to beginner coders, offering a low barrier to creating interactive and visual web content with cutting-edge HTML5/canvas/DOM APIs.

- **Educational** p5.js is focused on an API and curriculum that supports educational use, including a complete reference to the API with supporting examples, as well as tutorials and sample class curricula that introduces core creative coding principles in a clear and engaging order.

- **JavaScript and its community** p5.js aims to make web development practices more accessible to beginners by modeling proper JavaScript design patterns and usage, while abstracting them where necessary. As an open source library, p5.js also includes the wider JavaScript community in its creation, documentation and dissemination.

- **Processing and its community** p5.js is a direct response to the Processing language and it's community, and aims to make the transition from Processing to JavaScript easy and clear.  Supporting the Processing API and community is a priority for p5.js, while also expanding to include the new possibilities of creative coding on the web, and taking a Processing-style approach to exposing that API to beginners.

## How is p5.js different from Processing.js?

The main goal of Processing.js is to execute Processing files in HTML5, but not necessarily to write native HTML5. It supports a mixed syntax of Processing and JavaScript, where the JavaScript is not really meant to be consumed by the end-user. Processing.js is a port of Processing to JS, using regex to convert Java into JS. It is a good tool for those that want to run simple sketches on the web, however, it is quite opaque. It can be difficult for someone to understand how it works, how to fix things when it doesn't work, or how to modify or extend the library. As Processing.js says on their website, "it's not magic, but almost."

In contrast, with p5 we are reimagining Processing's original goals in native JavaScript, in a way that is intended to be transparent and intuitive. It is easy to translate a sketch from Processing to p5 and the process of doing so begins to teach people the basics of JS. From there, they are able to begin writing native JS using a syntax that feels familiar but appropriate for the context. We are closely studying the decisions Processing has made, but also always questioning to see if there are design decisions that would make the library cleaner, stronger, and more intuitive. 

Additionally, p5.js extends beyond canvas drawing to allow people to create, access and manipulate other HTML elements. Through this framework beginners begin to explore and understand HTML, JavaScript, and CSS, and the way they work together in the browser. p5.js will also have a system for people to contribute addon modules to deal with things like audio, video, various input devices, and data. There is also an option to use p5 globally or instantiated within a namespace, so it can be compatible with other JS libraries. 

Most importantly, this project is in active development, with enthusiastic support and contributions from around the world. We have begun working with various schools and institutions to teach workshops and classes, in hopes of integrating it into curriculums as a tool for understanding the web.

We are also putting a lot of energy into making the documentation clear, for developers as well as users. We'd like this to be a project that anyone feels welcome and empowered to be a part of, whether that's contributing documentation, writing code, teaching with it, or using it to create.
