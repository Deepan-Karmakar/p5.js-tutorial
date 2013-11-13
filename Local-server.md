Some functionality (loading external files, for example) works as expected when the files are placed online via FTP. However, if you try to view them locally, you see some kind of "cross-origin" errors in console. The solution to this is to view them using what's called a local web server. This tutorial includes instructions for setting this up on Mac OSX and Windows.

###Mac OS X

####Snow Leopard (10.6)

Snow Leopard has a built in web server, all you have to do is enable it and place the files in the right place.

1. Go into Sys­tem Pref­er­ences > Shar­ing, and check the “Web Shar­ing” box.
2. Place your project somewhere inside /Library/WebServer/Documents/.
3. View it at http://localhost.

There's some further info here http://georgebutler.com/blog/setting-up-local-web-server-on-os-x-snow-leopard-10-6/.


####Lion (10.7) and Mountain Lion (10.8)

In Lion and Mountain Lion the enable web server option has been removed, but you can set it up manually.

1. Open terminal.
2. Create the place your server will look for your files, type:
```
mkdir ~/Sites
```

3. Type:
```
cd /etc/apache2/users
ls
```
4. Check whether you have a file like ```<your short user name>.conf```. If that file doesn't exist, you will need to create it with:
```
sudo vi /etc/apache2/users/<your short user name>.conf
```
5. Copy and past the following into the window:
```
<Directory "/Users/<your short user name>/Sites/">
    Options Indexes MultiViews
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>
```
Then press ```<esc>``` and then type ```ZZ``` to save and quit.
6. Finally, turn on the server! For Mountain Lion, go into Sys­tem Pref­er­ences > Shar­ing, and check the “Web Shar­ing” box.
For Lion, type: 
```
sudo launchctl load -w /System/Library/LaunchDaemons/org.apache.httpd.plist
``` 
7. Place your project somewhere inside /Sites/.
8. Finally, view it at http://localhost/~username/!

There's some further info here https://discussions.apple.com/docs/DOC-3083.


###Windows

1. Download WampServer from [http://www.wampserver.com/en/](http://www.wampserver.com/en/).
2. Install WampServer and follow instructions.
3. The “www” directory will be automatically created (usually c:\wamp\www).
4. Create a subdirectory in “www” and put your HTML/JS files inside.
5. Open your internet browser and go to the URL : http://localhost/yourfile.html.