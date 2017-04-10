Some functionality (loading external files, for example) works as expected when the files are placed online via FTP or SSH. However, if you try to view them locally, you see some kind of "cross-origin" errors in console. The solution to this is to view them using what's called a local web server. This tutorial includes instructions for setting up several types of local web servers on each of Mac OSX, Windows, and Linux.

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

An alternative is node.js http-server. It is much faster than python simple server while requiring a little bit of setup. Just 3 simple steps:

1.  [Download and Install node.js](https://nodejs.org/en/download/)
2.  Open a terminal or command prompt 
3.  On OSX/Linux type

        sudo npm install -g http-server

    On Windows type (you might need to open the command prompt as admin)

        npm install -g http-server
 
Done!

From then on just `cd` to the folder that has the files you want to serve and type 

    http-server

Then point your browser at `http://localhost:8080/`

Note: If you are having problems where the browser does not reload your javascript files after changes are made, you may need to instantiate the server with a specific cache value. To do this, include the cache timeout flag, with a value of '-1'. This tells the browser not to cache files (like sketch.js).

```bash
http-server -c-1
```

## Processing Simple HTTPServer (3rd option) 
Simple HTTPServer library for processing. Allows communication in both ways.
```
import http.*;

SimpleHTTPServer server;

void setup() {
  // Create a server listening on port 8000
  // serving index.html,which is in the data folder
  server = new SimpleHTTPServer(this); 
}
```

[Library page of Processing simple HTTP server](https://transfluxus.github.io/SimpleHTTPServer/)


## Apache Server (4th option) 

Python SimpleHTTPServer is great to get started, but at some point you might want to set up an Apache server. The Apache server supports a greater range of HTTP functionality and scales well for bigger projects. See below for OS specific setup.

### Mac OS X

Mac OS X since 10.5 Leopard ships with Apache web server installed, all you have to do is enable it and place the files in the right place.

#### Mac OS X 10.7 and above

1. Open Terminal and type:
```
sudo apachectl start
```
2. Verify it is working by going to `http://localhost` on your browser. You should see "It works!" on the browser.
3. Enable permissions for the files on the server by typing the following two commands into Terminal:
```
sudo chown root:<your username> -R /Library/WebServer/Documents

sudo chmod -R 755 /Library/WebServer/Documents
```
4. Place your project somewhere inside /Library/WebServer/Documents/.
5. View it at http://localhost/(the project folder in /Library/WebServer/Documents).
```
http://localhost/my-p5-sketch
```

#### Mac OS X 10.5 and 10.6

1. Turn on the web server. Go into Sys­tem Pref­er­ences > Shar­ing, and check the “Web Shar­ing” box.
2. Verify it is working by going to `http://localhost/~<your username>` on your browser. You should see a default webpage with a title of "Your Website".
3. Place your project somewhere inside `<your username folder>/Sites`.
4. View it at http://localhost/~(your username)/(the project folder in `<your username folder>/Sites`).
```
http://localhost/~macusername/my-p5-sketch
```

### Windows

1. Download WampServer from [http://www.wampserver.com/en/](http://www.wampserver.com/en/).
2. Install WampServer and follow instructions.
3. The “www” directory will be automatically created (usually c:\wamp\www).
4. Create a subdirectory in “www” and put your HTML/JS files inside.
5. Open your internet browser and go to the URL : http://localhost/yourfile.html.


### Linux

1. Install apache2 via apt-get.
2. Place your project somewhere inside /var/www/.
3. View it at http://localhost.