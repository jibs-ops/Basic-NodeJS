# Basic-NodeJS Program on Linux


## Steps to install the NodeJS Runtime Environment.

* The exercises were done with the Desktop Version of Ubuntu 20.04  

1. Start a new terminal session (Ctrl + Alt + T)
2. Create a new directory as Projects and head into that directory: 
    - mkdir Projects
    - cd Projects

3. Run this command: 
    - sudo apt install -y nodejs
  
    - Interpretation of this command:
      - sudo - Execute this command with root privileges (You may be prompted to enter your password if your executing the command other than the root user).
      - apt - Get the application from the repository. 
      - install -y = Installing the application and -y as yes for the application to get installed.
      - nodejs - The name of the application that is to get installed “nodejs”.

4. Check the version of the installed nodejs framework:

    - nodejs -v

5. For installing all the required modules and packages for nodejs, the package manager called npm has to be used. npm is a package manager for the JavaScript programming language and also the default package manager for the JavaScript runtime environment Node.js. Use the below command. Syntax’s are similar to the section where the “interpretation of the command” was described.

    - sudo apt install -y npm
    - sudo npm install npm -global

6. Check the version of the installed npm framework
    - npm -v


## Using NodeJS

* A simple application and a web server is described in this section

1. Run the following commands to create a directory called nodejsapp, which is to keep the code and files organized. Move to the newly created directory and open an editor such as nano or vim (The author is using nano). Create a JavaScript file called as “firstapp.js”.

    - mkdir nodejsapp
    - cd nodejsapp
    - node firstapp.js

2. Type the following code to print out the output in the command line console and execute the code in the file. 
    
    - console.log (‘First NodeJS Application’): - ctrl+o to save and ctrl+x to exit.
    - nodejs firstapp.js
    - chmod +x firstapp.js – if there is any problem in executing it, use the +x for execution permission.


## Creating a local webserver

1. Create a new file in the nano editor named as server.js
    - nano server.js

2. Add the following lines to create a server connection on port number 6060. The output of the below code would be that NodeJS would listen to the server connection at localhost:6060. If the connection gets established successfully then the code 200 will be generated and ‘NodeJS App’ will be shown as a text output. Save the file afterwards.

```javascript

var http = require('http');

var server = http.createServer(function(request response) {
resquest.writeHead(200,{'Content-Type': 'text/plain'});
response.end('NodeJS App');
});
server.listen(6060);
console.log('Server is running at http://localhost:6060/') 

```

3. Execute the command for the web server to startup and start working. If everything is been running properly a message would be displayed on the console as ‘Server is running at http://localhost:6060’ . Open a browser to check if the content is running by typing the URL in the address bar “http://localhost:6060/”.

    - nodejs server.js
    - http://localhost:6060



## A simple exercise

1. In general any index file gets executed when the base URL executes. How to attach an html file is shown in this exercise. Create a html file like the one below in the same directory (nodejsapp).

    - gedit index.html and enter the below lines of html code
    
 ```html
    <html>
    <body>
      <center>
        <h2>Testing NodeJS Application </h2>
        <p> This is my first web application using NodeJS </p>
      </center>
    </body>
    </html> 
    
```

2. Create another JavaScript File named as server2.js using the nano editor with the below code in it to view the index.html file after web server connection is created. The fs module is used to read the index.html file. Save the file and execute it.


```javascript

var http = require('http');
var fs = require('fs');

var server = http.createServer(function (request, response) {

    if (request.url === "/") {
        fs.readFile("index.html", function (error, pgResp) {
            if (error) {
                response.writeHead(404);
                response.write('Page is not found');
            } else {
                response.writeHead(200, { 'Content-Type': 'text/html' });
                response.write(pgResp);
            }

            response.end();
        });
    } else {

        response.writeHead(200, { 'Content-Type': 'text/html' });
        response.write('<h1>Default Content</h1>');
        response.end();
    }
});

server.listen(5000);

console.log('Server is listening on 5000'); 

```

3. After executing the command, type this url in a browser 
    - http://localhost:5000


## There will be three kinds of outputs that can be expected from the above.

1. If the connection is established correctly and the “index.html” file exists then the contents of the index.html file will be loaded on the browser.
2. If the connection is established rightly but the “index.html” file is not located on the current location then the message ‘Page is not found’ will be printed.
3. If both the connection is established and the file too is available in the required location but the requested url is incorrect then the text ‘Default content’ will be displayed by default.

* The port number 5000 is set as the one listening here, so when the connection to the web server gets established correctly then the  message “Server is listening on 5000” will be shown on the console.


    
    
