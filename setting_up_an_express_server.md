Setting Up An Express Server
===

What is Express?

Express is a Javascript frmework that makes writing Node.js easier.

Remember to run `npm init` in order to initialize the Node Package Manager. NPM allows us to utilize node modules to do a variety of tasks, such as, using express.


```
var express = require("express"),
  app = express();

app.set("view engine", "ejs");

app.use(express.static(__dirname+"/public"));

var bodyParser = require("body-parser");
app.use(bodyParser.urlencoded({extended: true}));

var methodOverride = require('method-override');
app.use(methodOverride('_method'));

var morgan = require('morgan');
app.use(morgan('tiny'));



app.listen(3000,function(){
  console.log("Got to localhost:3000/");
});
```

