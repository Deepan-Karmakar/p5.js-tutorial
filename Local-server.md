Some functionality (loading external files, for example) works as expected when the files are placed online via FTP or SSH. However, if you try to view them locally, you see some kind of "cross-origin" errors in console. The solution to this is to view them using what's called a local web server. This tutorial includes instructions for setting up several types of local web servers on each of Mac OSX, Windows, and Linux. This tutorial assumes a basic understanding of the command line interface, for a quick introduction see the [command line introduction wiki](https://github.com/processing/p5.js/wiki/Terminal-and-the-Command-Line).

## Python SimpleHTTPServer (1st option)

If you need a quick web server running and you don't want to mess with setting up apache or something similar, then Python can help. Python comes with a simple builtin HTTP server. With the help of this little HTTP server you can turn any directory in your system into your web server directory. The only thing you need to have installed is [Python](https://www.python.org/downloads/) (Python is already installed if you are using Mac OS X).

[Python SimpleHTTPServer tutorial](https://github.com/lmccart/itp-creative-js/wiki/SimpleHTTPServer)

Type in Terminal:
```
python -m SimpleHTTPServer
```

Or if you are using Python 3, type:
```
python -m http.server
```

Then visit `http://localhost:8000` on your browser.

Unfortunately the python simple server is very slow. Loading a local page will often stall and it can't stream video and has trouble with even medium size files like an 8MB mp3 for example. However, it should suffice for loading in most text files, fonts and most images.

## Node http-server (2nd option) 

An alternative is node.js `http-server`. It is much faster than python simple server while requiring a little bit of setup. Just 3 simple steps:

1.  [Download and Install node.js](https://nodejs.org/en/download/)
2.  Open a terminal or command prompt (on Windows you might need to open the command prompt as admin)
3.  In the terminal type:

        npm install -g http-server

Done!

From then on just `cd` to the folder that has the files you want to serve and type 

    http-server

Then point your browser at `http://localhost:8080/`

Note 1: If you are having problems where the browser does not reload your javascript files after changes are made, you may need to instantiate the server with a specific cache value. To do this, include the cache timeout flag, with a value of '-1'. This tells the browser not to cache files (like sketch.js).

```bash
http-server -c-1
```


Alternatively, you can setup a `browser-sync` server which has the added benefit of automatically reloading the webpage when any changes were saved in the source code.

1. Follow instructions above to install node.js and open a Terminal/Command Prompt window
1. Type 

        npm install -g browser-sync

3. `cd` into your project folder.
2. Type

        browser-sync start --server -f -w

5. Your website should be available at `http://localhost:3000` and whenever you save a file in your project, the webpage will automatically reload.
- [https://www.browsersync.io/#install](https://www.browsersync.io/#install)  
- [https://github.com/CodingTrain/Rainbow-Topics/issues/646](https://github.com/CodingTrain/Rainbow-Topics/issues/646)

Note 2: If you encountered an error that says `EACCES` when installing either `http-server` or `browser-sync` it means npm is not installed with the right permissions, follow the steps outlined at https://docs.npmjs.com/getting-started/fixing-npm-permissions to fix it.

## Using PHP built-in web server (3rd option)

[PHP has (since version 5.4.0) a built-in web server](https://secure.php.net/manual/en/features.commandline.webserver.php) for testing purposes that can be used to test P5.js sketches. 

To check if you have PHP installed you can open a terminal and issue the command:

```
php -version
```

If you have PHP CLI (Command Line Interpreter) installed you can start a local development server by using the command:

```
php -S localhost:8000
```
Then point your browser at `http://localhost:8000/`

