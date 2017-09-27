Algunas funciones (como cargar archivos externos, por ejemplo) funcionan según lo esperado cuando los archivos son ubicados en línea a través de FTP o SSH. Sin embargo, si estás tratando de revisarlos localmente, verás algún error del tipo "cross-origin" (origen cruzado) en la consola. La solución a esto es usar lo que se conoce como un servidor web local. Este tutorial incluye instrucciones para configurar distintos tipos de servidores web locales en Mac OSX, Windows y Linux.

## Python SimpleHTTPServer (Primera opción)

Si necesitas ejecutar rápidamente un servidor web y no quieres molestarte en configurar apache o algo similar, Python te puede ayudar. Python incluye un servidor HTTP simple. Con la ayuda de este pequeño servidor HTTP puedes transformar cualquier directorio en tu sistema en un directorio de un servidor web. Lo único que necesitas es tener instalado [Python](https://www.python.org/downloads/) (Python ya viene instalado en Mac OS X).

[Tutorial de Python SimpleHTTPServer](https://github.com/lmccart/itp-creative-js/wiki/SimpleHTTPServer)

Escribe en Terminal:
```
python -m SimpleHTTPServer
```

O  escribe esto si estás usando Python 3:
```
python -m http.server
```

A continuación visita `http://localhost:8000` en tu navegador.

Desafortunadamente el servidor simple de Python es muy lento. Cargar una página local a menudo no funcionará y no podrá transmitir video y tendrá problemas con archivos medianos como un mp3 de 8MB, por ejemplo. Sin embargo, será suficiente para cargar la mayoría de los textos, tipografías e imágenes.

## Node http-server (Segunda opción) 

Una alternativa es http-server de node.js. Es mucho más rápido que el servidor simple de Python y requiere un poco de configuración. Solamente 3 simples pasos:

1.  [Descarga e instala node.js](https://nodejs.org/en/download/)
2.  Abre una sesión de terminal 
3.  En OSX/Linux escribe

        sudo npm install -g http-server

    En Windows escribe (quizás necesites abrir la terminal como admin)

        npm install -g http-server
 
¡Listo!

De ahora en adelante basta con hacer `cd` al directorio que tiene los archivos que quieres poner en tu servidor y luego escribir

    http-server

Luego dirige tu navegador a `http://localhost:8080/`

Nota: If you are having problems where the browser does not reload your javascript files after changes are made, you may need to instantiate the server with a specific cache value. To do this, include the cache timeout flag, with a value of '-1'. This tells the browser not to cache files (like sketch.js).

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

## Using PHP built-in web server (5th option)

[PHP has (since version 5.4.0) a built-in web server](https://secure.php.net/manual/en/features.commandline.webserver.php) for testing purposes that can be used to test P5.js sketches. 

To check if you have PHP installed you can open a terminal and issue the command:

```
php -version
```

If you have PHP CLI (Command Line Interpreter) installed you can start a local development server by usingd the command:

```
php -S localhost:8000
```
Then point your browser at `http://localhost:8000/`