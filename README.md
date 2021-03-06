# Angular1-GettingStarted

Angular is a fantastic MVC framework created by Google that has a phenomenal community. Almost anything that you want to know about, someone has already asked somewhere on the inter-webs, so a simple Google search will almost definitely find you the answer. Without further ado, though, let's get started.

To get your project started, let's pull up your text editor of choice and create two files. `index.html` and `app.js`.

In your `index.html` file, go ahead and set up a normal html structure with html, head, and body tags.

```text
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title></title>
  </head>
  <body>
  </body>
</html>
```

Inside your opening html element, insert this attribute: `ng-app="myFirstNgApp"`. You have just initiated the angular app!

```text
<!DOCTYPE html>
<html ng-app="myFirstNgApp">
  <head>
    <meta charset="utf-8">
    <title></title>
  </head>
  <body>
  </body>
</html>
```

Now, inside your opening body tag, insert this attribute: `ng-controller="myFirstController`. This may or may not be your first "rodeo" so to speak. If not, great, but if so, this may seem weird. Hold tight, we'll get there before the end of part 1.

```text
<!DOCTYPE html>
<html ng-app="myFirstNgApp">
  <head>
    <meta charset="utf-8">
    <title></title>
  </head>
  <body ng-controller="myFirstController">
  </body>
</html>
```

Now that we have that, let's put one more thing inside the body tags. Put `{{hello}}` right after the opening body tag. Make sure you save the file after you do this!

```text
<!DOCTYPE html>
<html ng-app="myFirstNgApp">
  <head>
    <meta charset="utf-8">
    <title></title>
  </head>
  <body ng-controller="myFirstController">
    {{hello}}
  </body>
</html>
```

Okay, now that we're done with the `index.html` file, let's move on to `app.js`. 

At the top of `app.js`, start by writing the following on the first line of the file: `var app = angular.module('myFirstNgApp', []);`. Let's talk about what just happened. We just created an Angular module, which is going to be our entire app in this example, and we named it `myFirstNgApp`. The square brackets after the comma are empty right now, but those would normally have other modules, often third-party (like ui-boostrap or ui-router) that we would inject into our app to give it more functionality. In this case, we don't need anything, but we will down the road.

Moving on. Below that, we are going to create another instance of the app variable, but add a method to this one aptly called `controller`. Remember that attribute we added inside the opening body tag? `ng-controller`? We called it `myFirstController`, so we're going to name this controller that we make `myFirstController` so we can tie those two together. The first argument inside the controller method is the name of the controller and the second one is a callback function. If you don't know what a callback function is, it will become moderately clear in a second. Let's write this out, though:

<pre><code>app.controller('myFirstController', function() {
});
</code></pre>

If you don't know what a controller is in an MVC framework, think of it as a middleman between the model and the view, the view being the HTML, so inside this controller, we're going to be able to connect with the HTML. The way we do that is through something called the `scope` variable.

Remember inside the opening body tag, we put `{{hello}}`? We just created a variable inside `myFirstController` called `$scope.hello`. Awesome! So now, we just have to set the value of `$scope.hello` inside the controller. Per first attempt rules, let's assign `$scope.hello` to a string of `'world'`. Inside the parameters of the callback, though, we have to 'inject' `$scope`. You'll hear the word 'inject' a lot with Angular because of the idea of 'dependency injection'. We'll get more into that later, though. For now, let's make `app.js` look like this:

<pre><code>var app = angular.module('myFirstNgApp', []);

app.controller('myFirstController', function($scope) {
  $scope.hello = 'world';
});
</code></pre>

Okay, so now that we have all that, once we open that index.html, it should all work, right? CLOSE, but not yet. Let's open up index.html, though, to see what it shows. The only thing you're going to see is still `{{hello}}`. We have all the code, but we didn't include Angular in our project, so let's do that. You can do it one of two ways. You can either download it and include it in the project directory OR you can use the CDN, which is the remotely hosted version of the AngularJS file. Make sure that when you download it or grab the CDN that is of 1.5.x, not 2.x. Angular was completely rewritten for version 2 and looks/works nothing alike, so none of this would work! For this example, we're just going to use the CDN, though.

```text
<!DOCTYPE html>
<html ng-app="myFirstNgApp">
  <head>
    <meta charset="utf-8">
    <title></title>
  </head>
  <body ng-controller="myFirstController">
    {{hello}}
    
    <script src="https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.5.8/angular.js" charset="utf-8"></script>
  </body>
</html>
```
Let's pull it up again. All we see is the `{{hello}}` still. We have everything, though, right? NOPE. We didn't include `app.js`. So, let's include that and see what happens. Make sure you add it BELOW the Angular CDN. If you added it before, our project wouldn't know what "Angular" was.

```text
<!DOCTYPE html>
<html ng-app="myFirstNgApp">
  <head>
    <meta charset="utf-8">
    <title></title>
  </head>
  <body ng-controller="myFirstController">
    {{hello}}
    
    <script src="https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.5.8/angular.js" charset="utf-8"></script>
    <script src="app.js" charset="utf-8"></script>
  </body>
</html>
```

And when we pull this up, VOILA! There is our `hello` value that we set in the controller. We know have a working Angular app! Yay! I'm going to end part 1 here because that was a lot to take in, but in the next lesson, we're going to talk about ng-model and more about controllers. I strongly encourage you to follow along with the lesson and not look at the solution branch before your version is working, but if you get stuck and you can't get it working, that solution is there to help. See you in part 2!
