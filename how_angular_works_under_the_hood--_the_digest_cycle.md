#How Angular works under the hood-- The digest cycle


Angular developers have their reasons for liking or disliking the framework. Those who dislike it, claim the following: Angular is too slow and/or it incorporates too much javascript into the html. Although, these points are valid, the beauty of Angular heavily outweighs the pitfalls. It comes with two-way-data-binding out of the box. This is ideal for single page applications and dynamic web applications. But, how does happen under the hood? Keep reading and you will find out.

##$scope

###$scope.$watch

If you are familiar with Angular, you know that `$scope` is an object that refers to your application model. It is what binds things between the controller and the view. Whenever a `$scope` is assigned to a variable a `$watch` gets assigned to it. This is key to Angular's two-way data binding, because when a `$watch` gets changed to variable the watch is initiated. 

###$scope.$digest

To go a level deeper, `$scope.digest` runs in the background and monitors which variables are getting changed that are being watched. What is being watched? This is referred to as the digest cycle or the digest loop. The method that is constantly called to update the to update data in the digest loop is `$digest`. We'll cover more about the digest cycle later in the article.

###$scope.$apply

Sometimes we see that `$scope` data is not getting updated in our HTML file. This occurs when we use API's that are external to Angular, such as (`setTimeout`,`XHR`). When we are not able to update data, we have to forcefully start that digest cycle,using `$scope.$apply`. While this sounds quite helpful, you should do this very infrequently.

## What is the difference between $scope.$digest and $scope.$apply?

You may be wondering what the difference between `$scope.apply` and `$scope.digest`. The code below should give you a better understanding. i.e.

    <!DOCTYPE html>
	<html lang="en" ng-app="sampleEx">
	<head>
	  <meta charset="UTF-8">
      <title>Document</title>
      <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.4.4/angular.min.js"></script>
    </head>
     <body>
     <div ng-app="MyApp">
    {{rootMessage}}
     <div ng-controller="MyController">
      {{childMessage}}
     </div>
     </div>
     </body>
    </html>

	<script>
    angular.module("sampleEx",[]).controller("MyController", function($rootScope, $scope){

    $rootScope.rootMessage = "This is the Root Message";
    $scope.childMessage = "This is the Child Message";

    setTimeout(function(){
      $rootScope.rootMessage = "New Root Message";
      $scope.childMessage = "New Child Message";

      //$scope.$apply();
    },1000);
    });
    </script>

When you run the following code in your browser, you'll see `This is the Root Message` and `This is the Child Message`. However, if you call the apply function, the browser will display, `New Root Message` and `New Child Message`. In conclusion, when you call `$scope.$digest` it only runs the digest loop from that particular `$scope` and all of its children. However, when you call `$scope.$apply` that uses the `$rootScope` targets all of the `$scopes` in the application.

## How does Angular extend the browser?

![Angular event loop](https://docs.angularjs.org/img/guide/concepts-runtime.png)

The rectangle on the left refers to the browser, and the one on the right refers to Angular's event loop. Events are put on the Event Queue and when they fire, they trigger callbacks. We have seen this before in Javascript's event loop. Typically, a callback will modify the DOM which the browser will then render; things are a little different in Angular.

When dealing with Angular  applications, all callbacks on the event queue that are relevant to Angular have the `$apply` function in them. When an event is fired, it goes into the Javascript event loop, runs `$apply`, then goes into the Angular JS event loop. When the digest loop runs, it always runs against `$scope`.

The digest loop is what runs after the `$apply` function imports a callback into the Angular event loop. The digest loop has two sub-loops: `$watch list` and `$evalAsync`

`$evalAsync` - All expressions from `$evalAsync` will be added to the queue and they will be a part of the current lifecycle and no new digest cycle will be invoked. What makes `$evalAsync` so efficient is that it reduces the possibility to create a new digest every time. 

`$watchlist` - This is where Angular implements dirty checking. This runs until the DOM is up to date(it is not dirty).

Don't worry if you are slightly confused about `$evalAsync`; it is primarily used for building larger applications. For your understanding, `$watchlist` is more important. 

Once everything on the `$watchlist` has been checked the DOM is rendered.

####Dirty Checking

Dirty Checking is a process to check if the value of an expression has changed. It simply compares an old value with a new one to determine if it has changed. Angular uses dirty checking to determine whether the value of a variable has changed or not. If it hs, it does the required operation. Feel free to read further [here](http://stackoverflow.com/questions/24698620/dirty-checking-on-angular).

I hope this gave you a better understanding of Angular and how it two-way-binds. Try it out yourself and as always, good hunting!

