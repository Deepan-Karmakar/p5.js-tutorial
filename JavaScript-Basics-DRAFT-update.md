
Update finished 11 Feb 18. Reviews invited !



JavaScript is a language that is typically used on web pages where it runs client-side (within the web browser). It is a general purpose language with a lot of built-in functionality for interacting with HTML elements on a webpage and responding to actions initiated by the user. It is described as one of the "core three" technologies that drive the Web: HTML, CSS, and JavaScript.

Although JavaScript has "Java" in it's name, it isn't related other than by the fact that it looks something like Java. It is supposedly influenced by the languages Self and Scheme, but with a Java or C++ appearance. JavaScript's official name is ECMAScript (ECMA is the European Computer Manufacturers Association, a standards body). It was initially created by Netscape Communications. ([Wikipedia: JavaScript](http://en.wikipedia.org/wiki/JavaScript))

JavaScript has an interesting history. It was created in 1995 by Brendan Eich in 10 days ! to provide an urgently-needed web scripting ability at Netscape, but then took off as part of the late 90's explosion of the Web. Since then it has matured into a fully-functioned language, used in client-side Web code, server-side code, and many types of general code having nothing to do with the Web. It is usually placed in the top few, and often at the very top, in surveys of "languages most used", "languages most required in job ads" etc. Time spent learning JavaScript could be time well spent! 

***

## Contents:

Not a comprehensive TOC, just shortcuts to some sections. 

