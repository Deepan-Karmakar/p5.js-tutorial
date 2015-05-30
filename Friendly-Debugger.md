The goal of the friendly debugger is to create accessible error messages to supplement the often cryptic console errors. They are color coded, written in natural language, linked to documentation, and assume a beginner level. The friendly debugger slows the program down, so it is only included in p5.js and not in p5.min.js

The errors are triggered in multiple files through out p5, but most of the work and error writing happens in:
src/core/error_helpers.js

## Current Features
* Checks that a function call contains the correct number of parameters.  
* Checks that a function call contains the correct type of parameters.  
* All the colors are checked for being color blind friendly. 
* Provides an error if a file fails to load correctly. 
* Welcomes the developer to p5 and the friendly debugger. 
* They work in the IDE. 

## Known Limitations
* It throws an error incorrectly when a function has multiple types it accepts. This comes up for image when you create graphics rather than. 
* Only detects an error in loadXML and loadTable when the file is requested as a url and not as a file path. I think this has to do with the reqwest library as documented here: https://github.com/ded/reqwest/issues/177

## In The Works
* Having a spanish translation available. 
* A more elaborate ascii welcome! 

## Thought for the Future
* Global Error catching. It would be very helpful to catch the errors the browser is throwing to the console, so we can match them up with friendly comments. So far we've tried window.onerror and the following with no success. 

     var original = window.console;
      
     ["log", "warn", "error"].forEach(function(func){
     window.console[func] = function(msg) {
      original[func].apply(original, arguments)
     };

* Checking that a number positive for nf() nfc() nfp() nfs()
* Having the needed parameters only specified in the comments above the function. Rather than twice: once in the function and once above the function in the comments.  