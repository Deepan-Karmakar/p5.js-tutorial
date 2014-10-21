JavaScript is a scripting language that is typically used on web pages where it runs client-side (within the web browser). It is a general purpose language with a lot of built-in functionality for interacting with elements on a webpage and responding to actions initiated by the user.

Although the JavaScript has "Java" in it's name, it isn't related other than by the fact that it looks something like Java. JavaScript's official name is ECMAScript (ECMA is the European Computer Manufacturers Association, a standards body). It was initially created by Netscape Communications. ([Wikipedia: JavaScript](http://en.wikipedia.org/wiki/JavaScript))


##The `<script>` tag

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

##Comments

Comments in JavaScript are similar to comments in Java or C:
```javascript         
  // Single Line Comment   
```
```javascript     
  /* 
    Multiple
    Line
    Comment
  */
```