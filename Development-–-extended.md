[THIS IS A ROUGH DRAFT]

Writing this outline thinking about someone who is comfortable programming and posting their code on github, but who hasn't worked on a larger collaborative project before. So this extended guide won't assume knowledge of unit testing, inline documenting, or Javascript deployment workflows. It will also be more self-contained than the quick dev guide (no need to open other pages to get an idea of what the mentioned tools are for) 
///does this approach make sense?

OUTLINE

Link to quick guide.
 
Present helping with documentation and tests as a good way to get familiarized with p5's structure; then fixing bugs and adding features. 

List ways to contribute: 
- **Help us document.** Explain that doc site will be auto-generated, and only as complete as inline doc. Point to src folder. Link to details below.  
- **Help us test.** brief description of unit testing. Point to tests folder. Link to details below.
- **Fix a bug.** Explain how Issues list is used in this project. 
- **Add a feature.**

Setting up: 
- start from beginning: fork repo and add upstream remote (and link to tutorial).
- explain why distribution needed: p5 runs in browser. browser gets library from server. can’t start running until all files have been transferred —> distribution. p5.js: all files combined into one. p5-min.js: one file w/o unnecessary spaces and line breaks. not readable, but faster download. 
- explain why grunt: javascript is interpreted, not compiled. p5 fairly big project --> series of steps to generate distribution and also do some quality control: syntax checking (and good practices? check what lint does), running tests. repetitive task, so automated. task runner: grunt. to install grunt: package manager.

- specific setup instructions will be the same, but adding details like ‘Open Terminal’. 

Writing code:
- one sentence about style guide, representative snippet of code for quick reference.
- one sentence about jsdoc, snippet of code for quick reference. 

Testing:
- explain what the tools are before going over specific steps.
- include test snippet.

