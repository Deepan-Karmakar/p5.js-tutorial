1. Increment version number in package.json.
2. Run `grunt` to build latest lib files with new tag and date.
3. Push changes to github.
4. Create new release. (click releases > draft a new release)
  * Give it version number as name.
  * Include list of changes since last release.
  * Include these files:
    * p5.js
    * p5.min.js
    * p5.dom.js
    * p5.sound.js
    * p5.sound.min.js
    * p5.zip containing:
      * all above files
      * empty-example containing:
        * libraries/p5.js
        * libraries/p5.dom.js
        * libraries/p5.sound.js
        * index.html
      


1. Run `grunt yui`.
2. Move `docs/reference` to `p5.js-website/reference`.
3. Push changes to github to auto-update site.


p5js.org/download/release.php