#Asynchronous JS
JS is "single threaded and synchronous", meaning everything runs in order that it's written in the file. __However__, JS also makes use of "asynchronous" functions to make the program flow faster. This means the program will begin to run the function, but continue on to the next line of code without waiting for the function to complete. Loading images, external files, and URLs are generally handled by async functions. 

#AJAX

AJAX (Asynchronous JavaScript and XML) is a technique for communicating with a server and dynamically altering a page without leaving the page. It can be used to send as well as receive information in a variety of formats, including JSON, XML, HTML, and text files. It is made possible with the [XMLHttpRequest object](http://www.w3schools.com/XML/xml_http.asp), a built-in feature of your browser. 

This diagram illustrates the basic flow:

![](http://www.w3schools.com/ajax/ajax.gif)

AJAX is a bit difficult to get working in a cross platform manner (see an example [here](http://stackoverflow.com/questions/9713058/sending-post-data-with-a-xmlhttprequest)) but there are quite a few libraries out there that have done the hard work. Following are some examples with p5.js and jQuery, but first, a brief note about callbacks.

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


If this were JSON data we loaded into a Javascript application, it would be stored in a variable, like this:

```javascript
var mydata = {
  "firstName": "John",
  "lastName": "Smith",
  "age": 25,
  "address": {
    "streetAddress": "21 2nd Street",
    "city": "New York",
    "state": "NY",
    "postalCode": "10021"
  }
  ...
};
```
Now you can access it with the variable `mydata`: 

```javascript
alert('I am at' + mydata.address.streetAddress);
```

##XML

[XML](https://en.wikipedia.org/wiki/XML) (Extensible Markup Language) is another popular format for providing machine readable data to and from web services. XML is made up of tags, similar to HTML, but unlike HTML, there are no predefined tags (like h1, p, html, etc), instead you make up your own.

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

  var data = loadStrings("lines.txt");
  doText(data); // this won't work!
}

function doText(data) {
  for (var i=0; i<data.length; i++) {
    text(data[i], 5, 20*i+20);
  }
}
```


###loadJSON

loadJSON loads a JSON file and returns a JavaScript object. It takes two arguments, the path to the file, and the callback function. When the server has returned the JSON data and it has been parsed, drawData is run with the result automatically passed in as the variable "data".

JSON file:
```json
{ "person1" : {
    "name": "Morgan",
    "age": "30",
    "location": "Boston",
    "desire": "Singing",
    "fear": "Violence"
  },
  "person2": {
    "name": "Joss",
    "age": "42",
    "location": "Boston",
    "desire": "Hiking",
    "fear": "Irrationality"
  }
}
```

JS file:
```javascript

function setup() {
  createCanvas(600, 400);
  noStroke();
  textSize(20);
  loadJSON("data.json", drawData);
}

function drawData(data) {
  // person 1 bubble
  fill(155, 30, 180, 180);
  ellipse(250, 200, data.person1.age * 5, data.person1.age * 5); // person1.age = 30
  fill(255);
  text(data.person1.name, 210, 200); // person1.name = Morgan

  // person 2 bubble
  fill(180, 180, 34, 180);
  ellipse(350, 200, data.person2.age * 5, data.person2.age * 5); // person2.age = 32
  fill(255);
  text(data.person2.name, 330, 200); // person2.name = Joss
}
```

In addition to local files, loadJSON can also load external URLs. Unfortunately, there are quite a few security restrictions on making AJAX requests across domains. If you are interested in investigating those and how to overcome them, checkout this: http://www.html5rocks.com/en/tutorials/cors/. Fortunately, since we are using libraries such as p5.js we don't have to worry so much.

[openweathermap.org](http://openweathermap.org/) has a pretty easy to use API for weather data in cities around the world. Note that you will need to sign up [here](openweathermap.org/appid) for an API key and add it where it says "YOUR_API_KEY".

It's a good idea to try just putting the url string directly into your browser address bar first to make sure it returns data. If you see JSON data appear there, then try adding it into your p5.js sketch.

```javascript
var bubbles = [];

function setup() {
  createCanvas(600, 400);
  noStroke();
  var url = 'http://api.openweathermap.org/data/2.5/weather?APPID=YOUR_API_KEY&q=NewYork,USA'
  loadJSON(url, drawWeather); 
}

function drawWeather(weather) {

  // Get the loaded JSON data
  console.log(weather); // inspect the weather JSON
  var humidity = weather.main.humidity; // get the main.humidity out of the loaded JSON
  console.log(humidity); // inspect the humidity in the console

  background(40, 90, 200);
  fill(0, 255, 255, humidity); // use the humidity value to set the alpha
  for (var i = 0; i < 50; i++) {
    ellipse(random(width), random(height), 30, 30);
  }
}
```

###loadXML

loadXML loads an XML file and returns an XML object. It takes two arguments, the path to the file, and the callback function. It's a little messier to work with XML objects, but you can learn about how to do that [here](http://www.w3schools.com/xml/dom_intro.asp).

###preload

If you'd prefer not to deal with asynchronous callbacks, p5.js also has a function called "preload" that lets you load external files synchronously before setup is run. If a preload function is defined, setup will wait until any load calls within have finished. This allows you to access the file data in setup and draw without needing a callback. Nothing besides load calls should be inside preload (loadImage, loadJSON, loadStrings, loadXML, etc).

```javascript
var lines;

function preload() {
  lines = loadStrings("lines.txt");
}

function setup() {
  createCanvas(600, 400);
  textSize(20);
  fill(0);
  noLoop();
}

function draw() {
  for (var i=0; i<lines.length; i++) {
    text(lines[i], 5, 20*i+20);
  }
}
```

# AJAX with jQuery

Rather that p5.js, you can also use [jQuery](http://jquery.com/) to help with loading external files. jQuery is a JS library that helps with handling DOM manipulation, events, animation, and AJAX. In order to use the jquery library, you will need to include a link to it in the head of your html file.

```javascript
<script src="//code.jquery.com/jquery-1.11.1.min.js"></script>
```

```javascript
$(document).ready(function(){

  $.ajax({
    url: "lines.txt", // path to file
    dataType: 'text', // type of file (text, json, xml, etc)
    success: function(data) { // callback for successful completion
      $("#sentences").html(data);
    },
    error: function() { // callback if there's an error
      alert("error");
    }
  });     
   
});
```

```javascript
$(document).ready(function(){
  $.ajax({
    url: "http://api.openweathermap.org/data/2.5/weather?APPID=YOUR_API_KEY&id=5128581&units=imperial",
    dataType: 'json',
    success: function(data) {
      alert("Temperature is: " + data.main.temp );
    },
    error: function() {
      alert("error");
    }
  });        
});
```

# Useful APIs
* OpenWeatherMap - http://openweathermap.org/API
* NYTimes - http://developer.nytimes.com/
* The Guardian - http://www.theguardian.com/open-platform
* flickr - https://www.flickr.com/services/api/
* MTA - http://web.mta.info/developers/developer-data-terms.html#data
* Foursquare - https://developer.foursquare.com/
* Sunlight Foundation - http://sunlightfoundation.com/api/
* http://en.wikipedia.org/wiki/List_of_open_APIs
* https://gist.github.com/afeld/4952991