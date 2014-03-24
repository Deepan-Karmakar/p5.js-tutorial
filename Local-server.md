Some functionality (loading external files, for example) works as expected when the files are placed online via FTP. However, if you try to view them locally, you see some kind of "cross-origin" errors in console. The solution to this is to view them using what's called a local web server. This tutorial includes instructions for setting this up on Mac OSX, Windows, and Linux.

##Python SimpleHTTPServer

If you need a quick web server running and you don't want to mess with setting up apache or something similar, then Python can help. Python comes with a simple builtin HTTP server. With the help of this little HTTP server you can turn any directory in your system into your web server directory. The only thing you need to have installed is Python.

[Python SimpleHTTPServer tutorial](http://www.pythonforbeginners.com/modules-in-python/how-to-use-simplehttpserver)

##Apache Server

Python SimpleHTTPServer is great to get started, but at some point you might want to set up an Apache server. The Apache server supports a greater range of HTTP functionality and scales well for bigger projects. See below for OS specific setup.

###Mac OS X

Snow Leopard has a built in web server, all you have to do is enable it and place the files in the right place.

1. Turn on the web server. In Snow Leopard, go into Sys­tem Pref­er­ences > Shar­ing, and check the “Web Shar­ing” box. In Lion, Mountain Lion, or Maverick, open Terminal and type:
```
sudo apachectl start
```
2. Enable permissions, type:
```
sudo chown root:<your username> -R /Library/WebServer/Documents

sudo chmod 755 -R /Library/WebServer/Documents
```
3. Place your project somewhere inside /Library/WebServer/Documents/.
4. View it at http://localhost.


###Windows

1. Download WampServer from [http://www.wampserver.com/en/](http://www.wampserver.com/en/).
2. Install WampServer and follow instructions.
3. The “www” directory will be automatically created (usually c:\wamp\www).
4. Create a subdirectory in “www” and put your HTML/JS files inside.
5. Open your internet browser and go to the URL : http://localhost/yourfile.html.


###Linux

1. Install apache2 via apt-get.
2. Place your project somewhere inside /var/www/.
3. View it at http://localhost.
