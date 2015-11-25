#How Angular works under the hood-- The digest cycle


Angular developers have their reasons for liking or disliking the framework. Those who dislike it, claim the following: Angular is to slow or it incorporates to much javascript into the html. Although, these points are valid, the beauty of Angular heavily outweighs the pitfalls. It comes with two-way-data-binding out of the box. This is ideal for single page applications and dynamic web applications. But, how does happen under the hood? Keep reading and you will find out.

##$scope

###$scope.$watch

If you are familiar with Angular, you know that `$scope` is an object that refers to your applciation model. It is what binds things between the controller and the view. Whenever a `$scope` is assigned to a variable a `$watch` gets assigned to it. This is key to Angular's two-way data binding, because when a `$watch` gets changed to variable the watch is initiated. 

###$scope.$digest

To go a level deeper, `$scope.digest` runs in the background and monitors what variables are getting changed that are being watched. This is refered to as the digest cycle or the digest loop. The method that is constantly called to update the to update data in the digest loop is `$digest`. We'll cover more about the digest cycle later in the article.

###$scope.$apply

Sometimes we see that `$scope` data is not getting updated in our HTML file. This occurs when we use API's that are external to Angular, such as (`setTimeout`,`XHR`). When we are not able to update data, we have to forcefully start that digest cycle,using `$scope.$apply`. While this sounds quite helpful, you should do this very **very infrequently**

## What is the difference between $scope.$digest and $scope.$apply?

After reading the following you may be wonder what the difference between `$scope.apply` and `$scope.digest` is. I'll use the following code as an example:

	<!DOCTYPE html>
	<html lang="en" ng-app="applydigest">
	<head>
	  <meta charset="UTF-8">
	  <title>Document</title>
	</head>
	<body >
	  <div>
    From $rootScope: {{name}}
	  </div>
	  <div ng-controller="MainController">
    	From $scope: {{age}}
	  </div>
	  <script src="http://ajax.googleapis.com/ajax/libs/angularjs/1.4.5/angular.min.js"></script>
	  <script src="script.js"></script>
	</body>
	</html>
-
	
	angular.module("applydigest",[]).controller("MainController", function($rootScope, $scope){
	  $rootScope.name = "Fido"
	  $scope.age = 3

	  // this is for example purposes
	  // NOTE - there is a $timeout which handles $apply for you
	  setTimeout(function(){
	    $rootScope.name = "Lassie"
	    $scope.age = 10
	    // $scope.$digest()
	    $scope.$apply()
	  },1000)
	})

When you call `$scope.digest` it only runs the digest loop from that  particular scope. However, when you call `$apply`, that uses the `$rootScope` and goes through all scopes in the application.


## How does Angular extend the browser?

![Angular event loop](https://docs.angularjs.org/img/guide/concepts-runtime.png)

The rectangle on the left refers to the browser, and the one on the right refers to Angular. Events are put on the Event Queeue and when they fire, they trigger callbacks. We have seen this before in Javascript's event loop. Typically, a callback will modify the DOM which the browser will then render; things are a little different in Angular.

When dealing with Angular  applications, all callbacks on the event queue that are relevent to Angular have the `$apply` function in them. When an event is fired, it goes into the Javascript event loop, runs `$apply`, then goes into the Agnular JS event loop. When the digest loop runs, it always runs against `$scope`.

The digest loop is what runs after the `$apply` function imports a callback into the Angular event loop. The digest loop has two sub-loops: `$watch list` and `$evalAsync`

`$evalAsync` - All expressions from `$evalAsync` will be added to the queue and they will be a part of the current lifecycle and no new digest cycle will be invoked. What makes `$evalAsync` so efficent is that it reduces the possibility to create a new digest every time. 

`$watchlist` - This is where Angular implements dirty checking. This runs until the DOM is up to date(it is not dirty).

Don't worry if you are slightly confused about `$evalAsync`; it is primarilly used for building larger applications. For your understanding, `$watchlist` is more important. 

Once everything on the `$watchlist` has been checked the DOM is rendered.

####Dirty Checking

Dirty Checking is a process to check if the value of an expression has changed. It simply compares an old value with a new one to determine if it has changed. Angular uses dirty checking to determine whether the value of a variable has changed or not. If it hs, it does the required operation. Feel free to read further [here](http://stackoverflow.com/questions/24698620/dirty-checking-on-angular).

I hope this gave you a better understanding of Angular and how it two-way-binds. Try it out yourself and as always, good hunting!