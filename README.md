QEDServer
============

You've just come across a great new client-side library that makes building richer client-side apps a breeze. It has support for client-side storage, but you're really interested in using this with an existing server-side web application, so you decide to try it out. Then you realize that to test everything, you need a backend. That means you need to write some server side code, set up a database, and you need to deploy the thing on a web server so that all the AJAX requests work right. And of course, you need to populate that database with dummy data. That's a lot of work just to try out a new framework!

QEDServer solves those pesky problems for you so you can focus on sharpening your front-end skills. In one small package, you get a simple web server that hosts a small "product catalog" web application and a database full of existing products. You can immediately start writing code against its RESTLike API that responds with JSON and XML.

You put your files in the `public` folder that QEDServer creates, visit http://localhost:8080/index.html in your browser, and you can start coding against this simple backend without worrying about server setup or same-origin-policy issues.

Additionally, QEDServer provides a web interface of its own that you can use to manage the stock data and add your own records. 

And if you need a fresh start, just delete the `products.sqlite3` file and restart QEDServer. The database will be recreated
so you'll have a clean environment again.

Setup and Usage
------
Visit http://qedserver.napcs.com for more on how to get started!

Customized Builds From Source
-------
If you're reading this far, you're probably interested in getting the source and customizing this to meet your needs.

You'll need JRuby. I recommend using RVM.

Then, 

    bundle
    ./start
    
This will run 'rackup' and load the server at http://localhost:9292. It's quicker to do this during development than it is to build the WAR file.

When you want to build your own package, use
    
    rake war

That will generate webserver.war, which you can launch with

    java -jar webserver.war
    
There's a `server.sh` and a `server.bat` file that you can package with

    rake package
    
That will also grab `END_USER_README.md` and throw it in the archive.

### The files
QED Server is just a Sinatra application wrapped by Warbler, so to customize it, just replace the guts. Add your own models, change the routes around, do what you need to do.

* `lib/server.rb` is the main Sinatra application.
* `lib/extensions/` contains extensions to Ruby classes.
* `lib/configuration.rb` is the code that sets up the database connections and location of the public directory by looking at where the user started up the app. 
* `lib/seed_data.rb` is just a Ruby script that loads data into the database when the server starts.
* `lib/views` contains the view files for the various pages
* `lib/models` contains the ActiveRecord models this app uses.
* `lib/controllers` contains the routes and responders for the main parts of the app
* `lib/helpers` has all the helper functions used in the views

Contributing
-----------
Fork, change, send a pull request. Please, please, please write specs!


History
------
See HISTORY for the change log.

License
--------

Copyright (C) 2011 by Brian P. Hogan

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.