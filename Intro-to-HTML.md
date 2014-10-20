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

Elements contain other elements to create a hierarchal structure. This is how an html page is built. The chunk below represents a very simple but complete html page.

```html
<html>
  <head>
    <title>The page title</title>
  </head>

  <body>
    <p>This is a basic page with a paragraph in it.</p>
  </body>
</html>
```

All of the content on the page is surrounded by one set of <html> tags. Within this, there are two sections - the head and the body. The head contains metadata about the page that does not show up on the page itself, for example, the title (as shown above). This section might also include links to other files that are incorporated in the page (more on this later). The body section is where all the content that shows up on the page goes, like the paragraph element we see above.

The hierarchical, nested structure of HTML is sometimes referred to as the Document Object Model, or DOM. You can think of the page (DOM) as a tree with parents and children — think of a family tree. Being able to access elements of the tree comes into play when we want to manipulate the HTML with CSS or JavaScript.