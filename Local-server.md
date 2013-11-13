Some functionality (loading external files, for example) works as expected when the files are placed online via FTP. However, if you try to view them locally, you see some kind of "cross-origin" errors in console. The solution to this is to view them using what's called a local web server. This tutorial includes instructions for setting this up on Mac OSX and Windows.

###Mac OSX

####Snow Leopard (10.6)

Snow Leopard has a built in web server, all you have to do is enable it and place the files in the right place.

1. Go into Sys­tem Pref­er­ences > Shar­ing, and check the “Web Shar­ing” box.
2. Place your project somewhere inside /Library/WebServer/Documents/.
3. View it at http://localhost.

There's some further info here http://georgebutler.com/blog/setting-up-local-web-server-on-os-x-snow-leopard-10-6/.


####Lion (10.7)

Lion has a built in web server, all you have to do is enable it and place the files in the right place.

1. Go into Sys­tem Pref­er­ences > Shar­ing, and check the “Web Shar­ing” box.
2. Place your project somewhere inside /Sites/.
3. View it at http://localhost/~username/.

There's some further info here https://discussions.apple.com/docs/DOC-3083.


####Mountain Lion (10.8)

In Mountain Lion the enable web server option has been removed, but you can set it up manually.

1. Open terminal.
2. Type ```sudo launchctl load -w /System/Library/LaunchDaemons/org.apache.httpd.plist```. This turns on the server.
2. Type ```mkdir ~/Sites```. This creates the place your server will look for your files.
3. Navigate to the Sites folder and place your project somewhere inside it.
3. View it at http://localhost/~username/.

There's some further info here https://discussions.apple.com/docs/DOC-3083.