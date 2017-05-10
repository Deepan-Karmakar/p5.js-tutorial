List of the very few things that get done when posting a new p5 release...

### Posting a new release
1. Increment version number in package.json.
2. Run `grunt` to build latest lib files with new tag and date.
0. Increment version number in p5.dom.js if changes made.
3. Push changes to github.
4. Draft a new release.
  * Give it version number as name.
  * Include list of changes since last release.
  * Include these files:
    * p5.js
    * p5.min.js
    * p5.dom.js
    * p5.sound.js
    * p5.sound.min.js
    * p5.zip (`zip -r p5-zip.zip p5-zip -x '*/.DS_Store'`) all above files + empty-example containing:
      * sketch.js
      * index.html
        ```html
<html><!DOCTYPE html>
<html>
  <head>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.5.9/p5.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.5.9/addons/p5.dom.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.5.9/addons/p5.sound.min.js"></script>
    <script src="sketch.js"></script>
    <link rel="stylesheet" type="text/css" href="style.css">
  <style> body {padding: 0; margin: 0;} </style>
  </head>
  <body>
  </body>
</html>
```

![](http://i.imgur.com/nLMqqOT.png?1)

### Post other versions
1. Run `npm publish` from p5.js repo to publish to http://npmjs.com.
2. Replace files in lib/ directory in [p5.js-release repo](https://github.com/lmccart/p5.js-release) (to support bower etc.
  ```
  git add lib/*
  git commit -m 'vx.x.x'
  git push origin master
  git tag x.x.x
  git push origin x.x.x
  ```

3. Links on website should auto-update to the latest version in package.json, but you can also refresh this by going here: http://p5js.org/download/release.php.

### Updating docs
1. Run `grunt yui`.
2. Move `docs/reference` to `p5.js-website/reference`.
3. Push changes to github to auto-update site.
