---
layout: post
title: Codecademy's JavaScript 
permalink: codecademy-javascript
comments: True
published: False
---

If you’re interested in getting a basic understanding of writing code using JavaScript before deciding whether or not to pursue learning the language further, I recommend you take the [JavaScript track](http://www.codecademy.com/tracks/javascript) offered for free on [Codecademy](http://www.codecademy.com/).

Earlier this month I wanted learn the basics of JavaScript to gain knowledge of a programming language used for web development. I choose to learn from Codecademy because it’s the most well-known to me of the education providers that offer self-contained interactive JavaScript programming tutorials online.

I signed-up for Codecademy’s JavaScript track two weeks ago and I worked through a couple of exercises that day. 

Six days ago I decided to complete the track by setting aside two hours each day for JavaScript.

Today I completed Codecademy’s JavaScript track. It took me roughly 14 hours to complete all 200+ interactive exercises that make up the track.

## Prerequisites for Learning JavaScript

You don’t need to have prior knowledge of another programming language in order to work though Codecademy’s JavaScript exercises.

Before starting the JavaScript track I’d never written a line of JavaScript code. However, I knew the fundamentals of structured programming using C and the fundamentals of object-oriented programming using Java.

## The JavaScript Language

I read that JavaScript supports much of the structured programming syntax from C so I was curious to investigate. I also read that JavaScript was “object-like” or “object-based” or “object-oriented” so I was curious to find out how it compared to Java.

### C Influences

If you have some experience programming using the C language then you’ll feel at home writing JavaScript code. I did. JavaScript’s syntax is very much like that of C from its usage of operators and expression, from writing control statements and functions, and from coding arrays and structures.

Codecademy’s JavaScript track introduces you to a few of JavaScript’s object types and you’ll learn how to setup three control loops (for, while, and switch). You’ll also learn how to write single and multidimensional arrays and how to write functions.

I found coding in JavaScript easier and faster to do than with C because of JavaScript’s use of objects.

### Objects

JavaScript’s built-in operators for objects made getting information about an object easy and simple to do. For example, to ask the string object “raywritescode” to return its length you write:

{% highlight javascript %}
console.log("raywritescode".length);   // displays 13
{% endhighlight %}

Writing code to create JavaScript objects using [object literal notation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects#Using_object_initializers) felt similar to coding C structures to me. The alternative way of coding JavaScript objects using [constructor notation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects#Using_a_constructor_function) felt more properly object-oriented.

All JavaScript classes inherit methods (or properties) directly from one top-level Object class. A Parent class having its methods inherited by a Child class is called a [prototype](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects#Inheritance) in JavaScript. To make a Child class inherit methods from a class other than the Object class, you must reference the Child class’s prototype method to an object of the new Parent class.

I had to re-read and step-through Codecademy’s JavaScript sections on Object Inheritance several times before I got that “aha” moment regarding syntax usage. Now I can follow, and write, short JavaScript programs that use multiple levels of inheritance like this one:

{% highlight javascript linenos %}
// original classes
function Animal(name, numLegs) {
    this.name = name;
    this.numLegs = numLegs;
    this.isAlive = true;
}
function Penguin(name) {
    this.name = name;
    this.numLegs = 2;
}
function Emperor(name) {
    this.name = name;
    this.saying = "Waddle waddle";
}

// set up the prototype chain
Penguin.prototype = new Animal();
Emperor.prototype = new Penguin();

var myEmperor = new Emperor("Jules");

console.log(myEmperor.saying); // should print "Waddle waddle"
console.log(myEmperor.numLegs); // should print 2
console.log(myEmperor.isAlive); // should print true
{% endhighlight %}

The last two sections of Codecademy’s JavaScript track are dedicated to object-oriented thinking and basic object-oriented programming concepts. Both are also the sections with the most number of exercises and the sections that will take you the longest time to complete.

## The Codecademy JavaScript Experience

I enjoyed my JavaScript learning experience on Codecademy. The JavaScript track covered [eight topics](http://www.codecademy.com/tracks/javascript), each with an Introduction section followed by a practice project. 

The track took me from simply printing my name to writing new classes and making objects inherit methods from other objects. I felt as though I got a good broad overview of JavaScript’s programmatic capabilities.

Hints are available for each exercise in case you need a reminder. A [JavaScript glossary](http://www.codecademy.com/glossary/javascript) button is also available onscreen which takes you a page showing examples of JavaScript syntax.

There are a few things to keep in mind when working through Codecademy’s JavaScript track.

### Make sure you type what’s asked for

I had no problem understanding and following along with each exercise’s written instructions. What I discovered quickly is that unless otherwise instructed, enter text into the editor exactly as given.

For example, if the exercise instructions tell you to enter `“Hello!”` make sure you don’t enter `“hello!”` or the tutorial will think you coded something wrong.

### Close the “Way to go!” message box to practice an exercise again

If you wrote your code correctly and click the “Save & Submit Code” button, the button will be replaced by the “Start Next Lesson” button shown below.

![wayToGo](/images/wayToGo.png)

If you want to experiment more with the exercise that you just passed, close the “Start Next Lesson” button by clicking the “x” located to the right of the button.

### You’ll earn achievement badges

![javascriptBadges](/images/javascriptBadges.png)

After completing specific exercises or reaching certain milestones you’ll be awarded an achievement badge. 

I thought it was cheesy at first but soon I enjoyed earning them. I like how the badges identify what you achieved and the date you achieved it.

# Conclusion

Codecademy’s JavaScript track will give you a broad overview of JavaScript’s main features. For me it equated to roughly 14 hours of JavaScript training.

Here's my [Codecademy profile page](http://www.codecademy.com/raywritescode). 

Will Codecademy’s JavaScript track teach you about good program design and coding best practices? No. That's not the track's intent.  

There are other online resources such as [Coursera](https://www.coursera.org/), [Udacity](https://www.udacity.com/), and [MIT OpenCourseWare](http://ocw.mit.edu/index.htm) that you can use to learn those important software developer skills.

Codecademy is a learning resource that I'll use again.
