#CSS

Cascading Style Sheets, or CSS, is used to tell web browsers how to style and display HTML-structured text. While HTML defines the content, CSS supplies the presentation. Separating the content from the style makes the code easier to read and also allows us to more easily swap out one style for another.

You can set style properties inline using the style attribute. Inside the quotes, you place one or more property:value pairs, separated by semicolons.
```html
<p style="width:400px; background:#FF0000; font-size: 18px;">This is some text.</p>
```

You can find all css style attributes in this [CSS reference](https://developer.mozilla.org/en-US/docs/Web/CSS). This is just the most basic way of adding CSS styling. Another alternative is to separate out the CSS into it's own file, getting us closer to the separate content and style goal mentioned above (more on this later!).