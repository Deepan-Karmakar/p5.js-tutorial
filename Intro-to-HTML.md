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

When rendered in the browser, the line above will produce text that looks like this:
<p>This is a paragraph with <em>some italicized text</em> in it.</p>
