

_This is a draft update to the p5.js JavaScript Basics tut. I will probably finish it by mid-Feb, hopefully earlier. Mainly just to add some extra detail that I have found useful when coding in p5.js. When done, I will signal that here and request review by Lauren and anyone else interested. Cheers, Greg E._

_**Previous version being updated from top down. Progress marked by "Updated down to here". Areas needing more work flagged as "Needs more work" or similar - in bold anyway.**_

JavaScript is a language that is typically used on web pages where it runs client-side (within the web browser). It is a general purpose language with a lot of built-in functionality for interacting with HTML elements on a webpage and responding to actions initiated by the user. It is described as one of the "core three" technologies that drive the Web: HTML, CSS, and JavaScript.

Although JavaScript has "Java" in it's name, it isn't related other than by the fact that it looks something like Java. It is allegedly based on the languages Self and Scheme, but with a Java or C++ appearance. JavaScript's official name is ECMAScript (ECMA is the European Computer Manufacturers Association, a standards body). It was initially created by Netscape Communications. ([Wikipedia: JavaScript](http://en.wikipedia.org/wiki/JavaScript))

JavaScript has an interesting history. It was created in 1995 by Brendan Eich in 10 days ! to provide an urgently-needed web scripting ability at Netscape, but unexpectedly took off as part of the late 90's explosion of the Web. Since then it has matured into a fully-functioned language, used in client-side Web code, server-side code, and many types of general code having nothing to do with the Web. It is usually placed in the top 3, and often at the top, in surveys of "languages most used", "languages most required in job ads" etc. Time spent learning JavaScript could be time well spent! 
 


# `<script>` tag

JavaScript can be placed anywhere within an HTML document, although it is typically included in the `<head>` section of the HTML, and is specified by the use of `<script>` tags:

```html
<html>              
  <head>              
    <script type="text/javascript">              
      //JavaScript goes here 
      str = "This is my first message";                                    
      console.log(str);  // This will show up in the browser's JavaScript console. 
      alert(str);        // This will show a popup message in the browser. Use sparingly!
    </script>
  </head>              
<body> 
  This is totally plain raw text, the browser will show it in a default font/colour/size.
</body>             
</html>              
```
If you put the above text in a file 'index.html', you can open it, eg. by just clicking on it in a "file browser" dialog window, in Windows/MacOS/Linux. 
	
You can also write JavaScript in a file external to the HTML and point to that file in a script tag. There can be more than one script. They can also be fetched from the Web.

```html
<script type="text/javascript" src="myProcessingCode.js"></script>                    <!-- this is an HTML comment -->
<script type="text/javascript" src="libraries/p5.js"></script>                        <!-- Our p5 library ! -->
<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.2.1.min.js"></script>    <!-- JQuery, a popular utility lib -->
```
Note, the 'type="text/javascript"' is not needed in the latest browsers, JavaScript is now the default script type.

# Console

One of the first things we probably want to learn is how to get debugging output. You can write to the console by using the built-in console.log method:
```javascript
console.log("hello");
console.log("variables x, y values", x, y);          // Use the default space separation of args
console.log("variables x, y values " + x + " " + y); // Concatenate message into a single string, more flexible
```
In order to see the console on Chrome, select menu sequence View > Developer > JavaScript Console. Use it often! On other browsers, just search for info on "how to open the JavaScript console on \<whatever\> browser". Note also that Processing has a "print()" function which does a similar job to console.log().

# Variables

A variable holds a value in memory. It can be used in calculations, composing some kind of message, updating the appearance of a web-page component, controlling the appearance of a Processing visual entity (very relevant here!), countless things. Variables are a fundamental part of programming languages, like words are part of spoken languages.

A quick swing through setting up variables:

```javascript
var x = 5;
var y = x + 7;                   // y is now 10

var a = "some text"; 
var b = a + " is here";          // b is now "some text is here". Note the + has a different function for strings

var stuff = [1, 22, 333];        // stuff is a three element array, with the values shown
var s = data[2];                 // s is 333. Note indexing from zero, not one.

var myRecord = { givenName:"Albert", familyName:"Einstein", age:33 };  // Create an "object" with three key:value pairs
var name = myRecord.givenName;   // name has string value "Albert"

var delete_file = false;         // var has a Boolean value "false".
var keep_file = !delete_file     // keepFile has Boolean value "true". (! means negate). Useful for binary options.

var string1 = "";                // One (good) way to initialise a string to an empty value.
var string2 = null;              // Another way. Be careful, null has tricky properties, see later.
var string3;                     // Both this ...
var string4 = undefined;         // ... and this give the var the "undefined" value. Also very tricky, see later.

```
Variables should always be given an initial value. Otherwise, like string3 above, they have an "undefined" value until later in the program, which can lead to hard-to-debug errors.


