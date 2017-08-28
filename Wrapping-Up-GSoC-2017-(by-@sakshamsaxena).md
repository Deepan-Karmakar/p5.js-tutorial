# Wrapping up GSoC 2017 with p5.js (by [@sakshamsaxena](https://github.com/sakshamsaxena))


## Summary

There were 3 major tasks that were proposed to pursue this summer under Google Summer of Code 2017 with p5.js under The Processing Foundation. All these focussed on improving the infrastructure and operations of the library, independent of the library API itself. To better tackle and organise new Issues, an Issue Template was implemented, which saw immense utility for contributors and owners to address new Issues. A new Grunt Task using Browserify was created which takes in the desired components that one wants to utilise as arguments, and built the library consisting of those components only. Dedicated Grunt Tasks were written to automate the release process end-to-end with minimal user interaction. The outcome of these tasks was improved developer operations (via Issue Templates and Release Process Automation), and improved library accessibility (via the Modularisation Task).

## Task Details

### 1. Adding Issue Templates

Reporting Bugs or Feature Suggestions by the Community through Issues is also a significant contribution to the Project and it catalyses the growth of Project through them. Relevant responses and discussions in context to those, delivered in a short time, further engages the community into the Project. The GitHub Issue Template was [added](https://github.com/processing/p5.js/commits/master/ISSUE_TEMPLATE.md?author=sakshamsaxena) as my first contribution under GSoC on June 12, and till date it has been proven to be extremely helpful to both the reporter as well as responder, meanwhile aligning to it's original aim.

