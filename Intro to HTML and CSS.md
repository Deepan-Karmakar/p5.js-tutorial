#HTML

HTML is a markup language. It tells the web browser how to structure and display content. Every HTML file is just a text document. If you open it in a text editor you see words and markup, but if you open it in your browser you see formatted text with no markup symbols.


##Tags

HTML uses a pre-defined set of elements to different types of content. Elements are enclosed by opening and closing tags (with a few exceptions). Tags are short pieces of text indicating the type of content enclosed, surrounded by angle brackets (<>). The closing tag looks just like the opening tag except it has a forward slash (/) after the first angle bracket.

For example, the line below contains a block of text surrounded by paragraph (p) tags, meant to tell the browser that the line should be interpreted as a paragraph.

```html
<p>This is a paragraph.</p>
```

Elements can also contain other elements within them. The tag `<em>` indicates that the content enclosed within should be italicized.

```html
<p>This is a paragraph with <em>italicized text</em> in it.</p>
```

When rendered (opened) in the browser, the line above will look like this:
<p>This is a paragraph with <em>some italicized text</em> in it.</p>

##An HTML page

Elements contain other elements to create a hierarchal structure. This is how an html page is built. The chunk below represents a simple but complete html page.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>The page title</title>
  </head>

  <body>
    <p>This is a basic page with a paragraph in it.</p>
  </body>
</html>
```

The first line tells the browser that it should interpret the text as HTML5.

All of the rest of the content on the page is surrounded by one set of <html> tags. Within this, there are two sections - the head and the body. 

The head contains metadata about the page that does not show up on the page itself, for example, the title (as shown above). This section might also include links to other files that are incorporated in the page (more on this later). 

The body section is where all the content that shows up on the page goes, like the paragraph element we see above.

The hierarchical, nested structure of HTML is sometimes referred to as the Document Object Model, or DOM. You can think of the page (DOM) as a tree with parents and children — think of a family tree. Being able to access elements of the tree comes into play when we want to manipulate the HTML with CSS or JavaScript.

##Other common tags

You can see all the possible tags in the [mdn element reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element), or see below for some of the most common ones.

* `<html>...</html>` start and end HTML
* `<head>...</head>` head of page, not actual content
* `<title>...</title>` title of page
* `<body>...</body>` body of page, where the content goes
* `<div>...</div>` content section
* `<p>...</p>` paragraph
* `<b>...</b>` bold
* `<em>...</em>` italic
* `<!-- ... -->` comments


####Headings `<h1>`, `<h2>`

`<h1>...</h1>` (also h2, h3, h4, etc..) are used for various headings, in decreasing size. If you think of your page like an outline, h1 could be used for the top level section headings, h2 for the secondary headings, etc. 

####Line breaks `<br>`

Your browser ignores line breaks in your html. So these two blocks would render the same:

```html
<p>This is a paragraph with no line breaks.</p>
```

```html
<p>This is a
paragraph
with no line
breaks.</p>
```

However, you can specify line breaks by using the `<br>` tag. Note that you do not need a closing tag for the line break tag, since there is no content in between. 

```html
<p>This is a<br>
paragraph<br>
with line<br>
breaks.</p>
```
Renders like this:

<p>This is a<br>
paragraph<br>
with line<br>
breaks.</p>


####Links `<a>`

The a tag indicates a link. It also has some extra information between the a and the > character, letting you designate the destination of the link. This extra href field is known as an attribute.

```html
Click on <a href="http://p5js.org">this text</a>.
```
The line above renders as:

Click on <a href="http://p5js.org">this text</a>.

####Images `<img>`

The img tag adds an image to the page. It also contains an attribute to specify the source of the image to display. The img element does not contain any text content or any other elements. Since it is an empty element, it doesn't need a closing tag. Instead, the forward slash from the closing tag is stuck just inside of the > character at the end of the opening tag.

```html
<img src="bubbles.jpg" />
```

The source can be relative to the html file you are working with (above), or it can be a full url (below). In the example above, the bubbles.jpg file would need to be located in the same directory as the html file.

```html
<img src="https://raw.githubusercontent.com/lmccart/p5.js/master/examples/p5.Image/unicorn.jpg" />
```

##Attributes

Attributes provide extra information necessary to a tag to work properly (such as the src attribute on the `<img>` tag or the href attribute on the `<a>` tag) or just provide some optional information. An attribute generally consists of an attribute name and an attribute value (usually surrounded by quotes), with an = sign between them.

You can see all the attributes and the tags they are associated with in the [mdn attribute reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes)

#CSS

Cascading Style Sheets, or CSS, is used to tell web browsers how to style and display HTML-structured text. While HTML defines the content, CSS supplies the presentation. Separating the content from the style makes the code easier to read and also allows us to more easily swap out one style for another.

You can set style properties inline using the style attribute. Inside the quotes, you place one or more property:value pairs, separated by semicolons.
```html
<p style="width:400px; background:#FF0000; font-size: 18px;">This is some text.</p>
```

You can find all css style attributes in this [CSS reference](https://developer.mozilla.org/en-US/docs/Web/CSS). This is just the most basic way of adding CSS styling. Another alternative is to separate out the CSS into it's own file, getting us closer to the separate content and style goal mentioned above (more on this later!).


#Reference
  * [Mozilla HTML guide](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML)
  * [HTML tag cheatsheet](http://www.simplehtmlguide.com/cheatsheet.php)
  * [HTML tag reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)
  * [Mozilla CSS guide](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Getting_started)
  * [CSS reference](https://developer.mozilla.org/en-US/docs/Web/CSS)
  * [Lynda.com HTML essentials](http://www.lynda.com/HTML-tutorials/HTML-Essential-Training/170427-2.html)
  * [Lynda.com CSS fundamentals](http://www.lynda.com/Web-Interactive-CSS-tutorials/CSS-Fundamentals/80436-2.html)