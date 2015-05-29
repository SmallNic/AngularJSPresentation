#AngularJS
So what is Angular JS? One way to begin thinking about it is to look at why it was created.

HTML is a declarative language that is great at creating static documents, but not so much at creating dynamic documents or applications. In order to make an HTML document more like a dynamic application you often incorporate the following:
* some sort of library (like jQuery), and 
* some sort of framework (like Express)

AngularJS is a client-side framework that allows you to create more dynamic / interactive applications by taking regular HTML syntax and adding some new markup. The following is a sample of some Angular code embedded in HTML (don't worry about what it's doing just yet; simply note the new markup):

```html
<div>
  Quantity: <input type="number" ng-model="qty">
</div>
<div>
  Costs: <input type="number" ng-model="cost">
</div>
```
One of Angular's key selling points is that it doesn't need to programmatically manipulate the DOM. Instead you can describe how the User Interface should change as the state of the application changes. What this means is that you can create a model and establish the view as a projection of that model. Then when the model changes, the view automatically reflects that change. And vice versa as well. And it does this super quickly.

This process is called data-binding and it is the "automatic synchronization of data between the model and view components." As you'd imagine it ends up eliminating a lot of code.

So let's jump right into building a simple Angular JS App, and we'll discuss it as we go along. We're going to build an app that displays "Hello name," where name will be submitted by a user in a form. We will witness how the display changes dynamically as the user updates the form.

First, let's create a basic HTML file with the usual structure

```html
<!doctype html>
<html>
  <head>
    <title>My First AngularJS App</title>
  </head>
  <body>
  </body>
</html>
```
Now let's create the display in HTML. 

```html
<body>
  <label>Name:</label>
  <input type="text" placeholder="Enter a name here">
  <h1>Hello your_name</h1>
</body>
```
Good. The next step is to install AngularJS. The fastest way is to use the CDN at (https://ajax.googleapis.com/ajax/libs/angularjs/1.3.15/angular.min.js). Throw it right in your head tags.

```html
<head>
  <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.3.15/angular.min.js" ></script>
</head>
```
After installing Angular we need to initialize it. We do this by adding a new kind of markup to our html right in the html tag. We'll come back to what it's doing a little later.

```html
<!doctype html>
  <html ng-app>
```
Now as I said before, in AngularJS models affect views dynamically, so if want our view to be change with the name entered by the user, we need to create a model that captures the user input. 
The syntax for creating a new model with AngularJS is as follows: `ng-model="modelName"`

We will put that right in our input, because we want to store the user input in our model.

```html
<input type="text" ng-model="yourName" placeholder="Enter a name here">
```

We now need our view to somehow reference our model, so that it can be changed. And how we do that will look somewhat familiar to those that have used Handlebars.

```html
<h1>Hello {{yourName}}</h1>
```

That's it. Your final code should look as follows:

```html
<!doctype html>
<html ng-app>
  <head>
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.3.15/angular.min.js" ></script>
  </head>
  <body>
    <label>Name:</label>
    <input type="text" ng-model="yourName" placeholder="Enter a name here">
    <h1>Hello {{yourName}}</h1>
  </body>
</html>
```

Now open it up in your browser and voila! 

So let's talk about this a little. If you don't count the CDN, we basically only added two snippets lines of code:

```html
ng-app
ng-model="yourName"
```

These are all called directives. Directives tell AngularJS's HTML compiler to attach a specified behavior to a specific DOM element. 
The *ng-app* directive simply initializes our application
The *ng-model* directive stores/updates the value of the input field into/from a variable, i.e. *yourName*

Behind the scenes, the AngularJS HTML Compiler is attaching event listeners to the DOM objects specified in the directives, which accounts for it being so interactive.
And now you know just as much AngularJS as I do. But how cool was that? It even works in CSS. Let's quickly update the app to dynamically change the background as we type a color into a form.

```html
<!doctype html>
<html ng-app>
  <head>
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.3.15/angular.min.js"></script>
  </head>
  <body style="background:{{backgroundColor}}">
    <label>Name:</label>
    <input type="text" ng-model="yourName" placeholder="Enter a name here">
    <h1>Hello {{yourName}}! What color would you like your webpage to be?</h1>
    <input type="text" ng-model="backgroundColor" placeholder="Enter a color here">
  </body>
</html>
```

Friggin cool, right?

Sources:
* (https://angularjs.org)
* (http://campus.codeschool.com/courses/shaping-up-with-angular-js/level/1/section/1/video/1)