Variables (and other names in JS, like functions) can be named with lower and uppercase letters, numbers, underscore, or dollar signs. Avoid dollar signs. For multi-component names, there are two favourite styles: my_data and myData. The second is more common. Underscores at the beginning or end of a name can denote something special, often a variable which is similar to a system-provided term. Eg. you desperately want to name some variable "var" but var is a reserved word in JS, so you can use "var_". `var var_ = 123;` Unless you know very well what you're doing, this is not recommended. 


## Data Types

JavaScript is a "loosely typed" or "dynamic" language, meaning you don't have to declare the types of variables ahead of time. The type will get determined automatically while the program is being processed. Other languages such as Java, C, C++ are strictly typed and each variable must declare the type of the data it will contain. Even though you don't have to declare types, JavaScript does have different data types.



### Data type: Number

A number, optionally with a decimal point. In other languages this is typically called a float, short for "floating point number". It can be written with or without the decimal point.

```javascript
var x = 5;
var y = 1.223;
var z = -300;
var big = 1.23e82;   // This is a big number, the estimated atoms in the universe, but quite ok to code with, why not?
var small = 1.6e-35  // The Planck Length, the smallest physical size (in metres) that has any meaning in classical physics.
```
JavaScript stores all numbers as 64-bit floats. This is very accurate but still has limits. Sometimes it can lead to very small inaccuracies. Try this in the JavaScript console: `0.362 * 100`  You should get the answer 36.199999999999996. This is rarely a problem in practice, after all it's accurate to 1 part in 100 quintillion, usually pretty ok ! 

Although JavaScript doesn't have a specific integer type, it uses special measures to keep integers 100% accurate where possible. Integers up to a magic value of 9007199254740991 (and down to -9007199254740991) are stored and computed with complete accuracy. (9007199254740991 is 2^53 -1, ie. 2 to the power 53, minus 1. This is because the integer is held precisely, in the 53-bit mantissa section of the 64-bit IEEE float word).

This means that counting and looping code will always work correctly. A loop like ` (for i = 0; i < 1000000; i++) ` will stop exactly at the million'th iteration. It won't blow up with 999999.999999996 or 1000000.000000003 issues.


### Data type: String

A series of characters. These can be defined with either single or double quotes. To include a quote character, use the other type of quote around the string. Or use a backslash to escape the quote.

```javascript
var x = 'hello';
var y = "maybe tomorrow";
var fancy = "we need some 'single quotes' in here";
var fancy2 = "strings can have \' and \" quotes inside"; 
```

