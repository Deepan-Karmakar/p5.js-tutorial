Some functionality (loading external files, for example) works as expected when the files are placed online via FTP. However, if you try to view them locally, you see some kind of "cross-origin" errors in console. The solution to this is to view them using what's called a local web server. This tutorial includes instructions for setting this up on Mac OSX and Windows.

###Mac OSX

####Snow Leopard (10.6)

Snow Leopard has a built in web server, all you have to do is enable it and place the files in the right place.
1. Go into Sys­tem Pref­er­ences > Shar­ing, and check the “Web Shar­ing” box.
2. Place your project somewhere inside /Library/WebServer/Documents/.
3. View it at http://localhost.