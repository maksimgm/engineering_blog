Setting Up An Express Server
===
#### Introduction

This tutorial will demonstrate how to set up an Node server using Express. Node.js is an open source environment for developing server-side web applications. A couple things make Node.js easy to use: One, it is written in Javascript, so you will not need to learn an entirely new language to use Node. Two, node, when used in conjunction with npm, its package manager, allows you to simply install and use external libraries and frameworks, such as Express.

#### What is Express?

Express is a Javascript framework that is designed for building web applicaitons. It is the de facto standard server framework for Node.js. It is minimal and provides robust features for web and mobile applciations.

#### Putting Everything Together

Before you read any furthur make sure you have Node [installed on you computer.](https://nodejs.org/en/).

Once, Node is installed, let's install some Node packages. NPM is a package manager for Javascript which is automatically installed with the Node environment. In order to access certain packages we will first initialize npm in our environment

	$ npm init

Once that is complete we will install the following: Express, EJS, body-parser, method-override, and morgan. I will go into depth what these are in a second.

The shorthand command for installing multiple packages in your terminal with one line is:

	$ npm i -S express ejs body-parser method-override morgan
	
This command will install all 5 pacakage. 

Before getting into the details of these pacakge make sure to intialize your folder as a git repository if you plan on pushing to GitHub.

	git init
	
Furthermore, Node packages are very bulky, so if you push to GitHub make sure to ignore the node modules folder, so that the person pulling will not get all of the unnessecary junk.

	$ echo node_modules >> .gitignore
	
You may be wondering how people will be able to see our packages if they work with our code. Thankfully `npm init` adds a JSON file which lists all our your dependencies(packages), so if someone wants to see what packages you have installed they can easily do that.

	{
	  "name": "express_library",
	  "version": "1.0.0",
	  "description": "",
	  "main": "app.js",
	  "scripts": {
    	"test": "echo \"Error: no test specified\" && 		exit 1"
	  },
	  "author": "",
	  "license": "ISC",
	  "dependencies": {
    	"body-parser": "^1.13.3",
	    "ejs": "^2.3.4",
    	"express": "^4.13.3",
	    "method-override": "^2.3.5",
    	"mongoose": "^4.1.7",
	    "morgan": "^1.6.1",
    	"request": "^2.62.0"
	  }
	}

As you can see all of the packages I have installed in my Node environment are listed in my dependencies.


##### EJS

EJS stands for embedded Javascript. It allows us to add embedded Javascript into our HTML files. Check out the documentation for more [information](http://www.embeddedjs.com/).

##### Body-parser

Body-parser is a piece of [middleware](http://expressjs.com/guide/using-middleware.html) which will parse the body of a request being sent ot us by the browser when a form is submitted. In short, it will allow use to the `POST` method.

##### Method-override

Method-override is another piece of middelware that will allow us to use the `PUT` and `DELETE` method in our file.

If you want to read more about HTTP refer to the [following](http://code.tutsplus.com/tutorials/http-the-protocol-every-web-developer-must-know-part-1--net-31177)

##### Morgan

Morgan is an HTTP request logger middleware for Node.js. It logs the status codes whenever a request is made, and is a good piece of middleware to utilize in order to help troubleshoot most issues.

```
//require the express module to use it in your app
var express = require("express"),
  app = express();

//set the ejs in order to use embedded javascipt files
app.set("view engine", "ejs");

//enables you to use static files like, frontend
//html, css, and JS
app.use(express.static(__dirname+"/public"));

//allows you to use body-parser
var bodyParser = require("body-parser");
app.use(bodyParser.urlencoded({extended: true}));

//allows you to use method-override
var methodOverride = require('method-override');
app.use(methodOverride('_method'));

//allows you to use morgan
var morgan = require('morgan');
app.use(morgan('tiny'));

//In your URL, go to `http://localhost:3000/` and 
//you should be able to see your application.
//You are now running a local server on your machine.

app.listen(3000,function(){
  console.log("Got to localhost:3000/");
});
```
#### Putting it all together

In order to start your server, go to the folder where your file is and enter:

	node <filename.js>
	
Now that your server is running you will be able to view your application in `http://localhost:3000/`.

The strengths of Node.js as a technology is the fact that it is made up of node-modules which allow you to install a variety of packages, such as body-parser, Express, and Morgan. This makes the Node environment very flxible to work in. Particulary, for real-time applications Node.js is incredbily exciting and I think we will see more application being built in Node. 