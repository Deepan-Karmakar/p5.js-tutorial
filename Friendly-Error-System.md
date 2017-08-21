The goal of the friendly error system (FES) is to create accessible error messages to supplement the often cryptic console errors. They are color coded, written in natural language, linked to documentation, and assume a beginner level. The errors are triggered in multiple files through out p5.js, but most of the work and error writing happens in: `src/core/error_helpers.js`. 

Two main features are:
#### `core/error_helpers/friendlyFileLoadError()`: 
* This function generates and displays friendly error messages if a file fails to load correctly. 
* This can be called through : `p5._friendlyFileLoadError(ERROR_TYPE, FILE_PATH)`.
* Currently version contains templates for generating error messages for `image`, `XML`, `table`, `text`, and `font` files.
* Implemented to `image/loading_displaying/loadImage()`, `io/files/loadFont()`, and `io/files/loadTable()`.

#### `core/error_helpers/validateParameters()`:
* This function runs parameter validation by matching the input parameters with information from `docs/reference/data.json`, which is created from the function's inline documentation. It checks that a function call contains the correct number and the correct type of parameters. 
* This can be called through: `p5._validateParameters(FUNCT_NAME, ARGUMENTS)` 
or, `this._validateParameters(FUNCT_NAME,  arguments)` inside the function that requires parameter validation.
* Implemented to functions in `color/creating_reading`, `core/2d_primitives`, `core/curves`, and `utilities/string_functions`. 

## Current Features
* Welcomes the developer to p5 and the friendly debugger. 
* They work in the IDE and the web editor. 

## Notes for developers
* Inline documentation: 
* When creating p5.js Objects: any p5.js objects that will be used for parameters will need to assign value for `name` parameter (name of the object) within the class declaration.

## Known Limitations
* The friendly error system slows the program down, so there is an option to turn it off via setting `p5.disableFriendlyErrors = true;`. In addition, the friendly error system is omitted by default in the minified (p5.min.js) version.
* Only detects an error in loadXML and loadTable when the file is requested as a url and not as a file path. I think this has to do with the reqwest library as documented here: https://github.com/ded/reqwest/issues/177

## In The Works


## Thoughts for the Future
* Having a Spanish translation available.
* All the colors are checked for being color blind friendly. 
* A more elaborate ascii welcome! 
* Global Error catching. It would be very helpful to catch the errors the browser is throwing to the console, so we can match them up with friendly comments. So far we've tried window.onerror and the following with no success. 

     var original = window.console;
      
     ["log", "warn", "error"].forEach(function(func){
     window.console[func] = function(msg) {
      original[func].apply(original, arguments)
     };
* Checking that a number positive for nf() nfc() nfp() nfs()