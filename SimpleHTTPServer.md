# Terminal

To run SimpleHTTPServer, you are first going to want to become familiar using the Mac OS X terminal.  The terminal provides "shell" access to your computer.  You can browse directories and execute applications via text-based commands.  You can find the Terminal app in Applications->Utilities->Terminal.   Run it and you'll see something like.

![Terminal](images/terminal.png)

The blinking cursor is the "prompt", where you can execute a command.  Here is a list of some common commands you'll need.

* `cd` - change directory.  The following, for example, will set the current path to your desktop.  You'll want to replace "shiffman" with your username.  `cd /Users/shiffman/Desktop`.
* `pwd` - print working directory.  This will print out the current directory.
* `ls` - list the contents of the current directory.

This is barely scratching the surface of [what you can do with unix commands](http://mally.stanford.edu/~sr/computing/basic-unix.html).  Allison Parrish's class also has [a tutorial about using unix commands to manipulate text data](http://www.decontextualize.com/teaching/rwet/introduction-and-unix-tutorial/).  But we'll stop here, after all, we're just here to run a simple web server.  

# Running SimpleHTTPServer

Your job is to get terminal to point to the directory on your computer where you are storing your p5.js work.  On my computer I've got a ton of examples in a directory called "The-Nature-of-Code-Examples-p5.js".  So I'm going to browse to it by doing the following.

```
$ cd /Users/shiffman/Documents/noc/The-Nature-of-Code-Examples-p5.js
```

(You don't need to type the '$' I'm just using it to represent a prompt.)

Once I'm there, I can start up a web server with the following command.

```
$ python -m SimpleHTTPServer
```

I should then see:

```
Serving HTTP on 0.0.0.0 port 8000 ...
```

This means the server is up and running at [localhost](http://en.wikipedia.org/wiki/Localhost) on port 8000.  And this means I can type `http://localhost:8000/` into the address of a web browser and I'll see:

![localhost](images/localhost.png)

# A couple more terminal tips

* If you don't feel like typing a long path to a directory on your computer, you can get to it quickly by dragging a folder from the finder into terminal.  It'll magically transform into the path!
* You can also "auto-complete" directories and filenames using `TAB`.
* You can repeat previous commands by using the up and down arrow keys.




(Tutorial via Dan Shiffman.)

