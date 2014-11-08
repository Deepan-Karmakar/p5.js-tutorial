#Asynchronous JS
JS is "single threaded and synchronous", meaning everything runs in order that it's written in the file. __However__, JS also makes use of "asynchronous" functions to make the program flow faster. This means the program will begin to run the function, but continue on to the next line of code without waiting for the function to complete. Loading images, external files, and URLs are generally handled by async functions. 

#AJAX

AJAX (Asynchronous JavaScript and XML) is a technique for communicating with a server and dynamically altering a page without leaving the page. It can be used to send as well as receive information in a variety of formats, including JSON, XML, HTML, and text files. It is made possible with the [XMLHttpRequest object](http://www.w3schools.com/XML/xml_http.asp), a built-in feature of your browser. 

This diagram illustrates the basic flow:

![](http://www.w3schools.com/ajax/ajax.gif)

AJAX is a bit difficult to get working in a cross platform manner but their are quite a few libraries out there that have done the hard work. Following are some examples with p5.js and jQuery, but first, a brief note about callbacks.

##Callbacks
A callback is a function that is passed to another function as a parameter, and called by that other function. A callback function is useful when working with asynchronous functions because it allows us to specify some code to execute after the first asynchronous task has completed.

We've actually already used callbacks when we used setTimeout, setInterval, and addEventListener. For example, "doSomething" below is a callback function:

```javascript
function doSomething() {
  console.log("doing something!");
}

setTimeout(doSomething, 5000);
```

You will see callbacks used in p5.js and jQuery to tell the program what to do after the external data is received.


##JSON
[JSON](http://json.org/) (JavaScript Object Notation) is a standard way to provide machine readable data to and from web services. Despite the fact that JavaScript is part of it's title, it is generally useful in all programming languages.

A JSON object is an unordered set of name/value pairs. An object begins with `{` (left brace) and ends with `}` (right brace). Each name is followed by `:` (colon) and the name/value pairs are separated by `,` (commas). The name is always a string, the value can be a string, number, boolean, array, or a nested object.
   
```json
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25,
  "address": {
    "streetAddress": "21 2nd Street",
    "city": "New York",
    "state": "NY",
    "postalCode": "10021"
  },
  "phoneNumber": [
    {
      "type": "home",
      "number": "212 555-1234"
    },
    {
      "type": "fax",
      "number": "646 555-4567"
    }
  ],
  "gender":{
    "type":"male"
  }
}
```

##XML

[XML](https://en.wikipedia.org/wiki/XML) (Extensible Markup Language) is another popular format for providing machine readable data to and from web services.

```xml
<breakfast_menu>
  <food>
    <name>Belgian Waffles</name>
    <price>$5.95</price>
    <description>
      Two of our famous Belgian Waffles with plenty of real maple syrup
    </description>
    <calories>650</calories>
  </food>
  <food>
    <name>Strawberry Belgian Waffles</name>
    <price>$7.95</price>
    <description>
      Light Belgian waffles covered with strawberries and whipped cream
    </description>
    <calories>900</calories>
  </food>
  <food>
    <name>French Toast</name>
    <price>$4.50</price>
    <description>
      Thick slices made from our homemade sourdough bread
    </description>
    <calories>600</calories>
  </food>
</breakfast_menu>
```

# AJAX with p5.js

p5.js has a variety of methods for using AJAX to retrieve files from a server. These include:
* [loadStrings](http://p5js.org/reference/#/p5/loadStrings) - loads .txt files
* [loadJSON](http://p5js.org/reference/#/p5/loadJSON) - loads .json files
* [loadXML](http://p5js.org/reference/#/p5/loadXML) - loads .xml files
* [loadTable](http://p5js.org/reference/#/p5/loadTable) - loads .csv files

###loadStrings

loadStrings loads a text file and returns an array of strings. It takes two arguments, the path to the file, and the callback function. When the server has returned the text data and it has been parsed, doText is run with the result automatically passed in as the variable "data".

```javascript
function setup() {
  createCanvas(600, 400);
  fill(0);
  noLoop();

  loadStrings("lines.txt", doText);
}

function doText(data) {
  for (var i=0; i<data.length; i++) {
    text(data[i], 5, 20*i+20);
  }
}
```

Note that if you tried to do something like the following, nothing shows up. This is because the program starts and calls loadStrings, but it moves on to doText before loadStrings completes. At the point where doText runs, the variable "data" is not yet set to anything. This is that asynchronous thing we were talking about.

```javascript
function setup() {
  createCanvas(600, 400);
  fill(0);
  noLoop();

  var data = loadStrings("lines.txt");
  doText(data); // this won't work!
}

function doText(data) {
  for (var i=0; i<data.length; i++) {
    text(data[i], 5, 20*i+20);
  }
}
```


# AJAX with jQuery

# Useful APIs
* http://openweathermap.org/API
* http://developer.nytimes.com/
* http://www.theguardian.com/open-platform
* https://www.flickr.com/services/api/
* http://web.mta.info/developers/developer-data-terms.html#data
* http://en.wikipedia.org/wiki/List_of_open_APIs
* https://gist.github.com/afeld/4952991