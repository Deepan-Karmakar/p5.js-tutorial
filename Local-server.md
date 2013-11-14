Some functionality (loading external files, for example) works as expected when the files are placed online via FTP. However, if you try to view them locally, you see some kind of "cross-origin" errors in console. The solution to this is to view them using what's called a local web server. This tutorial includes instructions for setting this up on Mac OSX and Windows.

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