[Script setup in HTML](#script-setup-in-html)  
[Use of console](#javascript-console)  
[Variables](#variables)  
&nbsp;&nbsp;&nbsp;[Variable naming](#variable-names)   
[Datatypes](#data-types)   
&nbsp;&nbsp;&nbsp;[Number](#data-type-number)  
&nbsp;&nbsp;&nbsp;[String](#data-type-string)  
&nbsp;&nbsp;&nbsp;[Extended character sets: Unicode, UTF](#extended-character-sets-unicode-utf)  
&nbsp;&nbsp;&nbsp;[Boolean](#data-type-boolean)  
&nbsp;&nbsp;&nbsp;[Null and Undefined](#data-type-null-and-undefined)   
&nbsp;&nbsp;&nbsp;[Arrays](#data-type-array)  
&nbsp;&nbsp;&nbsp;[Objects](#data-type-object)  
&nbsp;&nbsp;&nbsp;[Simple objects](#basic-objects)  
[Assignments](#assignment)  
[Operators](#operators)  
&nbsp;&nbsp;&nbsp;[Precedence of Operators](#precedence-of-operators)  
&nbsp;&nbsp;&nbsp;[Math functions](#maths-functions)  
[Conditionals](#conditionals)  
&nbsp;&nbsp;&nbsp;[If else](#if)  
&nbsp;&nbsp;&nbsp;[Comparison issues, loose vs strict](#comparison-issues)  
&nbsp;&nbsp;&nbsp;[Switch](#switch-statement)  
[Loops](#loops)      
&nbsp;&nbsp;&nbsp;[While](#while-)  
&nbsp;&nbsp;&nbsp;[Do while](#do-while-)  
&nbsp;&nbsp;&nbsp;[For](#for-)  
&nbsp;&nbsp;&nbsp;[Break out of loop](#breaking-out-of-loops)   
&nbsp;&nbsp;&nbsp;[For in, for of, forEach](#for-in-for-of-foreach)&nbsp;&nbsp;&nbsp;     
[Functions](#functions)    
&nbsp;&nbsp;&nbsp;[Function arguments](#function-arguments-or-parameters)   
&nbsp;&nbsp;&nbsp;[Arguments are optional](#arguments-are-optional)   
&nbsp;&nbsp;&nbsp;[Default arguments](#default-arguments)     
&nbsp;&nbsp;&nbsp;[Rest arguments](#rest-arguments)     
&nbsp;&nbsp;&nbsp;[Recursion](#recursion)  
&nbsp;&nbsp;&nbsp;[Closures](#closures)      
&nbsp;&nbsp;&nbsp;[Arrow functions](#arrow-functions)     
[Variable scope](#variable-scope)  
&nbsp;&nbsp;&nbsp;[Precedence of global vs local variables](#precedence-of-global-and-local-variables)       
&nbsp;&nbsp;&nbsp;[The "let" declaration](#new-scope-declaration-let)  
&nbsp;&nbsp;&nbsp;[Other points about let](#other-points-about-let)    
&nbsp;&nbsp;&nbsp;[The "const" declaration](#the-const-declaration)      
[Objects part 2: objects as classes](#objects-part-2-objects-as-classes)   
&nbsp;&nbsp;&nbsp;[A p5.js example](#a-p5js-example)  
[The new Class statement](#the-new-class-statement)     
[Code formatting, style, good practices, common mistakes](#code-formatting-style-good-practices-common-mistakes)  
&nbsp;&nbsp;&nbsp;[Comments](#comments)  
&nbsp;&nbsp;&nbsp;[Indentation](#indentation)  
&nbsp;&nbsp;&nbsp;[Padding](#padding)  
&nbsp;&nbsp;&nbsp;[Line continuation](#line-continuation)  
&nbsp;&nbsp;&nbsp;[Semicolons](#semicolons)  
&nbsp;&nbsp;&nbsp;[Strict mode](#strict-mode)  
&nbsp;&nbsp;&nbsp;[Style checkers](#style-checkers)  
&nbsp;&nbsp;&nbsp;[Common mistakes](#common-mistakes)   
&nbsp;&nbsp;&nbsp;[Performance, efficiency, profiling](#performance-efficiency-profiling)  
[The Bottom Line](#the-bottom-line)    
***

## Script setup in HTML

JavaScript in a web page can be placed anywhere within the HTML document, although it is typically included in the `<head>` section of the HTML. It is specified by the use of `<script>` tags:

```html
<html>              
  <head>              
    <script type="text/javascript">              
      //JavaScript goes here 
      var str = "This is my first message";                                    
      console.log(str);  // This will show up in the browser's JavaScript console. 
      alert(str);        // This will show a popup message in the browser. Irritating, use sparingly !
    </script>
  </head>              
<body> 
  This is totally plain raw text, the browser will show it in some default font/size/colour, maybe Times/12/black.
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

JavaScript can be scattered all through a web page, enclosed in <script> and </script>, or in special tags like \<button\>. Example: here we intercept a mouse click on a button, copy some data around, and change the background colour:

```html
<html>
<body>

Field1: <input type="text" id="field1" value="Hello World!"><br>
Field2: <input type="text" id="field2"><br><br>

<button onclick="myFunction()">Click me</button>  <!-- the onclick action is JavaScript too -->

<p>A function is triggered when the button is clicked. The function copies the text from Field1 into Field2, 
 and also changes the background colour</p>

<script>
function myFunction() {
    document.getElementById("field2").value = document.getElementById("field1").value;
    document.getElementsByTagName("body")[0].style.backgroundColor = "yellow";
}
</script>

</body>
</html>
```

Try the above in an index.html. However this tutorial is not about use of JavaScript to control HTML elements, see multitudes of other web tutorials for all that.

## JavaScript Console

One of the first things we need is to get some debugging output. You can write to the browser JavaScript console by using the built-in console.log method:

```javascript
console.log("hello");
console.log("variables x, y values", x, y);          // Use the default space separation of args
console.log("variables x, y values " + x + "," + y); // Concatenate message into a single string, more flexible
```

In order to see the console on Chrome, select menu sequence View / Developer / JavaScript Console. Use it often! On other browsers, just search for info on "how to open the JavaScript console in \<whatever\> browser". Note also that Processing has a "print()" function which does a similar job to console.log().

Another useful thing is to find a command-line JavaScript interpreter, to check basic things and follow along with this tutorial. 

On Mac, there is a JavaScript interpreter at /System/Library/Frameworks/JavaScriptCore.framework/Versions/Current/Resources/jsc 

You can invoke that directly from a Terminal screen (Finder / Go / Utilities / Terminal). 

To simplify typing, try "alias myjsc=/System/Library/Frameworks/JavaScriptCore.framework/Versions/Current/Resources/jsc". Once in jsc, it operates much like the JavaScript console in a browser. Use Ctrl-C (quit) or more elegantly Ctrl-D (end of input) to exit the interpreter.


## Variables

A variable holds a value in memory. It can be used in calculations, composing some kind of message, updating the appearance of a web-page component, controlling the appearance of a Processing visual entity (very relevant here!), countless things. Variables are a fundamental part of programming languages, like words are part of spoken languages.

A quick swing through setting up variables:

```javascript
var x = 5;
var y = x + 7;                   // y is now 12

var a = "some text"; 
var b = a + " is here";          // b is now "some text is here". Note the + has a different function for strings

var stuff = [1, 22, 333];        // stuff is a three element array, with the values shown
var s = data[2];                 // s is 333. Note indexing from zero, not one.

var myRecord = { givenName: "Albert", familyName: "Einstein", age: 33 };  // Create an "object" with three key:value pairs
var name = myRecord.givenName;   // name has string value "Albert"

var delete_file = false;         // var has a Boolean value "false".
var keep_file = !delete_file     // keepFile has Boolean value "true". (! means negate). Useful for binary options.

var string1 = "";                // One (good) way to initialise a string to an empty value.
var string2 = null;              // Another way. Be careful, null has tricky properties, see later.
var string3;                     // Both this ...
var string4 = undefined;         // ... and this give the var the "undefined" value. Also very tricky, see later.

```
Variables should nearly always be given an initial value. Otherwise, like string3 above, they have an "undefined" value until later in the program, which can lead to hard-to-debug errors.

### Variable names

Variables (and other names in JS, like functions) can be named with lower and uppercase letters, numbers, underscore, or dollar signs. Avoid dollar signs. For multi-component names, there are two favourite styles: my_data and myData. The second is more common. Underscores at the beginning or end of a name can denote something special, often a variable which is similar to a system-provided term. Eg. for some reason you desperately want to name some variable "var" but var is a reserved word in JS, so you can use "var_" or "\_var\_": `var var_ = 123;` Unless you know very well what you're doing, this is not recommended. 


## Data Types

JavaScript is a "loosely typed" or "dynamic" language, meaning you don't have to declare the types of variables ahead of time. The type will get determined automatically while the program is being processed. Other languages such as Java, C, C++ are strictly typed, mainly for catching errors at compile time, and each variable must declare the type of the data it will contain. Even though you don't have to declare types, JavaScript does have different data types.



### Data type: Number

A number, optionally with a decimal point, or exponent. In other languages this is typically called a float, short for "floating point number". It can be written with or without the decimal point.

```javascript
var x = 5;
var y = 1.223;
var z = -300;
var big = 1.23e82;   // This is a big number, the estimated atoms in the universe, but quite ok to code with, why not?
var small = 1.6e-35  // The Planck Length, the smallest physical size (in metres) that has any meaning in classical physics.
var biggest = 1.7976931348623157e+308  // Biggest number JavaScript can hold. I know you wanted to know.
var smallest = 5e-324                  // Why not symmetrical with biggest ? Small numbers can be "denormalised", we sacrifice
                                       // digits to get more exponent. You didn't need to know this probs. 
```
JavaScript stores all numbers as 64-bit floats. You generally get from 15 to 17 decimal digits of accuracy, so you could safely write `x = 1.23456789012345`. This is very accurate but still has limits. Sometimes it can lead to very small inaccuracies. Try this in the JavaScript console: `0.1 + 0.2` You should get `0.30000000000000004` Try `0.362 * 100`  You should get `36.199999999999996`. This is rarely a problem in practice, after all it's accurate to 1 part in a quintillion, usually pretty ok ! Better than my old Engineers slide rule, accurate to 3 sig figs, that I designed those nuclear power stations with (ok not true).

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

There are a large number of useful built-in JavaScript properties and methods that let you manipulate strings. You can see them all here [w3schools](http://www.w3schools.com/js/js_string_methods.asp), and also here [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/). These two sites, the www3schools site, and the Mozilla Development Network (MDN), are good references. Another useful one is [Javascript.info](https://javascript.info/types#a-string/). A few of the most useful String methods follow:

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

Sometimes the interesting info is the last occurrence of something in a string.

```javascript
var str = "long.complicated.filename.txt";
var suffixPosition = str.lastIndexOf(".");  // 25
```

**includes(str)**

This method just returns whether the string contains a smaller string, true or false.

```javascript
var str = "reallycrazylongstring";
var maybe = str.includes("zylo");  // returns true
```

**substring(start, end)**

Extracts a part of a string and returns the extracted part in a new string. The method takes 2 parameters: the starting index, and the ending index+1. So the substring returned is from str(start) to str(end-1) inclusive. Bit tricky.

```javascript
var str = "I like to eat apples.";
var newStr = str.substring(2, 6);  // "like", ie. characters 2,3,4,5
```

**substr(start, length)**

Another variation of substring. It takes 2 parameters: the starting index, and the length required. Murphy's Law of Programming says you'll always use one when you meant the other.

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
In the console, try `abc = " abc \n";` .. `abc;` .. `trim(abc);`

**trimLeft(), trimRight()**

These are more specific versions which trim whitespace only from the left or right of a string. Surprisingly they are not 100% standard, although very common extensions in JavaScript. For maxiumum robustness and portability of code, you could code these yourself as private utility functions, very easy. Or you could just check they work in your preferred browser and not worry. 

Here's a suggested code from MDN for replacing trim(), you can modify it to create a trimLeft or trimRight. This uses a regexp call, a "regular expression", a miniature language in itself, and very powerful. IMHO the Perl documentation on regexp is the best I have seen: [Perl regexp doco](https://perldoc.perl.org/perlre.html). But there can be tiny differences, if you have issues check the: [JavaScript regexp doco](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions).

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

**Converting between number and string**

There are some legit ways to convert between numbers and strings.

```javascript
var num = 123;
var str = num.toString();
console.log(str);                    // "123", a string

var num2 = parseInt(str, 10)         // 10 is the radix. You can use 16 or 8 or 2 for hex, octal, binary
console.log(num2);                   // 123, back to a number
```

There are also some somewhat clunky ways of forcing conversions between numbers and strings:

```javascript
var str = "123";  console.log(str);        // "123" ie. in quotes, a string
var num = +str;   console.log(num);        //  123   a number
var num2 = 456;
var str2 = ""+num2; console.log(str2);     // "456"  a string
```

### Extended character sets: Unicode, UTF

In the English-speaking world we live in a privileged bubble where everything is in our familiar character set, ie. the good old English typewriter/printing character set. ASCII is the familiar encoding for these. But it still limited; only about half the punctuation set we routinely use is in there, for example the dollar sign $ is there, but not a proper cents sign &#xa2; or UK Pounds sign &#xa3;. 

European languages have many accented characters, like the &#xe9; in caf&#xe9;. Then there is the Cyrillic alphabet, eg. Kremlin = Кремль. Then the character sets of Chinese, Japanese, Korean and many other languages. These can be the compact "phonetic" character sets, like Japanese Hiragana ひらがな with 46 characters, or the Chinese-derived Kanji 漢字 set of thousands of characters. There is the arabic العَرَبِيَّة‎ character set which runs right to left. My apologies to important languages I have not mentioned here. 

(How am I entering these characters in the Wiki text here? - mainly cut & paste from web pages).

JavaScript allows the use of all these characters, using the Unicode character set. For example if you want to print a currency message:

```javascript
cent = "\u00a2";
ukpound = "\u00a3"; 
message = "Your card will be billed $123 and 45" + cent + " which is UK pounds " + ukpound + "78.99";
console.log(message);         // Your card will be billed $123 and 45¢ which is UK pounds £78.99";  
```

One of the main traps with extended character sets is that the length of the visual string (say caf&#xe9, 4 visual characters) is not equal to the length of the encoded string, which will be longer than 4. This makes some text layout coding more difficult. There are facilities in JS to give you the "encoded length" of a string:

```javascript
enc = new TextEncoder('utf-8');    // You can choose the UTF type. UTF-8 is the most common.
enc.encode("cafe").length;         // 4
enc.encode("café").length;         // 5
```

UTF-8 uses plain single-byte Ascii for the common English characters, "caf" here, and a 2-byte encoding for the next commonest Western set, which includes accented European characters. It uses 3 and 4 byte encodings for further characters. (I'm trying not to say "uncommon" characters here. Hindi हिन्दी written in the usual Devangari मानक हिन्दी script is not at all uncommon to the 380 million Hindi speakers).
 
Extended character sets are a big subject. If you need to, look up Unicode, UTF-8 in Wikipedia, and Google for other info.

[Unicode chars](https://unicode-table.com/en/#control-character)  
[Example of cents](https://www.toptal.com/designers/htmlarrows/currency/cent-sign/)

### Data type: Boolean

A "true" or "false" value. Boolean variables are often used for conditional testing and keeping track of state. Things that need to be on or off, done or not done.

```javascript
var drawBackground = true;
var drawDebugInfo = false;
```

### Data type: Array

Arrays are used to store multiple objects or values in one variable, and access them via a numeric index. To create an array, use square brackets, and place any number of items separated by commas in between.

```javascript
var arr = [];                                     // empty array
var fruits = ["apple", "dragonfruit", "banana", "starfruit"];
var ages = [10, 21, 89, 3, 68];
var misc = ["pumpkin", 10.4, "dog", false, -1];   // arrays can have items of different datatypes
var more_misc = ["dustpan", "k", fruits, misc];   // arrays can contain other arrays. Works fine, but be careful ! 
console.log(more_misc[2][2]);                     // prints banana
console.log(more_misc[3][1]);                     // prints 10.4
```

You can place or access items in the array by numeric index; the first item in an array has index 0.

```javascript
var arr = [];
arr[0] = "moss";
arr[1] = "sludge";
arr[2] = "mold";
console.log(arr);      // ["moss", "sludge", "mold"]
console.log(arr[1]);   // "sludge"
```

You can use a for loop to iterate over an array.

```javascript
var arr = ["mushrooms", "cheerios", "sparkling water"];
for (var i = 0; i < 3; i++) {
  arr[i] = "I love " + arr[i];
}
console.log(arr); // ["I love mushrooms", "I love cheerios", "I love sparking water"]
```

Arrays can contain arrays, as noted above, so you can construct a 2 (or higher) dimensional array, even though JavaScript doesn't have an explicit multi-dimensional array type.

```javascript
// A 2x2 matrix.
var matrix = [
    [ 1, 2 ],    // row 0
    [ 3, 4 ],    // row 1. You can leave that dummy comma there, but better to omit; confuses some old JS engines.
];
console.log(matrix[0][1]);   // Shows 2. Ie matrix(row 0, col 1) in mathematical thinking.

// A 4x4 identity matrix, familiar to 3D graphics programmers ...
var identity_4x4 = [
     [1, 0, 0, 0],
     [0, 1, 0, 0],
     [0, 0, 1, 0],
     [0, 0, 0, 1]    // no last comma, better
]
```

Does JavaScript have a native matrix math ability ? No. But there are many matrix libraries available for JavaScript, just Google around. Also p5.js has a matrix facility for graphics transforms, eg. applyMatrix(), but that looks like only 2D graphics transforms at present.

Arrays can have empty (undefined) elements. If you add a new element beyond the current length of the array, the array is just extended. The array.length always returns the whole length of the array, including any undefined elements.

```javascript
var arr = [1, 2, 3];
arr[5] = 999;
console.log(arr.length)     // prints 6
for ( var i = 0; i < arr.length; i++ ) {
   console.log(arr[i]);     // prints 1 2 3 undefined undefined 999
}
```

Like strings, arrays have some built-in convenience properties and methods. You can see them all in the [MDN array reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Methods). A few of the common ones follow.

**array.length**

Gives the length (number of items) of the array. This can be useful for iterating over arrays. Note, as for String.length, this is a plain property, not a method call.

```javascript
var arr = [3, 5, 19];
for (var i = 0; i < arr.length; i++) {
  arr[i] *= 2;
}
console.log(arr.length); // 3
console.log(arr); // [6, 10, 38]
```

**array.push(), array.pop()**

Adds (pushes) a new element to the end of the array, increasing the length of the array by 1. Pop does the opposite.

```javascript
var arr = [30, 10, 0];
arr.push(true);
console.log(arr.length); // 4
console.log(arr); // [30, 10, 0, true]

var last = arr.pop();        // last is true, arr is back to what it was
```

**array.shift(), array.unshift()**

These remove or add an element from the beginning of the array.

```javascript
var arr = ["cats", "eat", "birds"];
arr.unshift("some");
console.log(arr.length); // 4
console.log(arr); // ["some", "cats", "eat", "birds"]

var first = arr.shift();        // last is "some", arr is back to what it was
```

**array.indexOf(elt, [start])**

Returns the index of given element, or returns -1 if it's not found. Arrays can't have negative indices, so -1 is an ok failure indicator. If given two args, the second is the start index for the search. If the start index is negative, we start "start" places back from the end (but we still search forward). 

```javascript
var arr = [2, 5, 9, 33];        //      arr.length is 4, last index 3
var index = arr.indexOf(2);     //  0  (2 is first, ie. zero'th, element)
index = array.indexOf(7);       // -1  (there's no 7 in the array)
index = array.indexOf(5, -2);   //  2  (5 is there, even when starting search at index 3-2 = 1) 
index = array.indexOf(5, -1);   // -1  (5 is not there, when starting search at index 3-1 = 2) 
```

**array.reverse()**

Reverses the order of the elements, in situ.

```javascript
var arr = [111, 222, 333, 444];
arr.reverse();                   // arr is now [444, 333, 222, 111]
```

**array.slice(start, end)**

Extract a "slice" of an array, from index "start", to index "end" - 1. Like String.substring(), the end is one past the last element extracted.

```javascript
var arr = [111, 222, 333, 444];
var arr2 = arr.slice(1, 3);    // arr2 is [222, 333]   ( not [222, 333, 444] )
```

**array.splice(start, end)**

Delete or insert one or more elements from/into an array. I'm going to let you just read that one, it has a lot of functionality crammed into one call [MDN splice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)

There are many more methods: fill(), sort(), keys(), values() ... Look them up when you need them [MDN array methods]
(https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) 

**Creating empty arrays**

Some final words on creating empty new arrays that will be populated later.

```javascript
var arr1 = new Array(100);                     // Creates an array 100 long, and fills all elements with undefined. 
                         
var arr2 = []; 
for(var i = 0; i < 100; i++) { arr2[i] = 0; }  // Same effect as arr1 above (but 0 much better than undefined).

var arr3 = new Array(100); arr3.fill(0);       // Populate all elements with 0. Probably the clearest approach.
```


### Data type: Object

An object can be thought of as a collection of properties. These properties can be values of any type, including numbers, text strings, arays, other objects, and functions, which can enable the building of complex and dynamic data structures. Arrays and objects are very similar; in fact arrays are a type of object, which only have numeric indexes, and have a defined order (array[0] to array[lastone], and allow gaps in the indices (ie. undefined parts of the array), and a few other subtleties.

Here we will cover just the basics of objects, with static members. Further down we will add function calls, ie. "methods" to objects, which allows us to create dynamic objects which provide the functionality called "classes" in other languages.
 
### Basic objects

At a basic level, JavaScript objects are a data type like an Array, where a numeric or string "key" can be used to access the data. In other languages they are sometimes called associative arrays, or hash tables. 

```javascript
var obj = { 1: 1, "twos": 22, 333: "threes", "name": "Fred Nurk" };    // all the combos of number & string
console.log(obj);                         // 1: 11  33: "threes"  twos: 22  name: "Fred Nurk"
console.log(obj.twos, obj.name);          // 22  "Fred Nurk"
console.log(obj[1], obj[333]);            // 1  "threes"         (have to use [] notation for numeric keys)
console.log(obj["twos"], obj["name"]);    // 22  "Fred Nurk"     (string keys can use the [] notation as well)
```

Objects with string keys ( obj.name  or  obj["name"] ) are a convenient way to store arbitrary data. Note here we have array elements, which are objects.
```javascript
var staff = [];
staff[0] = { "first": "Sue", "last": "Smith", "age": 55, "title": "Dean", "faculty": "Arts", "salary": 234567 };
staff[1] = { "first": "Jim", "last": "Jones", "age": 44, "title": "Prof", "faculty": "Arts", "salary": 123456 };
staff[0].age  // returns 55
```
Objects can contain other objects.

```javascript
var obj = { 1: 11, 2: {2: 22}, 3: 33};           // Build with nested object literal

var obj2 = {2: 22};
var obj = { 1: 11, obj2, 3: 33 };                // Build it in stages

var obj = {};                                    // Build it in different stages
obj[1] = 11;
obj[2] = {2: 22};
obj[3] = 33;        
```

If we use an iterative access method to access all the members of an object, the order the records will be returned in is unpredictable.

```javascript
var stuff = { 0: "a", 1: "b", 2: "c", 3: "d" };
for (var x in stuff) {
   console.log(x);          // Could be 0 2 1 3
   console.log(stuff[x]);   // and a c b d
}
```

Objects can use the array-like [] access notation, ie. object[key], so it can be hard to know if something you see in some code is an object or an array. Thing[accessor] ? What's that ? Could be array or object. typeof(anObject) and typeof(anArray) both return "object", reflecting the fact that they are closely related. The function Array.isArray() can distinguish them:

```javascript
var arr = [1, 2, 3];
var obj = {1: 1, 2: 2, 3: 3};
typeof(arr);           // returns "object"
typeof(obj);           // returns "object"
Array.isArray(arr);    // returns true
Array.isArray(obj);    // returns false
```

We will come back to more details on Objects later. Particularly the ability to embed function calls (methods) in an Object, and hence make a kind of class, where the Object has data and methods to insert, access, process, etc its data.


### Data type: Null and Undefined

The value of a variable which has not been given any value is `undefined`. This is a specific single type with a single value, which you can also assign manually. 

Variables can be "emptied" by setting the value to `null`. This is another specific single type and value. It means a specific value *has* been assigned, but it's deliberately null.

Often it's better to avoid null and undefined, JS does some unexpected things with them.

```javascript
var car;                // Value is 'undefined'. Not a string, a built-in value.
var truck = undefined;  // Same effect
var person = null;      // Value is 'null'. Not a string, a built-in value.

var count = 0;          // Often safer for numerics
var message = "";       // Ditto for strings
var newArray = [];      // Safe
var newObject = {};     // Safe
```

Creating new "empty" things in JavaScript is surprisingly clunky. It's slightly hard to know what you have done with a statement like `var myArray = []`. Go to the JS console and type it, then just type "myArray". JS will compute the expression, which is a single array, with no useful effect, ie. no assignment to anything, but that's ok, and display a breakdown of what it is, an array with no elements, length 0. You can hit the disclosure triangle for more detail if there is one. Try again with `myArray = [1,2,3]`. You'll get the picture quickly. Also try `var myObj = {}` and `myObj = {"alpha":1, "beta":2}`.

Note: the `typeof()` call is a great debugger and learning tool. Try it in the JS console. `typeof(1); typeof("a"); x = 12.34; typeof(x); x = x + "hello"; typeof(x); a = 1.23; b = a + '4'; typeof(b); typeof(undefined); var z; typeof(z); typeof(null)`

## Assignment

Once variables are declared, you can assign values to them and use them in operations.

```javascript
var x = 5;
x = x * 5;        // x now 25
x = "cat";        // You can change the type of a variable any time, here number to string
var y = x + "s hate dogs";  // y is "cats hate dogs". Note + is the only math operator that has been hijacked for string use.
var z = x - "t";  // Result is NaN (Not a Number), not "ca". It totally blew up! Brilliant. Thanks Brendan.
```

## Operators

We will zoom through the operators here. We assume some very basic maths background in the reader.

### Assignment

* `=`
* `a = b = c = 123;`&nbsp;&nbsp;&nbsp;&nbsp;// Multiple assignment is allowed and looks neat, but is unwise. [Details](https://www.undefinednull.com/2014/02/03/multiple-left-hand-assignment-in-javascript-is-really-bad-think-once-before-you-do-it/)

### Mathematical

* `+` addition
* `-` subtraction
* `*` multiplication
* `/` division
* `**` exponentiation:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;// 3**4 gives 81. New in EcmaScript 6. Before we required Math.power(x,y). See later in tut.
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
* `b = a++` b is 1, a is 2 - the ++ was done after the assignment
* `b = ++a` b is 3, a is 3 - the ++ was done before the assignment. Similarly for -- &nbsp; Use these carefully, "out by one" oversights happen easily.

### Relational, ie. comparisons

* `>=` greater than or equal to &nbsp;&nbsp;&nbsp;&nbsp; // works with strings also, but many subtleties. Is 'aAa' < 'BbBb' ? Is ODonnel < O'Donald ?
* `<=` less than or equal to
* `==` equal to 
* `!=` not equal to 
* `===` equality with strict type checking, safer
* `!==` inequality with strict type checking, safer

### Logical, ie. Boolean logic tests

```javascript 
* ||  logical OR              // if ( feelingTired || reallySleepy ) { lieDown(); }
* &&  logical AND             // if ( haveWallet && (money > 10) ) { buyBeer(); }
* !   logical NOT             // showDebugInfo = ! inProductionMode;
```

### Precedence of operators

The operators have a precedence which sometimes matches what we learned in school.  When operators have equal precedence, they proceed left to right. `xx = 24 / 6 * 5` will produce 20. But `xx = 1 + 2 * 3` will produce 7, not 9, because the multiplication has higher precedence and will get done first. To force the order you want, use brackets. 
```javascript
var xx = (1 + 2) * 3           // will produce 9.  
var gravity = G * (mass1 * mass2) / (distance * distance);  
var intensity = light / (Math.sqrt( (radius * radius) + fudgeFactor ); 
```
Other operators have progressively lower precedence. [Full table here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence). This allows you to write most expressions in a natural way. 
```javascript
if( radius > 5.0 && radius < 10.0) { drawCircle(); }               // works fine, but ...
if( (radius > 5.0) && (radius < 10.0) { drawCircle(); }            // clearer and safer. 
```
The lowest operator is a strange thing called the 'comma' operator. You can pack several statements into one. (x = y, a = b). The most common use is in a slightly more fancy 'for loop'.
```javascript
for (var i = 0, j = 9; i < 9; i++, j--) {  // i runs 0 up to 9, j runs 9 down to 0
  console.log( a[i][i] );                  // Print the conventional diagonal elements of a 9x9 array
  console.log( a[i][j] );                  // Print the other diagonal, top-right to bottom-left, of the array
}
```
Some traps exist. No precedence order can be what you want all the time. An example from p5.js:
```javascript
var images = [];
for (var i = 0; i < 10 ; i++) {
  images[i] = createImage(width, height);   // Create an array of new images.
  images[i].loadPixels();    // Ok? Noooo. The member access ".loadPixels()" has higher precedence than the array index, so gets called
                             // on the entire Array 'object' and fails. Moreover we get a silent error, very hard to chase.
  (images[i]).loadPixels();  // Better. Force the array indexing first, call loadPixels() on the individual array element. 
}
```

### Maths functions

The maths functions are sequestered inside the Maths package, to avoid polluting the top level namespace with everyday terms like min, max etc. and just following good modern practice. Unless you're a Rocket Scientist you don't need complex maths stuff as top level functions. Although, Processing has plenty of math in it once you start moving those elegant graphics around the screen, not to mention 3D WebGL stuff. A few examples:
```javascript
circumference = 2 * Math.PI * radius;           // a constant 'property' of Math, no () call needed 
distance = Math.sqrt((x1 - x2) * (x1 - x2) + (y1 - y2) * (y1 - y2 ));  // Standard 2D distance calc; you know this
absoluteValue = Math.abs(value);                            
maxiumum = Math.max(a,b,c, ...);                // any number of args, Math.min similar  
roundUp = Math.ceiling(69.69);                  // result is 70   
height = base * Math.sin(angle);                // and similarly cos, tan, asin, sinh, etc  
expo = Math.pow(2, 10);                         // 1024  
bigInt = Math.pow(2, 53);                       // 9007199254740992 of course. Have you been paying attention ?  
rand = Math.random();                           // result between 0.0 and 1.0 (actually 0.9999999999...)
```
The [full Montezuma](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)  &nbsp;&nbsp;
[???](https://en.oxforddictionaries.com/definition/full_monty)

## Conditionals

Conditionals allow your program to execute a block of code based on the result of an expression that utilizes relational or logical (boolean) operators, or just boolean values.

### if

```javascript
var x = 1;
if (x > 0) {
  var a = x + 1;
  var b = a + 3;
}
```

### if, else

```javascript
if (runAnalysis) {
  // run some analysis, if the boolean var 'runAnalyis' was true
} else {
  // run some other code
}
```

### if, else if, else

```javascript
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
if ( (x >= -5) && (x <= 5) ) {   // fully bracketed
  // execute some code if x was in range -5 to +5
}
```

```javascript
var x = "puddings";
if ( x.length === 8 || x.indexOf("ding") === -1 ) {   // just wing it
  // execute some code. Note the above is using exact or "strict" comparisons, safer.
}
```
Editorial note: in Pedantic World these names are used - () parentheses, [] brackets, {} braces, <> angle brackets. However it's common to just say () round brackets, [] square brackets, {} curly brackets, <> angle brackets. I think there is a fancy name for angle brackets, but it escapes me.
 
### Comparison issues

Warning: some comparisons between variables that you think would return a clear true or false result can be tricky. The "==" and "!="  operators use loose comparison and can produce some surprising results, eg.  `"" == false` is true, but `"false" == false` is false. (There is some logic to that, but it's not great design). There's a quaint terminology called "truthy" and "falsy". Values like 0 or "0" or "" or [] or [[]] or [0] are falsy. Values like 1, "1" and [1] are truthy.  

The "===" and "!==" operator set were introduced at JavaScript 1.3 to use exact comparison - things must be the same type and the same value to be equal. The only thing that is equal to Boolean `true` is another Boolean `true`, not 1 or "1" or [1]. It's advisable to always use the === and !== versions, but the "==" and "!=" are so common in other languages your fingers will type them without thinking. This is all a legacy from the early days. Here are the gory details: [Comparison tables](http://dorey.github.io/JavaScript-Equality-Table/)

### Switch{} statement

Rather than a long if/else chain, we can select among simple options with a switch statement.
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

  default:
    console.log("Unexpected user input", userInput);
}
```
This is neat and clear. Although, if you omit the 'break' the code will "fall through" to the next case. This is generally error-prone, a reader often doesn't notice it, and then you create hours of head scratching, most likely for yourself.

Always use the `default` catcher, even if you think it can never happen.

Having said all that, switch{} is a little archaic and rigid. It seemed a devilishly clever idea back in 1969-72 when Kernighan and Ritchie et al were writing C at Bell Labs on a PDP-11. With memory so tiny and CPU speeds so slow and 16-bit words, the compiler could construct an efficient machine code "jump table" where the 'switch' value, often just a byte ('q', 'r' above, or small numbers like 1,2,3,5,8,10) indexed into a table of offsets, and then jumped direct to the 'case' code. Such desperate efficiency is no longer needed. (But don't worry, we have replaced it with databases of your banks millions of customers which take 5 minutes to load your account, all is well for efficiency workers).

## Loops

### While {}

Just as with our conditional (if / else) statements, a while loop employs a boolean test that must evaluate to true in order for the instructions in the curly brackets to be executed. The instructions continue to be executed until the test condition becomes false. If the test condition is false at the start, the loop body will not execute at all.

```javascript
var x = 0;
while (x < 10) {    
  console.log(x);     // Should print about 10 times. Or 9, or 11 ? A good exercise to check.
  x++;   
}
```
### Do while {}

This is similar to the while loop, but the test is done at the bottom, after each iteration of the loop. One oft-quoted consequence is that the loop always executes at least once. But really the point is that it's just clearer to test some conditions at the bottom. The code can reflect your thinking.

```javascript
var x = 0;
do  {      
  console.log(x);    // How many times does it print now ?
  x++;   
} while (x < 10)
```

### For {}

Since this is a very common use of a loop, ie. running through a simple sequence of values, there is a simpler way to do it: the for{} loop. You can read the example below as: a) create variable x and set it to 0;  b) if x is less than 10 do the stuff in the loop body; c) increment x by 1 at the end and go back to b).

```javascript
for (var x = 0; x < 10; x++) {  
  console.log(x);     // This is a very common idiom. The loop will run exactly 10 times, for sure.
                      // Remember: x = 0; x < loopCount  :  gives exactly loopCount passes.
                      //           x = 1; x <= loopCount :  same, less common. Programmers like 0 basing.
} 
```
### Breaking out of loops

The `break` statement will terminate a loop. One common idiom is to have an endless loop, and break out when you have done what you need. Sometimes this is clearer to code than other options.

```javascript
while(true) {
  // do stuff
  if ( value === 100 ) { break; }  // Don't forget that semicolon
  // do more stuff
}
```

### For in, for of, forEach

There are further loop types that iterate conveniently over the elements of an array or object. I will show them without much explanation, they have some gotchas.

```javascript
var arr = [44, 33, 22, 11];
var obj = { "1st": 1, 2: 2, "3rd": 3, 4: 4 };

for (n in arr) {
  console.log("index is", n);   //  prints "index is 0, index is 1, index is 2, index 3"
}

for (n of arr) {
  console.log("value is", n);   //  prints "value is 44, value is 33, value is 22, value is 11"
}

for (n in obj) {
  console.log("accessor", n);   //  prints "accessor 2, accessor 4, accessor 1st, accessor 3rd". Note random order.
}

// forEach has a lot of functionality. Also see array.some(), array.every() etc. Basic example:

function funky(value) {
    console.log(value);
}
arr.forEach(funky);         // prints 44 33 22 11
```

The above loop types have some things to watch out for. One is that there can be unsuspected extra properties on arrays and objects, that your for-in/on/each loop will hand you. You may have to take precautions that you only iterate over the conventional "iterable" elements, ie. in the case of an array the elements arr[0] to arr[last]. That's if you just want to do conventional processing on array/object data.

However on other occasions you may want to see everything that's there, to do fancy stuff with object-oriented dynamic design. Then you can let the loops show you the works. All this is beyond the scope of this tut.

You will probably not need these loop types in p5.js. (These are not the loops you're looking for ...)

[A readable blog on forEach](https://thejsguy.com/2016/07/30/javascript-for-loop-vs-array-foreach.html) (He's grabbed a great URL there, "thejsguy.com").


## Functions

A function is a unit of reusable code, which can be invoked or "called" many times, possibly with different input values. They are a key part of any language. Functions help structure and organize your code: self-contained processes and computations can be neatly isolated in a function. 

Functions are named after mathematical functions: f(x) = x * x. In JavaScript this would become `function square(x) { return (x * x); }`

Other languages can use terms like "subroutine" or "procedure" to describe a function. Fortran IV used to provide SUBROUTINE which returned no value, and FUNCTION which did return a value. In modern languages a "function" can return or not return a value just as you wish, and you can also use or ignore the return value afterwards. 

A neatly self-contained function can be replaced with a better version at a future time: a standard example would be a "sorting" function. With low numbers of test data items that need to be sorted into order in some sort() function, a simple "bubble sort" might be fine. This runs in O(N2), which is academic speak for "Order N squared", meaning the time to sort a list of N items is approximately proportional to N squared. This goes up quite rapidly, but it's not going to be a problem until N reaches high numbers, maybe thousands or tens of thousands.

When you need to sort millions of things, you might need to replace your sort() function with a more sophisticated multi-phase tree/bucket/heap/shell sort, which can be O(n Log n) or better. Just change your sort function !  [\[full monty\]](https://en.wikipedia.org/wiki/Sorting_algorithm) [\[JavaScript monty\]](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

Here are simple functions:

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
  background(random(255), random(255), random(255));  // choose a number from 0 to 255 for red, green, blue
}
```

### Function arguments, or parameters

A function can accept values as input, known as arguments or parameters. Note that within the function code, the parameters are not the names of actual variables in your enclosing program, but are "place holder" variables limited to the scope of the function. To split hairs, the "parameter" is the name of the formal parameter, "person" in the first example below, it's a static term in the code source text. The "argument" is the value that gets passed in, a dynamic run-time thing, "name" in the code below, if talking about it from the callers perspective, or maybe again "person" if talking from the functions perspective.

When a function is run, the values passed in are temporarily assigned to the parameters defined in the function, until the function completes its execution and returns to the caller. After return, normally all data inside the function just "evaporates", its job is done. (Technically, the "stack frame" with all the function's data is popped off the stack).

In the case of simple variables supplied as function arguments, the value is "copied" to the parameter inside the function, and the caller's value for the variable can't be changed.

In the case of arrays or objects supplied as function arguments, a pointer to the actual array or object is passed to the function, and the caller's value _can_ be changed.

```javascript
var var1 = 1;
var array1 = [1, 22, 333];
var object1 = { "a":1, "b":22, "c":333 };
function example(v, a, o ) {
   v = 123;
   a[0] = 456;
   o.b  = 789;
}

example(var1, array1, object1);
console.log(var1);            // 1
console.log(array1);          // [ 456  22  333 ]
console.log(object1);         // { "a":1  "b":789  "c":333 }
```

Here are some functions with arguments.

```javascript
function sayHello(person) {
  console.log("Hello " + person);
}
var name = "Jenny";
sayHello(name);  // prints "Hello Jenny"
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
  return;     // You can explicitly make it clear where the function returns, if you like, even if it returns no data
}
drawEllipse(mouseX, mouseY);  // a nice circle, centre x,y radius 50 
```

Try this in the console: `function ff() { console.log("zippo"); }` then `typeof(ff)` then `ff` then `ff()`


### Arguments are optional

In JavaScript, all function arguments are in fact optional. This presents both convenience and some risk. 

Additional trailing arguments can be given to functions with great ease - p5.js uses this extensively, eg. [rect() call.](https://p5js.org/reference/#/p5/rect) However it can be difficult to know how many arguments are actually available, without good documentation, or access to the source code of the function.

Any arguments not supplied, but which the function attempts to use, have the value `undefined`.

```javascript
function show(a, b, c) {
   console.log(a, b, c);
}

show(1, 2, 3);  // prints  1 2 3
show(4, 5);     // prints  4 5 undefined
show();         // prints  undefined undefined undefined

setReactorControls(min);   // Err, was there a max ?
```

### Default arguments

To ensure all arguments have some useful default value, and protect against `undefined` causing havoc, you can specify default argument values in the function declaration.

```javascript
function show2(a = 2, b = 33, c = "cat") {
   console.log(a, b, c);
}

show(1, 2, 3);  // prints  1 2 3
show(4, 5);     // prints  4 5 cat
show();         // prints  2 33 cat
```

### Rest arguments

Given that a JS function can be called with any number of arguments, from none to any number, it's handy to have a facility to easily deal with them.

One facility is the `arguments` object. This puts all the arguments the function was called with into an object `arguments`. You can access them like this:

```javascript
function f1(a,b,c) { 
  for (var i = 0; i < arguments.length; i++) { 
    print(arguments[i]);     
  }
}

f1(1, 22, 333);      // Prints 1, 22, 333
```

The arguments object has some limitations. It's not a regular array, but a type of object. It has a length which you can access, as above, but it can't be "popped", "shifted" etc, which are things you might like to do when parsing your function arguments.

A neater method introduced in ES6 is the `...rest` syntax. This puts all the trailing arguments not specifically assigned to a named parameter, into a normal array. It's like the `varags` facility in C/C++.

```javascript
function f2(a, b, ...theRest) { 
  console.log("a = ", a);
  console.log("b = ", b);
  for (var i = 0; i < theRest.length; i++) { 
    print("trailing arg ", i, " = ", theRest.shift() );     
  }
}

f2(1, 22, 333, 4444);      
// Prints a = 1
          b = 22
          trailing arg 0 = 333
          trailing arg 1 = 4444
```

### Returning a value

The functions above take some action or change the state of the program (typically draw something, in p5.js), but they don't return any value. If you want your function to return a value, use `return someValue`. This is often at the end of the function, but can also be anywhere else in the function. 

```javascript
function addNumbers(a, b) {
  var c = a + b;
  return c;
}
var result = addNumbers(3, -10);
console.log(result);   // prints -7
```

```javascript
var name = "Jenny";
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
  var y = x + random(-1, 1); // use p5.js random() func. Two args allowed, min and max.
  return y;
}
var result = addJitter(10);
console.log(result); // 10.3 or 9.8 or ...
```


```javascript
function severalReturns(number) {
  if (number < 0 ) {
    return(number - 1);   // Note this terminates the function. An easy coding style, and not too bad if used clearly.
  }                       // Some people will be expecting the return at the end of the function. It's a matter of style.

  if (number > 0 ) {
    return(number + 2);
  }

  if (number === 0) {
    return(0);            // no change
  }
}

severalReturns(5);   // returns 7
severalReturns(-8);  // returns -9
```
### Recursion

JavaScript copes fine with recursive algorithms. The function calls and their local data just stack up on the "stack" and then unwind in the usual way. Here's the classic factorial(n) function:

```javascript
function factorial(n) {   
  if ( n === 1 ) {
    return 1;
  } else {
    return n * factorial(n-1);   // it's not a proper language tutorial without a recursive factorial function !
  }
}

fact(1)    //  1
fact(5)    //  120
fact(69)   //  1.711224524281413e+98   This was as high as my HP-45 Engineers calculator could go, with a 2 digit exponent 
```
<br>  
Let's try a two-legged recursion: the famous Ackermann function. This recurses down the two arguments, and will stack vast chains of recursive calls on the stack. It looks simple enough, but grows ferociously, in both computational data storage, and the final answer.

```javascript
function ackermann(m,n) {
   if ( m === 0 )           { return n+1; }
   if ( m > 0 && n === 0 )  { return ackermann( m-1, 1); }
   if ( m > 0 && n > 0 )    { return ackermann( m-1, ackermann(m, n-1) ); }
}

ackermann(0,0)   //  1    Ok so far.
ackermann(0,1)   //  2 
ackermann(0,100) //  101  This leg of the recursion is simple !
ackermann(1,1)   //  3
ackermann(2,1)   //  5
ackermann(2,2)   //  7    a doddle !
ackermann(3,2)   // 29    growing a little, what could go wrong ?
ackermann(4,1)   // Exception: RangeError: Maximum call stack size exceeded. Well, the answer is supposed to be only 65533, 
                 // but we ran out of stack space to store all the recursion levels.
ackermann(4,2)   // Exception: RangeError: Maximum call stack size exceeded. The answer here has 19,729 digits, ie. 
                 // approx 10^19729. We couldn't remotely represent the answer in 64 bits, never mind store all the recursion.
```

By raising the stack space to the maximum in the JavaScript configuration, we might just get Ackermann(4,1) to complete. Let's not bother. [Ackermann's function](https://en.wikipedia.org/wiki/Ackermann_function) 

### Closures

Just for fun let's briefly mention closures. These are an advanced topic which you will probably not need in your p5.js app code. 

Closures are a software design technique where some data and code are cleverly "encapsulated" and protected in a function. Rather than waffle on further, let's look at an example.

```javascript
var update = (function () {            // Note, unnamed function here. No name between "function" and ().
    var importantCounter = 0;          // This holds important data, that you want to tightly manage access to. 
    return function () {               // Another unnamed function.
       if ( checkAuthorisation() ) {
          return importantCounter += 1;
       }   
})();

update();  // returns 1
update();  // returns 2
update();  // returns 3
```

What's happening here ? "update" is defined as a function. Remember JavaScript has "first class" functions, or another way to say it, functions are "first class citizens", like other data types. So a variable can hold a function, which can be passed around and called. "update" also has an internal data item, importantCounter. 

Normally importantCounter would evaporate every time update() is called. But here the function becomes preserved as part of the definition of update(), and so does importantCounter. 

"update" becomes a callable function, which has access to importantCounter. But this is the only way to get at the counter, there's no shortcut. You have to call update() and pass some checks. 

At the time of the declaration and definition of update, at line "var update = ...", an internal function is called once and sets importantCounter to 0, and then it returns another function, which when called in future will make a check and then increment the counter.

After that, easy peasy. Each call of update() calls the check() code and then updates the counter.  

More sophisticated use of closures can make convenient but safe and reliable code. They are used a lot in Node.js and JQuery, two common JS utility libaries, and no doubt many others. I see mention of closures in libraries/p5.js !

[\[Wikipedia on closures\]](https://en.wikipedia.org/wiki/Closure_(computer_programming))

## Arrow functions

You may see these in code. They're a convenient short-cut for very simple utility functions. The arrow notation `=>` is used in the function definition.

```javascript
let x2 = (x) => x * x;               // x2 is a function which returns the square of x
                                     // Read this as: x2 = a function which maps x to x*x
a = 5;
b = x2(5);                           // b is 25

let func x2(x) {                     // The same thing defined with a standard function.
   return x * x;
}

let sum = (a, b) => a + b;           // An arrow function with two args
a = 1; b = 2; c = sum(a,b);          // c is 3
```

Arrow functions also allow some concise expression of larger but very "regular" operations. The examples below use some array features which we haven't covered. You can look them up if you're interested, eg. [array reduce](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

```javascript
let arr = [5, 6, 13, 0, 1, 18, 23];

let sum = arr.reduce((a, b) => a + b);            // 66

let even = arr.filter(v => v % 2 == 0);           // [6, 0, 18]

let double = arr.map(v => v * 2);                 // [10, 12, 26, 0, 2, 36, 46]
```


## Variable scope

Variables that you declare inside a function, and also the function arguments, are local to that function, and can't be accessed outside the function. This provides vital "encapsulation" and protection of the functions data. Otherwise a statement `x = y + 1` in one function could trample badly on a statement `y = x + 2` in another function, or at top level.

Variables declared outside of any function are known as "global variables" and can be accessed from anywhere in the program, inside or outside functions. These are convenient, and essential at times to pass around global information, but can create hazards. Try not to declare simple names as globals, like min, max, sum, total, error, count. These can clash with other declarations in functions, or at top level in other code modules concatenated with this one, and unfortunately, due to JavaScripts permissive nature, this can create silent errors. One protocol is to declare all globals as "g_total", or an Object member "g.total" to make things clear. Slightly ugly but could save your bacon one day.

Another option is to put all your code in one top level function, say main(). Then nothing "escapes" from main(), so that stops clashes with other concatenated code modules. Like p5.js say !

```javascript
<html>
<head>
<script> src="libraries/p5.js"></script>  <!-- load p5.js --->
<script>

  function main() {
    var str = "a carefree string";  // cannot clash with global "str" in p5.js. Yes, there is one.
    console.log(str);
  }
  main();                           // Call our whole code as a single function call: main()

  // Todo: should really make this a full p5.js prog with a setup() and draw() that draws something.
  // Otherwise the clash with str is not important.

</head>
<body>Not much of a body, this is a JavaScript example, not HTML</body>
</html>
```

p5.js has an "instanced" mode, which is another similar way to do this. See the tutorial [Global and Instanced Mode](https://github.com/processing/p5.js/wiki/Global-and-instance-mode)


Here's another example of global and local scopes:

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

If you use the same name as a global variable, and also as a local function variable, the function variable overrides within the function. This is ok in many situations, despite what we said above. For example simple count variables like i, j, k that you are sure have a short life. (Famous last words ?).

```javascript
var g_data = [ 1, 22, 333 ]    // global array
var i,j,k;                     // global simple control vars. A common style from older languages. Not even initialized! 
var offset = 3;                // global var, but who would know?

for (i = 0; i < g_data.length; i++) {   // a loop at top (global) level
  g_data[i] += 2;          // Adjust g_data values somehow
}

function adjustData() {
  var i;                   // This is a different i from the global i, but we have decided to ignore that.
                           // For absolutely temporary vars like i, j, k, tmp, str, you can ignore scope if you like.
  for (i = 0; i < g_data.length; i++) {   
    g_data[i] += offset;   // Ok: offset is still the global var. Could be better as g_offset
  } 
}

adjustData();
console.log(g_data[2]);   // prints 338 (333 + 2 + 3)
```  


### New scope declaration: let

The issue of the scope of identifiers in programming languages is an important one, as you can see from the hammering it's getting here. 

You can have languages where everything is in a single global scope, as in simple ancient BASIC. Programming is easy, but the possibility of accidental errors is higher.

You can have modern languages where scope is very restricted. Errors are reduced, but coding needs more care at times. Nothing wrong with that.

JavaScripts original `var` style was very unusual and much disliked by some. JavaScript has recently (ECMAScript 2015, aka ES6) introduced the `let` keyword to augment and largely replace the `var` keyword. 

Some more explanation of `var`: The scope of a variable declared with `var` is the whole of the function it is in. Even it is declared towards the bottom of a function, or is a trivial loop variable. There is an awful expression called "hoisting", where any `var` declaration is treated as if it was "hoisted" to the top of the enclosing function:

```javascript
function hoistingExample() {
  var cat = "cat";
  // i and j below are treated as if they were declared here, but not initialised, eg. just var i, j; So use of them is
  // allowed, but will almost always produce an error as they are undefined. Possibly a silent error, woo hoo.

  if (whatever) {
     // miles of code here, pages and pages, you forget what you wrote last week.
     if (rareEventNotWellTested) { 
        var k = i + j;   // Error, undefined. i and j exist due to hoisting, you can reference them,
   }                     //  but they have no value yet. A recipe for problems.
  }

  for (var i = 0; i < 3 ; i++) {
     var j = i * 3;   // i and j have valid values here, all is ok.
  }
}
```

However a variable declared with `let i = 0` has only "block scope". In the following examples, it exists only in the loops or blocks shown. This is much safer. For variables you want to exist inside the whole function, put them at the top.

```javascript
function drawStuff(param) {

  let j = 5;                             // This "j" exists in the whole function, unless overridden in a smaller block.

  for(let j = 0; j < 99; j++) {          // Draw some ellipses. Note this temporary "j" is only scoped inside this loop. 
    drawCircle(j*20, j*20, j*5, j*10);   // It does not affect, and is not affected by, other "j" vars in the function. Good. 
  }

  if (param > 5 ) {
     let j = param * 7;                 // This "j" is similarly unique to the if block. No interaction with other j's.
     drawCircle(j*3, j*3, 10, 20);   
  }

  if (j > 100) {
     drawCircle(j*9, j*9, j, j);        // Finally we use the "function scope" j we set up at the top.
  }
}
```

The [\[MDN monty\]](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)  

[\[A rather flamboyant blog about let and var\]](https://dmitripavlutin.com/variables-lifecycle-and-why-let-is-not-hoisted/) People get very excited about all this.

The bottom line: always use `let` in new code, forget `var`. Place `let` declarations at the top of each function, for things which will or may be used throughout the function. Use `let` inside loops and blocks to restrict temporary variables to that region only.

### Other points about "let"

There are some other changes/benefits to let. `let str = "abc"` at top level does not create a global "str" which can clash with other js modules, like p5.js. From the MDN monty above ...

```javascript
var x = 'global';
let y = 'global';
console.log(this.x); // "global"
console.log(this.y); // undefined. This solves a key problem when using a library like p5.js
// Note, "this" at top level is the explicit global entity, your whole universe of data and code and libs in use.
```  
   

Another `let` quirk: you can't redeclare a name in the same scope. This is a good thing, redeclaring the same name in the same scope is sloppy, although it's fine with `var`, and indeed we kind of accepted it with those temp `var` variables i, j, k we talked about before. JavaScript is quite a sloppy language. I didn't want to say that earlier.

```javascript
let foobar = 1;
let toto = foobar + 3;
let foobar = 2;  // SyntaxError: Identifier 'foobar' has already been declared
```

For the same reasons, declarations toughen up in `switch{}` blocks:

```javascript
switch(x) {
  case 0:
    let foo = x;
    doStuff(foo);
    break;
    
  case 1:
    let foo = x * 2; // SyntaxError: redeclaration. Already declared in switch{} block. Just drop the "let".
    doStuff(foo);
    break;
}
```

If you want, you can fix the above by leveraging the same block-scope rules that caught you out in the first place. Below the "foo" are each unique to their single `case{}` block. The simple switch/case is getting messy though. An if/else style might be just as easy. Just my $0.02

```javascript
switch(x) {
  case 0: {
      let foo = x;
      doStuff(foo);
      break;
    }
  case 1: {
      let foo = x * 2;
      doStuff(foo);
      break;
   }
}
```

There are other tiny subtleties with changing from `var` to `let` but I think the average p5.js beginner will have reached their limit by now ! I know I have. Remaining quirks are really for the designers of big systems, like the whole p5.js library. They take many precautions and scope and encapsulate well, so that you can code simply and safely.

### The const declaration

Many languages have a "constant" facility, so you can safely set up constants in your program. EcmaScript 2015 introduced the `const` keyword. This has the same rules as `let` but you cannot change the value once it has been defined.

```javascript
const pi = 3.141592653589793;     // You feel you want some precision. In fact that's the value of Math.PI

function area(radius) {
  return (pi * radius * radius);
}

// Include some other persons code here ...

function circumference(radius) {
   let pi = 3.142;                // Rough old code here. Probably an Engineer, used to slide rules ...
   return( 2.0 * pi * radius );   // Fortunately, denied !! You can't change the const pi
}
```

## Objects part 2: objects as classes

We introduced basic objects above, such as `let obj = { "name":"Vincent", "age":3 }`. At that stage they were pretty much just a convenient way to have a type of "array" addressable with a text string key. Handy but not going to change the world. Now let's go ahead and add "methods", ie. internal object functions, to produce a full-featured dynamic object. This gives us the effective functionality of a "class", as provided in languages such as C++ and Java.

Let's proceed gradually here, and build up the concept. First, we could create an empty object with `obj = {}` or `obj = new Object`. Both create the same thing, an empty object. Try it in the console. The `new` syntax is useful when we want to create a lot of objects: `obj = []; for (let i = 0; i < 100; i++) { obj[i] = new Object; }`. This creates an array of 100 empty Objects, obj[0] to obj[99].

Next we want to add some plain "data" properties to an object. We could do this like so:

```javascript
cats = [];                     
for (let i = 0; i < 99; i++) {  
  cats[i] = new Object;
  if ( i === 0 ) {
    cats[i].name = "Margot";    // this is data for cats, by the way, if that's not obvious
    cats[i].age = 8;            // probably less than 15 ?        
    cats[i].color = "black";    // not going to include yellow, green, blue
  }
  if ( i === 1 ) {
    cats[i].name = "Sam";
    cats[i].age = 2;
    cats[i].color = "white";
  }
  ...
}
console.log(cats[0]);   // {name: "Margot", age: 8, color: "black"}

```

However it's more convenient to use a function notation, and create a "constructor" for our objects. The term "constructor" is used in C++, Java etc. for a function which creates a class object. Here the constructor is the function Cat(). 

```javascript
function Cat(Name, Age, Color) {
   this.name  = Name;             // "this" refers to this instance, ie. the Cat we are creating
   this.age   = Age;
   this.color = Color;
} 

cats = [];  
cats[0] = new Cat("Margot", 8, "black");   // the "new" forces a permanent object to be created,
cats[1] = new Cat("Sam", 2, "white");      // without it the function call would just return undefined and have no effect

console.log(cats);   // Shows something like ..
                     //  (2) [Cat, Cat]            // this is console "icing", but useful. 
                     //    [
                     //      0: Cat {"Margot", 8, "black"}
                     //      1: Cat {"Sam", 2, "white"}
                     //    ]
```

The "this" notation is a common one in Object Oriented Programming, or OOP. It always refers to the overall "thing" we are inside, or working with. At top level in a JavaScript program, "this" refers to the whole program invocation. We mentioned it above when talking about accidental creation of global variables. When JavaScript is used in a web environment, the global top level object is "window", referring to the screen/window/canvas hierarchy. When used as a standalone JavaScript interpreter, eg. the Mac "jsc" command-line tool we mentioned earlier, "window" is not there.

You can access and modify the plain properties of objects directly by using `.propertyName`.

```javascript
console.log(cats[0].name);    // "Margot"
cats[0].name = "Robbie";      // change name to "Robbie" 

cats[0].age++;                // Margot/Robbie is getting older
console.log(cats[0].age);     // 9
```

### Adding methods

While properties are like variables within an object, methods are like functions within an object. They are set and accessed in much the same way. Let's extend our definition of the object type Cat.

```javascript
function Cat(Name, Age, Color) {
   this.name  = Name;    
   this.age   = Age;
   this.color = Color;

  // Add some methods

  this.greet = function() {                               // method greet()
    console.log("Hello, I'm " + this.name);
  }

  this.aboutMe = function() {                             // method aboutMe()
    console.log("Hello, I'm " + this.color + " and aged " + this.age);
  }

cats[1].greet();          //  "Hello, I'm Sam"
cats[1].aboutMe();        //  "Hello, I'm white and aged 2" 
```

The constructor function above sets some properties of Cat, then it adds two methods, "greet()" and "aboutMe()". These are written as unnamed or anonymous functions, but really they do have an effective name: they are preserved in Cat.greet() and Cat.aboutme(). 

It's useful to be completely comfortable with unnamed functions:

```javascript
function doSomething() {                     // First definition
  console.log("I'm doing something!");
}

var doSomething = function() {               // Second definition. This is identical to the first.
  console.log("I'm doing something!");
};
```

These two definitions are the same, just written differently. In the second case, the function is saved in the variable "doSomething".  Remember in JS, a variable can be anything - a string, a number, a boolean - but also a function. 

In the first case, this variable name is stuck after the word "function", in the second, the variable is explicitly stated first, then the function is assigned. They mean the same thing, so it's helpful to get used to seeing both forms.

Both forms allow you to invoke the function with `doSomething()`.

So turning back to the method declaration in Cat, it starts to look more familiar. It's very similar to the new function definition format we just saw, but `var functionName = ` is replaced with `this.functionName = `. This is because, just like the properties, we use `this.` to say that the method belongs to the object being created.

Calling these methods on an instance looks similar to accessing properties, except we use the () notation to order a function call.

```javascript
cats[0].greet();      // "Hello I'm Margot" (or Robbie)
cats[0].aboutMe();    // "I'm black and aged 8" (or 9)
```

An "instance" is an OOP term for an instance of an object or class. So cats[0] is an instance of Cat. It's a "thing", ie. an "Object", with internal data: name, age, color - and internal callable methods: greet(), aboutMe().

### The Delete operator and Garbage Collection

This is a good place to briefly mention the subject of memory management. Languages which allow you to dynamically create things during execution - like arrays, objects, arrays of millions of objects - must provide a way for that memory to be released when necessary. Even a modern JavaScript interpreter only has maybe 500 Mbyte of memory for dynamic data by default. You can configure it up a bit, to maybe 2GByte or 4Gbyte. But if you have a program consuming memory because it allocates dynamic things and doesn't delete them, 4GBbyte might fill very soon after 1/2 GByte.

Languages like C++ and Java have an ability to "delete" or "free" objects which have been created. This is aimed at cleaning up and removing dynamic data which you have created, and you know is not needed anymore. It's important sometimes to do that, to prevent memory usage building up, and prevent creating slow "memory leaks". Memory leaks are a problem in long-running codes - after days or weeks even the most carefully coded application can gradually increase its memory usage, and eventually fail. These are very pernicious errors and hard to track down - it could be smallest thing which is building up, some inconsequential temporary data.

The alternative approach is very good automatic "garbage collection". What on Earth is that? It's the automatic deletion and clean-up of things which can't be used anymore. If a variable, array, object, or anything else, has gone completely "out of scope" and can't be legally referenced any more, then JavaScript can delete it and free up its memory. 

There are other situations where things might appear to be referenced, but the system can still delete them. The textbook example is a "cycle" of references, where say a refers to b, b to c, c back to a. `a = b+1, b = c+1, c = a+1`. (This is not a proper example, we need stronger references, where a is say an Object which must fetch some of its data from b, etc). At a first level, it looks like every item has a reference to it, and can't be cleaned up. But stepping back to a wider view, there might be no other reference to a, b or c anywhere. Hence the whole lot can be cleaned up.

JavaScript has an advanced Garbage Collector system which tracks use of data, and references to data. If nothing references some data any more, it is cleaned up. 

Having said all that, the explicit Delete statement in JavaScript does not in fact free up memory. It only removes the definition of a property.

```javascript
let astronaut = {
  firstName = "Neil";
  LastName = "Armstrong";
}

console.log(astronaut.firstName)      // shows "Neil"
delete astronaut.firstName; 
console.log(astronaut.firstName)      // shows "undefined"
```

You might never need to use this. If you don't need "firstName" any more, just don't use it. It's ok to leave it sitting there as a property on "astronaut" which you never use. There would be many instances where you don't use some properties which are available on an object, eg. in some pre-packaged code or library you are using.

Re memory usage, one good practice is never to create large volumes of data at top level, in the global scope. These never go out of scope and can't be garbage collected. Create large volumes of data in some subsidiary function, and try to return from that function when you are done with it, or return periodically. The Garbage Collector can then clean things up for you.

In a small to medium p5.js application you will never need to think about this !

The [gory details]:(https://developer.mozilla.org/en-US/docs/Web/JavaScript/Memory_Management) 



### A p5.js example

Now that we have described an Object which has properties and methods, we're ready
to develop a p5.js example using dynamic objects, which will run and draw something. Graphical toolkits are good for illustrating programming concepts, a picture is worth a thousand words and all that. (This code is similar to numerous examples elsewhere in Processing).

```javascript
// This data at the is global to the app.

const numShapes = 30;
const baseRadius = 5;
let shapes = [];        // Declare array to hold shape objects

function setup() {      // Runs once at beginning of app

  createCanvas(800, 600);
  
  // Use HSB colors in our app, so we can get easy changes of just color (hue).
  colorMode(HSB, 100);   // H,S,B will be in range 0 - 100

  // Create each object

  for (let i = 0; i < numShapes; i++) {
    let x = random(1, width - 2);       // Centre our circle randomly somewhere in the window
    let y = random(1, height - 2);
    shapes[i] = new Shape( x, y );
  }
}

function draw() {

  background(0, 0, 5, 10);      // Dark grey with a small alpha value, this achieves a blurring effect.
  noStroke();                   // No outline of shapes

  // Update some controls for our shapes.

  let cycle = 200;  // Change the shapes appearance over a cycle of n frames

  let percent = (frameCount % cycle) / cycle;     // 0.0 to 0.999
  let percent2 = percent;                         
  if (percent > 0.5 ) { percent2 = 1 - percent }  // 0.0 to 0.5, then back down

  radius = baseRadius + 30 * (percent2);          // Grow and shrink the radius

  // Update and display each shape in the array

  for (let i = 0; i < shapes.length; i++) {
    shapes[i].setRadius(radius);   
    shapes[i].followMouse(0.008);   // rate to follow mouse at
    shapes[i].setColor(percent);    // change hue as well
    shapes[i].display();            // draw it
  }
}

function Shape(xpos, ypos) {

  // Set initial values for properties, as supplied in the constructor, ie the New() call

  this.xpos = xpos;
  this.ypos = ypos;
  this.hue = 0;                     // value not important, just good practice to init to something

// Some methods to operate on an instance of Shape

// Method to set the radius

  this.setRadius = function() {
    this.radius = radius;
  }

// Method to move the shape's position towards the cursor position.
// Don't move if closer than a certain distance.

  this.followMouse = function(fraction) {

    let xdiff = mouseX - this.xpos;
    let ydiff = mouseY - this.ypos;

    let dist = Math.sqrt(xdiff * xdiff + ydiff * ydiff);

    if ( dist > 100 ) {
      this.xpos += xdiff * fraction;
      this.ypos += ydiff * fraction;
    }
  }

// Method to reposition the shapes randomly. This is only because our simple
// follow-the-cursor code eventually clumps all the shapes together :=(

  this.resetPos = function () {
    this.xpos = random(1, width - 2);
    this.ypos = random(1, height - 2);
  }

// Method to set color of the shape. Use the HSB system, and vary hue from 0.0 to 1.0

  this.setColor = function(hue) { 
    this.hue = 100 * hue;
  }

// Method to draw the shape to the screen. This is it! draw those pixels.

  this.display = function() {
    fill(this.hue, 100, 100);
    ellipse(this.xpos, this.ypos, this.radius, this.radius );  // a solid circle
  }
}

// Separate callback function for user keystrokes.
// Allow any key to reset the app.

function keyTyped() {

  for (let i = 0; i < numShapes; i++) {
    shapes[i].resetPos();
  }
}
```

Here's the code working ... [Open Processing](https://www.openprocessing.org/sketch/507368)

I think I'm going to say nothing more, just let that picture / 1000 words thing happen. Look through the code, with the OpenProcessing page also running. You can experiment with changing the OpenProcessing version by hitting the </> tag at the top. 
 

## The new Class statement

ECMAScript 2015 (ES6) introduces the "class" statement. This is an attempt to give JavaScript something that looks close to the class system of languages like Java and C++.

It's effectively [syntactic sugar](https://en.wikipedia.org/wiki/Syntactic_sugar) which allows you to declare classes, and members, methods, constructors etc. with a similar syntax to other languages. However it doesn't actually add any new underlying capability. What you end up with is the same as you could have set up without "class".

Authors who have transitioned to using it say it's concise and handy. I'm just going to include links here to some resources. As always you can can find many more by searching.

[MDN reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)   
[More info](https://javascript.info/class)  
[More info](https://coryrylan.com/blog/javascript-es6-class-syntax)  



## Code formatting, style, good practices, common mistakes

### Comments

Comments in code document what's going on. They should be reasonably succinct though, there's no point explaining every line. The commenting below is too trivial, and just distracting. 

```javascript
while ( true ) {         
  b = a + 1;                   // add 1 to a, store in b
  if (b > 100) { break;}       // if b greater than 100, quit the loop
}
```

As a rule of thumb, have a line or two of comment for every 10-30 line paragraph of code, explaining what the block is going to do. Put a few words of explanation to the right of any very important statement. That's -very- subjective.

Comments in JavaScript are similar to comments in Java or C, C++.  `//` comments are often referred to as C++ comments, and `/*  */` comments as C comments. However C, C++, Java, C#, Objective-C and others all now allow both styles.

Commenting is also useful for quickly removing or adding back in chunks of code (better than deleting the chunk). 

```javascript         
  // single line comment
  a = b;  // comment after a statement   
   
  /* 
    multiple
    line C style
    comment
  */

 /*
  * Some prefer this style
  * Easier to see the commented-out section
  * The lone stars have no function, they're just text
  */


// if (x > 5) {       // You can comment out a whole block C++ style
//    a = 123;
//    b = 456;
//    c = 789;
// }

aa == bb  /* + cc */  + dd;  // You can comment out just a snippet. A bit unclear though.

if (false) {        // This style is also ok for de-activating a piece of code.
  a = b + 1;        // Some people use if(0). This is falsy enough as a stand-alone flag.      
  c = d * 5;;
  createImage(500, 500);
}
```

Avoid inter-mixing and nesting comment styles.

```javascript
// /* a = 1 */  +2;            // what does this mean ? does the */ terminate the // ?
   /* /*  b = 1;  */ */        // and this ? who knows. Don't go there.
```

### Indentation

There are many popular styles of indenting. (The good thing about standards is, there are so many to choose from!) (That's my favourite Dad tech joke).

Generally whenever you introduce curly braces, you should indent everything inside. Anything from two to eight spaces is common, but typically 2 to 4. Don't use tabs, they are archaic and will just cause endless problems down the track. If you're accustomed to hitting the Tab key, configure your editor to turn it into n spaces.

A great tool is an automatic formatter. I use [AStyle](http://astyle.sourceforge.net/) from the Mac command line. Properly indented code will line up well, help you understand your code flow, and alert you when you have forgotten to close a loop with a brace } or whatever. You can configure the formatter for different indent and spacing and padding styles. (Did I mention the great thing about standards ...) 

p5.js developers use [prettier](https://prettier.io/) and [ESlint](https://eslint.org/).  A good guide to installing Prettier on Mac is here: [Installing Prettier](http://blog.teamtreehouse.com/install-node-js-npm-mac). Prettier has only a few style options and is aimed at maintaining a uniform style of code in large collaborative projects, like p5.js on GitHub.  

Academic note: Python uses _nothing but_ spaces to indent and block code. Correct indentation is key.
```javascript
if pwd == 'secret':                         // A Python if/else block
    print('Logging on ...')
else:
    print('Incorrect password.')
    print('Try again')
```

### Padding

The amount of space padding around terms can improve clarity of code. But too much can be too much. 

```javascript
distance = Math.sqrt(((x1-x2)*(x1-x2))+((y1-y2)*(y1-y2)));                                 // A little dense
distance = Math.sqrt( ((x1 - x2) * (x1 - x2)) + ((y1 - y2) * (y1 - y2)) );                 // Better
distance = Math.sqrt( ( ( x1 - x2 ) * ( x1 - x2 ) ) + ( ( y1 - y2 ) * ( y1 - y2 ) ) );     // Mmmm .. too sparse ?
```

The formatter can apply padding rules to function calls, expressions, if{} blocks, loops, array indices, etc. There are maybe 8 or 10 areas you can adjust. But there are pre-packaged choices that give you a standard set. Here's mine, I just use the pre-packaged Java style with a couple of mods.

```javascript
cat ~/.astylrec
--style=java
--indent=spaces=2
--pad-oper
--verbose
```

### Line continuation

JavaScript allows some lines to continue with a backslash \ on the end. Not a very clear style in general. But can be useful for some big block of text you need to get into the code.

Also plain statements can run over more than one line. Not usually very clear.

```javascript
let str = "A hugely long text string which you decide to split over \
two lines like this";
console.log(str);   // "A hugely long text string which you decide to split over two lines like this"

let str2 = "A long documentation text which needs to be multiline, so we\n\
use escaped newlines in it blah blah blah blah blah blah blah blah blah\n\
more blah, the end.";
console.log(str2);   // A long documentation text which needs to be multiline, so we 
                     // use escaped newlines in it blah blah blah blah blah blah blah blah blah
                     // more blah, the end.

fred = 1 + 2 +       // Very bad practice
  3 + 4;             
console.log(fred);   // 10  .. this time
```

### Semicolons

A code statement almost always ends with a semicolon.

```javascript
let x = 10;
if (a > 1) { callFunc(); }   // Must have semicolon here. Some other languages don't enforce that, the } is enough.
if (a > 99) {
  callFunc2();
}                            // No semicolon needed after the }
```

Semicolons are partly optional in JavaScript. You can read more here [semicolon blog](http://news.codecademy.com/your-guide-to-semicolons-in-javascript), but a strong recommendation is to use always use semicolons. There are rare gotchas which will cause you problems if you leave them off.

There's a nice academic point that comes up here, and in all languages with a statement terminator. Is the semicolon a terminator ? `(a = 1; b = 2;)` or a separator ? `(a = 1; b = 2)`. Aha. Well.

### Strict mode

JavaScript introduced a "strict" mode to tighten up coding practices and prevent some types of errors (in ECMAScript 5, JavaScript 1.8.5, in 2009). Other languages also have a strict mode, eg. Perl. This tends to get added later in the day, when problems develop with the original design.

Just place `"use strict";` at the top of your whole code, or in individual functions if you want it to only apply there.

Strict mode makes certain kinds of risky practices illegal. The most important one is undeclared variables (or arrays, objects, etc).

Without Strict mode, it is legal to just write `x = 123;` anywhere. JS assumes you meant `var x = 123` and just creates x for you. I haven't even mentioned that in this tutorial because it's such bad practice. But this makes accidental typos very easy:

```javascript
// Top of code
let reactorSettings = [1, 2, 3, "fast"];

// Much further down
reactorsettings[3] = "stop";     // oops, forgot the capital S, JS silently creates a new array reactorsettings. We're doomed.
```

But with strict mode:

```javascript
// Top of code
"use strict";
let reactorSettings = [1, 2, 3, "fast"];   

reactorsettings[3] = "stop";     // ReferenceError: reactorsettings is not defined
```

This will also prevent unwanted global variables being created. If you have a rogue undeclared `x = 123` in a function, it is created as a global variable. This can clash with data at top level, and in other functions, and in other libraries like p5.js. 

You should always use Strict mode !

The odd syntax `"use strict";` is so the instruction is ignored by an old JavaScript engine which doesn't know what it is. A statement like `"use strict";` is just an isolated string with no computational effect, like `"Cool bananas;"`. It's parsed, created, then thrown away by any engine that isn't looking for it. Some other languages warn about this: "Warning, statement has no effect". Isolated expressions are easy to create: `var x = y;+z;`. You meant `y+z;` but z got orphaned and had no effect.

There are a number of other practices which are disallowed in Strict mode: [Strict mode](https://www.w3schools.com/js/js_strict.asp)

### Style checkers

There are quite a few style checkers for JavaScript. Two well-known ones are [JSLint](http://www.jslint.com/) and [JSHint](http://jshint.com/).  You can cut and paste code into their online versions and check quite a lot. You can also download and install locally JSHint. They are best at standalone JavaScript programs. Checking a large p5.js app may throw up lots of complaints like "don't know what function createImage() is". There are ways to tell JS[HL]int what external functions and terms you're using, so you're not flooded with these warnings. I haven't pursued that.

Note the JSLint term comes from the old C style checker "lint", which picked up small imperfections in your code like lint on your clothes. 

### Common mistakes

We have already mentioned a few risks to watch out for. Here's another selection of common mistakes.

```javascript
let x = 0;          
if (x = 10) { // some code }      // Accidentally used = instead of == or ===. The comparison wrongly returns true,
                                  // and the code block executes, since the result of (x = 10) is 10, which counts as a
                                  // true value in loose comparison.

let x = 10;                       // Be aware of loose comparisons
let y = "10";
if (x == y)  { // some code }     // This will match, code will run
if (x === y) { // some code }     // This will not match, code will not run. 

let x = 10;                       // Switch statements invisibly use exact === comparison !
switch(x) {
    case 10: alert("Hello");      // We get an alert here.
}                
switch(x) {
    case "10": alert("Hello");    // We don't get an alert. Good really, but not if you had assumed otherwise.
}

let x = 10 + 5;                   // x is 15.     Be aware of string + number concatenations ... 
let x = 10 + "5";                 // x is "105"   You shouldn't be doing this anyway.
let x = "11"; y = +x;             // Forces y to numeric 11, if you must do these things
let x = 12;   y = "" + x;         // Forces y to string "12". Ugh. 

if (x == 19);
  { // code block }        // This will always execute, since the semicolon has orphaned the block. Easy to do.

function myFunction(aa) {  // Never break return statements
    let
      power = 10;     // This is poor practice, but works; power is set to 10
    return            // Returns undefined, since JS completes the statement as early as possible, as "return;" 
      aa * power;     // This is orphaned, and in fact never executes.
}

person = {firstName:"John", lastName:"Doe", age:46,}   // last comma is legal but bad practice. Old IE versions will fail
points = [40, 100, 1, 5, 25, 10,];                     // ditto.

if (myObj !== null && typeof myObj !== "undefined")    // Bad way to test if myObj exists. if myObj is undefined, the first 
                                                       // test against null errors with "myObj is not defined"
if (typeof myObj !== "undefined" && myObj !== null) {  // Better, typeof will safely check for undefined, then we test null.

for (var i = 0; i < 10; i++) {  // Quick re-visit of 'var' issues ... 
    // some code
}
var j = i;   // j = 10. For var variables, the i is still defined after the loop. This is risky design. You should
             // never rely on the end value of a loop. Many things can cause it to be different. Always use let here, 
             // ie. in the loop, then i will not be valid and you won't be able to make this mistake. 
```

### JavaScript versions

Just some background on JavaScript versions - you won't need this much for your p5.js apps.

JavaScript version naming is very messy. There are terms like JavaScript 1.7, ECMAScript 2015, ES 2015, ES6. These are all approximately the same ! 

JavaScript has moved away from the "JavaScript 1.x" terminology. It's now versioned in terms of ECMAScript. But this has quirks too. The most widespread version, which you can rely on in all browsers, is ECMAScript 2015, or ES 2015, or ES6. This is because the 6th edition of ECMAScript was released in 2015.

There is no easily accessible internal version number in JavaScript. One traditional hack to get a version was to put this in your index.html:

```javascript
  <script language="javascript">var js_version="1.0"</script>
  <script language="javascript1.1">var js_version="1.1"</script>
  <script language="javascript1.2">var js_version="1.2"</script>
  <script language="javascript1.3">var js_version="1.3"</script>
  <script language="javascript1.4">var js_version="1.4"</script>
  <script language="javascript1.5">var js_version="1.5"</script>
  <script language="javascript1.6">var js_version="1.6"</script>
  <script language="javascript1.7">var js_version="1.7"</script>
  <script language="javascript1.8">var js_version="1.8"</script>
  <script language="javascript1.8.5">var js_version="1.8.5"</script>
```

So js_version shows up in your main code as perhaps "1.7". But as noted above these numbers have little meaning any more.

In actuality, all the major browsers try to keep up with the latest ECMAScript spec, currently ES June 2017, aka ES8. Chrome, Firefox, Safari support 95%+ of the latest ES8 features, and also some of their own extensions. Edge is a little behind, and IE even further. 

To test whether your JavaScript engine or browser has a new fancy feature, you have to check for it explicitly. One quick example - check if the "geolocation" feature is in the system. A note here: "navigator" persists in the Web world as an internal term for your browser, from the old Netscape Navigator. 

```javascript
if("geolocation" in navigator) { // use it }    // just check for the property we want, at the top-level
```
There's a library called Modernizr [Modernizr](https://modernizr.com/) which simplifies all these feature-existence checks. 

References:  
[JavaScript versions](https://en.wikipedia.org/wiki/JavaScript#Version_history)  
[ECMAScript versions](https://en.wikipedia.org/wiki/ECMAScript#History)  
[Feature detection](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Feature_detection)  

### Performance, efficiency, profiling

This is very well treated in another tutorial here.

[Efficiency and profiling](https://github.com/processing/p5.js/wiki/Optimizing-p5.js-Code-for-Performance)

### The Bottom Line

In this tutorial we've mentioned a number of times that JavaScript is sloppy, and had fun documenting many hazards ! But that's true of all interpreted languages. They allow loose (creative?) coding, and leave detailed checking of many things until run-time, unlike languages such as C++ and Java which use detailed compile-time checks.

The pay-off is flexible design of course, but also much faster development, rapid turn-around when testing code, and a much more enjoyable experience. For example, compiling a large C++ program can take a loooong time, many minutes or -much- longer if it pulls in vast libraries, subclasses loads of things from those libraries, tries to use multiple inheritance to join two chains of library classes. It explodes a bit like Ackermann's function, literally (you have been paying attention, right?). It's a long time to wait to just find you forgot some small thing. In the development phase of code you want rapid turn-around: edit, run, test in a few seconds.

An interesting paper describing all this is John Ousterhout's seminal paper from the late 90's [The Rise of Scripting Languages](https://web.stanford.edu/~ouster/cgi-bin/papers/scripting.pdf). Ousterhout is the original driver behind the scripting language Tcl and its companion gui builder Tk. The paper is based a lot on Tcl/Tk but the discussion applies equally to JavaScript. The rigorous compile-time checking of languages like C++ and Java don't always produce that much gain: development is *much* slower, maybe 20x, than script approaches; reliability is not much different in the end; performance may not be much different - your code is usually limited by things you don't have control over: graphics rendering power, disk speed, network speed - and there's plenty of cpu these days to drive the interpreted JavaScript engine.

So despite it's looseness and oddities JavaScript is quick and fun and pretty reliable to work with. Get stuck in !


## Todo:


