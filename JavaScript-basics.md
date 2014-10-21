JavaScript is a scripting language that is typically used on web pages where it runs client-side (within the web browser). It is a general purpose language with a lot of built-in functionality for interacting with elements on a webpage and responding to actions initiated by the user.

Although the JavaScript has "Java" in it's name, it isn't related other than by the fact that it looks something like Java. JavaScript's official name is ECMAScript (ECMA is the European Computer Manufacturers Association, a standards body). It was initially created by Netscape Communications. ([Wikipedia: JavaScript](http://en.wikipedia.org/wiki/JavaScript))


# The `<script>` tag

JavaScript can be placed anywhere within an HTML document, although it is typically included in the "head" section of the HTML, and is specified by the use of `<script>` tags:

```html
<html>              
  <head>              
    <script type="text/javascript">              
      //JavaScript goes here

    </script>
  </head>              
</html>              
```
	
You can also write JavaScript in file external to the HTML and point to that file in a script tag.

```html
<script type="text/javascript" src="myscript.js"></script>
```

# Comments

Comments in JavaScript are similar to comments in Java or C:
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

# Console

One of the first things we probably want to learn is how to get debugging output. You can write to the console by using the built-in console.log method:
```javascript
console.log("hello");
```
In order to see the console on Chrome, select "View" > "Developer" > "JavaScript Console". Use it often!

# Variables

A variable stores a value in memory so that it can be used later in a program. The variable can be used many times within a single program, and the value is easily changed while the program is running.

The primary reason we use variables is to avoid repeating ourselves in the code. If you are typing the same number more than once, consider making it into a variable to make your code more general and easier to update.

## Data Types

JavaScript is a "loosely typed" or "dynamic" language, meaning you don't have to declare the types of variables ahead of time. The type will get determined automatically while the program is being processed. Other languages such as Java are strictly typed and each variable must declare the type of the data it will contain. Even though you don't have to declare types, JavaScript does have different data types.

### Number

A number with a decimal point. In other languages this is typically called a float. It can be written with or without the decimal point, the processor will interpret it as a floating point number.

```javascript
var x = 5;
var y = 1.223;
var z = -300;
```

### String

A series of characters. These can be defined with either single or double quotes.

```javascript
var x = 'hello';
var y = "maybe tomorrow";
```

There are a number of built-in JavaScript properties and methods that let you manipulate strings. You can see them all [here](http://www.w3schools.com/js/js_string_methods.asp), a few of the most common follow.

**length**

Gives the length of the string.

```javascript
var str = "I like to eat pickles."
console.log(str.length); // 22

**indexOf(str)**

Returns the index of (the position of) the first occurrence of a specified text in a string. Returns -1 if the search string is not found.

```javascript
var str = "I like to eat apples.";
var pos = str.indexOf("eat");
console.log(pos); // 10
pos = str.indexOf("pears");
console.log(pos); // -1 
```

**substring(start, end)**

Extracts a part of a string and returns the extracted part in a new string. The method takes 2 parameters: the starting index, and the ending index.

```javascript
var str = "I like to eat apples.";
var newStr = str.substring(2, 6);
console.log(newStr); // "like"
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

### Boolean

A "true" or "false" value. Boolean variables are often used for conditional testing and keeping track of state.

```javascript
var n = false;
var m = true;
```

### Object

An object can be thought of as a collection of properties. These properties can be values of any type, including other objects, which enables building complex data structures. Arrays are a special type of object, more on this later.

### Null and undefined

The value of a variable with no value is undefined. Variables can be emptied by setting the value to null.

```javascript
var cars;              // value is undefined
var person = null;     // value is null
```

# Operators

# Logic

# Arrays

# Functions

# Variable scope