There are a large number of useful built-in JavaScript properties and methods that let you manipulate strings. You can see them all [here](http://www.w3schools.com/js/js_string_methods.asp), and also [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/). These two sites, the www3schools site, and the Mozilla Development Network (MDN), are good references. A few of the most useful String methods follow:

**length**

Gives the length of the string. Note, this is a direct "property" of the string, always maintained by JS, not a callable method. So no function call() syntax is needed, just string.length. This is a common mistake when working with strings. If you are having weird errors around a use of some mystring.length code, make sure you are not typing mystring.length().


```javascript
var str = "I like to eat pickles"
console.log(str.length); // 21
```

**indexOf(str)**

Returns the index of (the position of) the first occurrence of a specified text in a string. Returns -1 if the search string is not found. All these methods return an indicator if the method fails, see the documentation. This is a callable () method, JS can't precompute anything about this request. 

```javascript
var str = "I like to eat apples.";
var pos = str.indexOf("eat");   // pos is 10
pos = str.indexOf("pears");     // pos is -1
```

**lastIndexOf(str)**

Returns the index of the last occurrence of a specified text in a string. Sometimes the interesting info is the last occurrence of something in a string.

```javascript
var str = "long.complicated.filename.txt";
var suffixPos = str.lastIndexOf(".");  // 25
```
**includes(str)**

This method just returns whether the string contains a smaller string, true or false.

```javascript
var str = "reallycrazylongstring";
var maybe = str.includes("zylo");  // returns true
```


**substring(start, end)**

Extracts a part of a string and returns the extracted part in a new string. The method takes 2 parameters: the starting index, and the ending index.

```javascript
var str = "I like to eat apples.";
var newStr = str.substring(2, 6);  // "like"
```

**substr(start, length)**

Another variation. It takes 2 parameters: the starting index, and the length required. Murphy's Law of Programming says you'll always use one when you meant the other.

```javascript
var str = "Bananas are yellow";
var newStr = str.substr(2, 5);    // "nanas"
```

**toLowerCase(), toUpperCase()**

These functions convert the string to all lower or all upper case.

```javascript
var str = "I like to eat apples.";
var lowerStr = str.toLowerCase();
console.log(lowerStr); // "i like to eat apples."
var upperStr = str.toUpperCase();
console.log(upperStr); // "I LIKE TO EAT APPLES."
```
**split(separator)**

This splits a string into an array of substrings, based on the separator, which can be one character or several.

```javascript
var str = "a.multi.part.filename";
var result = str.split(".");   // result is a 4 element array, ["a", "multi", "part", "filename"]
console.log(result[2]);        // prints "part"

var str = "some; data; structured; like; this";
var result = str.split("; ");  // result is a 5 element array, ["some", "data", "structured", "like", "this"]
console.log(result[3]);        // prints "like"
```
**join(separator)**

We are jumping ahead to an array method here. The logical opposite of a "split" operation is a "join". These twin operations are available in most languages. In JS arrays have a join() method.

```javascript
var str = "cool.image.jpg";
var result = str.split(".");      // result is a 3 element array, ["cool", "image", "jpg"]
var newstr = result.join("-");    // newstr is a string "cool-image-jpg"
var newstr = result.join("...");  // newstr is a string "cool...image...jpg"
```

**trim()**

This method trims whitespace from both ends of a string. Whitespace includes space and tab characters, also CR and NL/LF, and also some uncommon characters like FormFeed and VerticalTab. (Uncommon these days, but common enough in the 50's, 60's, 70's when giant line-printers spewed out reams of 132 character wide line-printer pages. Oh I remember it well. Ok not the 50's or 60's).

```javascript
var str = " string with spaces around          ";
var result = str.trim();   // result is "string with spaces around" (not any more)
```

**trimLeft(), trimRight()**

These are more specific versions which trim whitespace only from the left or right of a string. These are not 100% standard, although very common extensions in JavaScript. For maxiumum robustness and portability of code, you could code these yourself as private utility functions, very easy. Or you could just check they work in your preferred browser and not worry. Here's a suggested code from MDN for replacing trim(), you can modify it to create a trimLeft or trimRight. This uses a regexp call, a "regular expression", a miniature language in itself, and very powerful.

```javascript
if (!String.prototype.trim) {                                       // we don't have trim(), rats
  String.prototype.trim = function () {                             // add a local version
    return this.replace(/^[\s\uFEFF\xA0]+|[\s\uFEFF\xA0]+$/g, '');  // trim all crazy whitespace off both ends
    //  this.replace(/^[\s\uFEFF\xA0]+/g, '');                      // for trimLeft
    //  this.replace(/[\s\uFEFF\xA0]+$/g, '');                      // for trimRight
  };
}
```

There are many more String functions but the above would be 98% of what you need in p5.js.


### Data type: Boolean

A "true" or "false" value. Boolean variables are often used for conditional testing and keeping track of state. Things that need to be on or off, done or not done.

```javascript
var drawBackground = true;
var drawDebugInfo = false;
```

### Object

An object can be thought of as a collection of properties. These properties can be values of any type, including other objects, which enables building complex data structures. Arrays are a special type of object, more on this later.
* Read more [about arrays](https://github.com/processing/p5.js/wiki/JavaScript-basics#arrays)
* Read more [about objects](https://github.com/processing/p5.js/wiki/JavaScript-basics#objects)

**Need to expand Array and Object here**

### Null and undefined

The value of a variable which has not been given any value is `undefined`. This is a specific single type which you can also assign manually. Variables can be emptied by setting the value to `null`. This is another specific single value. Often it's better to avoid these, JS does some unexpected things with them.

```javascript
var cars;               // value is 'undefined'
var trucks = undefined; // Same
var person = null;      // value is `null`

var count = 0;          // Often safer
var message = "";       // Ditto
var newArray = [];      // Safe
var newObject = {};     // Safe
```
Creating new "empty" things in JS is surprisingly clunky. It's slightly hard to know what you have done with a statement like `var myArray = []`. Go to the JS console and type it, then just type "myArray". JS will compute the expression, which is a single array, with no useful effect, ie. no assignment to anything, but that's fine, and display a breakdown of what it is, ie. an array with no elements, length 0. You can hit the disclosure triangle for more detail if there is one. Try again with `myArray = [1,2,3]`. You'll get the picture quickly. Also try `var myObj = {}` and `myObj = {"alpha":1, "beta":2}`.

## Assignment

Once variables are declared, you can assign values to them and use them in operations.

```javascript
var x = 5;
x = x * 5;        // x now 25
x = "cat";        // You can change the type of a variable anytime, here number to string
var y = x + "s hate dogs";  // y is "cats hate dogs". Note + is the only math operator that has been hijacked for string use.
var z = x - "t";  // Result is NaN (Not a Number), not "ca". It totally blew up! Brilliant.
```

# Operators

We will zoom through the operators here. We assume some teensy maths background in the reader.

### Assignment
* `=`
* `a = b = c = 123;`       // Multiple assignment is allowed but unwise. [Details.](https://www.undefinednull.com/2014/02/03/multiple-left-hand-assignment-in-javascript-is-really-bad-think-once-before-you-do-it/)

### Mathematical
* `+` addition
* `-` subtraction
* `*` multiplication
* `/` division
* `**` exponentiation: 3**3 gives 27. New in EcmaScript 6.
* `%` modulo
* `++` add one shorthand
* `--` subtract one shorthand

These operators have shortcut styles, occasionally useful.
* `a = 1` 
* `a += 5`  Same as a = a + 5. a now 6
* `a -= 4`  a now 2
* `a *= 7`  a now 14
* `a /= 2`  a now 7
* `a %= 2`  a now 1
* `b = a++` b is 1, a is 2, ie. the ++ was done after the assignment
* `b = ++a` b is 3, the ++ was done before the assignment. Similarly --. Use these sparingly, "out by one" oversights happen easily.

### Relational, ie. comparisons
* `>=` greater than or equal to
* `<=` less than or equal to
* `==` equal to 
* `!=` not equal to 
* `===` equality with strict type checking, safer
* `!==` inequality with strict type checking, safer

### Logical, ie. Boolean logic combos
```javascript 
* ||  logical OR              // if ( feelingTired || reallySleepy ) { lieDown(); }
* &&  logical AND             // if ( haveWallet && (money > 10) ) { buyBeer(); }
* !   logical NOT             // showDebugInfo = ! inProductionMode;
```

### Precedence of operators

The operators have a precedence which vaguely matches what we learned in school.  When operators have equal precedence, they proceed left to right. `xx = 24 / 6 * 5` will produce 20. But `xx = 1 + 2 * 3` will produce 7, not 9, because the multiplication will get done first. To force the order you want, use brackets, which have the highest precedence. 
```javascript
xx = (1 + 2) * 3           // will produce 9.  
gravity = G * (mass1 * mass2) / (distance * distance);  
intensity = light / (Math.sqrt( radius * radius) + fudgeFactor); 
```
Other operators have progressively lower precedence. Full table [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence). This allows you to write most expressions in a natural and  concise way. 
```javascript
if( radius > 5.0 && radius < 10.0) { drawCircle(); }               // works fine, but ...
if( (radius > 5.0) && (radius < 10.0) { drawCircle(); }            // clearer and safer. 
```
The lowest operator is a strange thing called the 'comma' operator. You can pack several statements into one. The most common use is in a slightly more fancy 'for loop'.
```javascript
for (var i = 0, j = 9; i < 9; i++, j--) {  // i runs up 0 to 9, j runs down 9 to 0
  console.log( a[i][i] );                  // Print the conventional diagonal elements of a 9x9 array
  console.log( a[i][j] );                  // Print the other diagonal, top-right to bottom-left, of the array
}
```
Some traps exist. No precedence order can be what you want all the time. An example from p5.js:
```javascript
var images = [];
for (var i = 0; i < 10 ; i++) {
  images[i] = createImage(width, height);
  images[i].loadPixels();    // Ok? Noooo. The member access ".loadPixels()" has higher precedence than the array index, so gets called
                             // on the entire Array object and fails. Moreover we get a silent error, very hard to chase.
  (images[i]).loadPixels();  // Better. Force the array indexing first, call loadPixels() on the individual array element. 
}
```
### Maths functions

The maths functions are sequestered inside the Maths package, to avoid polluting the top level namespace with everyday terms like min, max etc. and just following good modern practice. Unless you're a Rocket Scientist you don't need maths stuff as top level functions. Although, Processing has plenty of math in it once you start moving those elegant graphics around the screen, not to mention 3D WebGL stuff. A few examples:
```javascript
circumference = 2 * Math.PI * radius;                       // a constant 'property' of Math, no () call needed 
distance = Math.sqrt((x1 - x2) * (x1 - x2) + (y1 - y2) * (y1 - y2 ));  // Standard 2D distance calc; you know this
absoluteValue = Math.abs(value);                            
maxiumum = Math.max(a,b,c, ...);                            // any number of args, Math.min similar  
roundUp = Math.ceiling(69.69);                              // result is 70   
height = base * Math.sin(angle);                            // and similarly cos, tan, asin, sinh, etc  
expo = Math.pow(2, 10);                                     // 1024  
bigInt = Math.pow(2, 53);                                   // 9007199254740992 of course. Have you been paying attention ?  
rand = Math.random();                                       // result between 0.0 and 1.0
```
The full [Montezuma](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math) !

# Conditionals

Conditionals allow your program to execute a block of code based on the result of an expression that utilizes relational or logical (boolean) operators.

### if

```javascript
var x = 1;
if (x > 0) {
  // execute some code
}
```

### if, else

```javascript
var x = 1;
if (x > 0) {
  // execute some code
} else {
  // execute some other code
}
```

### if, else if, else

```javascript
var x = 1;
if (x > 5) {
  // execute some code
} else if (x < -5) {
  // execute some other code
} else {
  // execute some other other code. The "else if" chain can go on as long as you like.
}
```

### Multiple conditions
```javascript
var x = 1;
if (x > -5 && x < 5) {
  // execute some code!
}
```

```javascript
var x = "puddings";
if (x.length === 8 || x.indexOf("ding") === -1) {
  // execute some code! Note the above is using exact or "strict" comparisons.
}
```
Warning: comparisons between variables or expressions that you think will return a clear true or false result can be tricky. The "==" and "!="  operators use loose comparison and can produce some surprising results, eg.  `"" == false` is true, but `"false" == false` is false. The "===" operator set use exact comparison - the only thing that is equal to "true" is another "true". It's advisable to always use the === and !== versions, but the "==" and "!=" are so common in other languages your fingers will type them without thinking. This is all a legacy from the early days. Here are the gory details: [Comparison tables](http://dorey.github.io/JavaScript-Equality-Table/)

### Switch {} statement

Rather than a long if/else chain, we can select a simple option with a switch statement.
```javascript
switch ( userInput ) {

  case 'q':
    quitProg = true;    // set a flag to quit the prog a little later
    break;

  case 'r':
    resetProg = true;   // a flag to reset things
    frames = 0;         // reset another thing right here
    break;

  case 'd':
    showDebug = true;   // a flag to show debug info each frame
    break;
}
```
This is neat and clear. If you omit the 'break' the code will "fall through" to the next case. This is generally error-prone, a reader often doesn't notice it, and then you create hours of head scratching, most likely for yourself.

Having said all that, switch{} is a little archaic and rigid. It seemed a devilishly clever idea back in 1969-72 when Brian Ritchie et al were writing C at Bell Labs. With memory so tiny, and CPU speeds so slow, you could construct a machine code "jump table" where the 'switch' value, often just a byte ('q', 'r' above, or small numbers like 1,2,3,5,8,10) indexed into a table of offsets, and then jumped direct to the 'case' code. Such desperate efficiency is no longer needed. 

# Loops

### While {}

Just as with our conditional (if / else) statements a while loop employs a boolean test that must evaluate to true in order for the instructions in the curly brackets to be executed. The difference is that the instructions continue to be executed until the test condition becomes false. If the test condition is false at the start, the loop body will not execute at all.

```javascript
var x = 0;
while (x < 10) {    
  console.log(x);     // Should print about 10 times. Or 9, or 11 ? A good exercise to check.
  x++;   
}
```
### Do while {}

This is similar to the while loop, but the test is done at the bottom, after each iteration of the loop. One consequence is that the loop always executes at least once. But really the point is that it's just clearer to test some conditions at the bottom.

```javascript
var x = 0;
do  {      
  console.log(x);    // How many times does it print now ?
  x++;   
} while (x < 10)
```

### For {}

Since this is a very common use of a loop, ie. running through a simple sequence of values, there is a simpler way to do the above. You can read this as: create variable x and set it to 0, while x is less than 10 do the stuff in the loop body, then increment x by 1 at the end.

```javascript
for (var x = 0; x < 10; x++) {  
  console.log(x);     // This is a very common idiom. The loop will run 10 times, for sure.
}                     // Remember: x = 0; x < loopCount   gives exactly loopCount passes.
```
### Breaking out of loops

The `break` statement will terminate a loop. One common idiom is to have an endless loop, and break out when you have done what you need. Occasionally this is clearer to code than other options.

```javascript
while(true) {
  // do stuff
  if ( value === 100 ) { break; }  // need that semicolon
  // do more stuff
}
```
**To do: foreach and variations**



# Functions

A function is a block of reusable code. You can reuse it, executing it many times. Functions also help structure and organize your code: self-contained processes and computations can be neatly isolated in a function.

```javascript
function sayHello() {
  console.log("hello");
}

sayHello(); // Call the function. Prints "hello"
```

```javascript
// A p5.js example. 
// Note, p5.js supplies "random()" as an interlude to Math.random(), with more flexible value range.

function changeBackground() {
  background(random(255), random(255), random(255));  
}
```

### Function parameters

A function can also accept values as input, known as arguments or parameters. Note that within the function code, these parameters are not the names of actual variables in your program, but are "place holder" variables limited to the scope of the function. When a function is run, the values passed in are temporarily assigned to the parameters defined in the function, until the function completes its execution.

```javascript
function sayHello(person) {
  console.log("Hello " + person);
}
sayHello("Jenny");  // prints "Hello Jenny"
```

```javascript
function addNumbers(a, b) {
  var c = a + b;
  console.log(c);  
}
addNumbers(3, -10)  // prints -7
```

```javascript
// Using p5.js
function drawEllipse(x, y) {
  ellipse(x, y, 50, 50);
  return;     // You can explicitly make it clear where the function returns, if you like
}
drawEllipse(mouseX, mouseY);  // a nice circle, centre x,y radius 50 
```

### Returning a value

The functions above take some action or change the state of the program, but they don't return any value. If you want your function to return a value, use 'return'. This is typically at the end of the function, but can be anywhere in the function. 

```javascript
function addNumbers(a, b) {
  var c = a + b;
  return c;
}
var result = addNumbers(3, -10);
console.log(result);   // prints -7
```

```javascript
var name = "jenny";
function makeSuper(person) {
  return "Super " + person;
}
var name = makeSuper(name);
console.log(name);    // "Super Jenny"
```

```javascript
// p5.js has some built-in functions like this
var x = random(100);
console.log(x);   // could print 23 or 77 or ...

// You can write your own enhanced function, using p5.js functions
function addJitter(x) {
  var y = x + random(-1, 1); // use p5.js random func. Two args allowed, min and max.
  return y;
}
var result = addJitter(10);
console.log(result); // 10.3 or 9.8 or ...
```
```javascript
function severalReturns(number) {
  if (number < 0 ) {
    return(number - 1);   // Note this terminates the function. An easy coding style, and not too bad if used clearly.
                          // Some people will be expecting the return at the end of the function. It's a matter of style.
  if (number > 0 ) {
    return(number + 2);

  if (number === 0) {
    return(0)            // no change
}

severalReturns(5);   // returns 7
severalReturns(-8);  // returns -9
```

# Variable scope

Variables that you declare inside a function, and also the function arguments, are local to that function, and can't be accessed outside the function. This provides vital "encapsulation" and protection of the functions data. Otherwise a statement `x = y + 1` in one function could trample on a statement `x = z + 3` in another function, or at top level.

Variables declared outside of any function are known as "global variables" and can be accessed from anywhere in the program, inside or outside functions. These are convenient, and essential at times to pass around global information, but can create hazards. Try not to declare simple names as globals, like min, max, sum, total, error, count. These can clash with other declarations in functions, or at top level in other code modules concatenated with this one, and unfortunately, due to JavaScripts permissive nature, this can create silent errors. One protocol is to declare all globals as "g_total", or an Object member "g.total" to make things clear. Slightly ugly but could save your bacon one day.

Another option is to put all your code in one top level function, say main(). Then nothing "escapes" from main(), so that stops clashes with other concatenated code modules. Like p5.js say ! **Check the instanced mode doco**

Example of global and local scopes:

```javascript
var xGlobal = "global";
	
function globalLocalTest() {
  var xLocal = "local";
  console.log("inside function global: " + xGlobal);  // prints "global"
  console.log("inside function local: " + xLocal);    // prints "local"		
}
	
globalLocalTest();                                    // prints the two values as above
	
console.log("outside function global: " + xGlobal);   // prints "outside function global: global"
console.log("outside function local: " + xLocal);     // prints "ReferenceError: xLocal is not defined"
```

### Precedence of global and local variables

If you use the same name as a global variable, and also as a local function variable, the function variable overrides within the function. This is ok in many situations, despite what we said above. For example simple count variables like i, j, k.

```javascript
var g_data = [ 1, 22, 333 ]    // global array
var i,j,k;                     // global simple control vars. A common style from older languages. Not even initialized! Never mind.
var offset = 3;                // global var

for (i = 0; i < g_data.length; i++) {   // a loop at top (global) level
  g_data[i] += 2;          // Adjust g_data values somehow
}

function adjustData() {
  var i;                   // This is a different i from the global i, but that's ok, we don't care what we did with i above
                           // For absolutely temporary vars like i, j, k, tmp, str, you can ignore scope if you like
  for (i = 0; i < g_data.length; i++) {   
    g_data[i] += offset;   // Ok, offset is still the global var
  } 
}

adjustData();
console.log(g_data[2]);   // prints 338 (333 + 2 + 3)
```
###To do: let, const

# Arrays

Arrays are used to store multiple objects or values in one variable. To create an array, use square brackets, and place any number of items separated by commas in between.

```javascript
var arr = []; // empty array
var fruits = ["apple", "dragonfruit", "banana", "starfruit"];
var ages = [10, 21, 89, 3, 68];
var misc = ["pumpkin", 10.4, "dog", false, -1]; // arrays can have items of different datatypes
var more_misc = ["dustpan", "k", fruits, misc]; // arrays can contain other arrays
```

You can place or access items in the array by index, the first item in an array has index 0.

```javascript
var arr = [];
arr[0] = "moss";
arr[1] = "sludge";
arr[2] = "mold";
console.log(arr); // ["moss", "sludge", "mold"]
console.log(arr[1]); // "sludge"
```

You can use a for loop to iterate over an array.

```javascript
var arr = ["mushrooms", "cheerios", "sparkling water"];
for (var i=0; i<3; i++) {
  arr[i] = "I love "+arr[i];
}
console.log(arr); // ["I love mushrooms", "I love cheerios", "I love sparking water"]
```

Like strings, arrays have some built-in convenience properties and methods. You can see them all in the [MDN array reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Methods), a few of the common ones follow.

**length**

Gives the length (number of items) of the array. This can be useful for iterating over arrays.

```javascript
var arr = [3, 5, 19];
for (var i=0; i<arr.length; i++) {
  arr[i] *= 2;
}
console.log(arr.length); // 3
console.log(arr); // [6, 10, 38]
```

**push()**

Adds (pushes) a new element to the end of the array, increasing the length of the array by 1.

```javascript
var arr = [30, 10, 0];
arr.push(true);
console.log(arr.length); // 4
console.log(arr); // [30, 10, 0, true]
```

**indexOf(elt)**

Returns the index of given element, or returns -1 if it's not found.

```javascript
var array = [2, 5, 9];
var index = array.indexOf(2); // 0
index = array.indexOf(7); // -1
index = array.indexOf(9, 2); // 2
index = array.indexOf(2, -1); // -1
index = array.indexOf(2, -3); // 0
```

# Objects

JavaScript doesn't have a "class" statement like Java or C++, instead it just uses functions as classes. Defining a class is as easy as defining a function.

```javascript
function Cat() {

}
```

The code above creates a constructor function for a Cat object. It is a very simple object with no properties or methods.

## Creating a new instance

To create a new instance of an object using a constructor, you write "new" followed by the name of the class and a set of parentheses.

```javascript
var cat0 = new Cat();
```

If you were to log this object to the console you will notice that it prints an empty set of curly braces.

```javascript
console.log(cat0); // Cat {}
```

 That is really all this object is, and you could have created the same thing by writing:

```javascript
var cat0 = {};
```

However, creating the constructor function is useful when you want to make more than one instance of the object, especially if you have set properties or methods for the object.

```javascript
var cat0 = {};
var cat1 = {};
var cat2 = {};
```

## Adding properties

Properties are variables within the object. They can be set in the constructor by including a line in the form `this.propertyName = propertyValue;`. Within an object constructor function, there is a special variable "this" that always refers to the new instance that is being created. So when the function includes `this.propertyName = propertyValue;` it is saying that all new instances will be automatically assigned the given properties and values upon instantiation.

```javascript
function Cat() {
  this.name = "Margot";
  this.age = 8;
  this.color = "Black";
}
```

If you create and log a Cat object now you will notice that the new instance now has properties, rather than just empty curly braces.

```javascript
var cat0 = new Cat();
console.log(cat0); // Cat {name: "Margot", age: 8, color: "Black"}
}
```

You can access and modify these properties directly by using `.propertyName`.

```javascript
console.log(cat0.name);  // "Margot"
cat0.name = "Sam";       // change name to Sam
console.log(cat0.name);  // "Sam"

cat0.age++;              // increment age by 1
console.log(cat0.age);   // 9

console.log(cat0.color); // "Black"
```

## Adding methods

While properties are like variables within an object, methods are like functions within an object. They are set and accessed in much the same way.

```javascript
function Cat() {
  // set some properties
  this.name = "Margot";
  this.age = 8;
  this.color = "Black";

  // set some methods
  this.greet = function() {
    console.log("Hello, I'm "+this.name);
  }
```

The constructor function above sets some properties of Cat, then it adds one method, "greet". This line looks kind of like a function definition, but is a slightly different format. With a normal function, you may be used to something like this:

```javascript
function doSomething() {
  console.log("I'm doing something!");
}
```

However, it's important to know that the above function could be rewritten like this:

```javascript
var doSomething = function() {
  console.log("I'm doing something!");
};
```

These two definitions are the same, just written differently. In both cases what is happening is that a function is defined and assigned to a variable name of your choosing. Remember in JS, a variable can be anything - a string, a number, a boolean, etc - but also a function. 

In the first case, this variable name is stuck after the word function, in the second, the variable is explicitly stated first, then the function is assigned. They mean the same thing, so it's helpful to get used to seeing both forms.

So turning back to the method declaration, it starts to look more familiar. It's very similar to the new function definition format we just saw, but `var functionName = ` is replaced with `this.functionName = `. This is because, just like the properties, we use `this.` to say that the method belongs to the object being created.

```javascript
this.greet = function() {
  console.log("Hello, I'm "+this.name);
}
```

Calling this method of an instance looks similar to accessing properties.

```javascript
var cat0 = new Cat();
cat0.greet(); // "Hello I'm Margot"

cat0.name = "Sam";
cat0.greet(); // "Hello I'm Sam";
```

## Using parameters

You can also pass parameters into the constructor function, the same way parameters are passed into any function. The arguments are listed within the parentheses for the constructor function, separated by commas.

```javascript 
function Cat(name, age) {
  this.name = name;
  this.age = age;
  this.color = "Black";

  this.greet = function() {
    console.log("Hello, I'm " + this.name);
  }
}

var cat0 = new Cat("Joanie", 10);
var cat1 = new Cat("Jay", 2);

cat0.greet(); // "Hello, I'm Joanie"
cat1.greet(); // "Hello, I'm Jay"
```

# Code formatting

### Comments

It is a good idea to add comments to your code so you can remember what you're doing and debug when things go wrong. Commenting can also be useful for quickly removing or adding back in chunks of code (safer than deleting the chunk). Comments in JavaScript are similar to comments in Java or C.

```javascript         
  // single line comment   
```
```javascript     
  /* 
    multiple
    line
    comment
  */
```

### Indentation

Whenever you introduce curly braces, you should indent everything inside. You can use two spaces or four, but be consistent. This will help you make sense of your code later.

```javascript
function doStuff(x) {
  if (x > 0) {
    console.log("x is greater than 0");
  } else {
    console.log("x is not greater than 0");
  }
}
```

### Semicolons

A code statement generally ends with a semicolon.

```javascript
var x = 10;
```

However, you may hear that semicolons are optional in JavaScript. This is sort of true. You can read more [here](http://news.codecademy.com/your-guide-to-semicolons-in-javascript), but my general recommendation is to use semicolons to avoid confusion.
