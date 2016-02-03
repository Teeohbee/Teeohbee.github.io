---
layout: post
title: Dependency Injection in Angular
published: true
---


_Note - I remember struggling to get some dependencies correctly set up in our final project at Makers Academy, and having the realisation that the order in which you inject dependencies is important, I had no idea why. This excellent [blog post](https://www.airpair.com/angularjs/posts/top-10-mistakes-angularjs-developers-make) by Mark Meyer on airpair finally answered my question._

_Ionic must minify it's production code before deploying onto mobile phones and so our injection names became meaningless. Defining the names before the actual injection allowed our code to be minified without any loss of meaning. The excerpt below from the original blog post explains it much better._

---
Dependency injection is one of AngularJS's best patterns. It makes testing much simpler, as well as making it more clear upon which any particular object depends. AngularJS is very flexible on how things can be injected. The simplest version requires just passing the name of the dependency into the function for the module:

{% highlight javascript %}
var app = angular.module('app',[]);

app.controller('MainCtrl', function($scope, $timeout){
    $timeout(function(){
        console.log($scope);
    }, 1000);
});
{% endhighlight %}

Here, it's very clear that MainCtrl depends on $scope and $timeout.
This works well until you're ready to go to production and want to minify your code. Using UglifyJS the example becomes the following:

{% highlight javascript %}
var app=angular.module("app",[]);app.controller("MainCtrl",function(e,t){t(function(){console.log(e)},1e3)})
{% endhighlight %}

Now how does AngularJS know what MainCtrl depends upon? AngularJS provides a very simple solution to this; pass the dependencies as an array of strings, with the last element of the array being a function which takes all the dependencies as parameters.

{% highlight javascript %}
app.controller('MainCtrl', ['$scope', '$timeout', function($scope, $timeout){
    $timeout(function(){
        console.log($scope);
    }, 1000);
}]);
{% endhighlight %}

This then minifies to code with clear dependencies that AngularJS knows how to interpret:

{% highlight javascript %}
app.controller("MainCtrl",["$scope","$timeout",function(e,t){t(function(){console.log(e)},1e3)}])
{% endhighlight %}
