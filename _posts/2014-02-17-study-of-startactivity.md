---
layout: post
title: A Study of startActivity(Intent) 
permalink: study-of-startactivity
comments: True
published: False
---

To test my retained knowledge of Android development I attempted to create a simple application from scratch without using reference materials or the Android GUI Layout Manager.

I failed completing the project on my first attempt.

Over the course of two hours I practiced making the application from scratch six times. By the sixth time I was able to complete the application from scratch, from memory, within 15 minutes.

These are my notes.

## A Study Of

This first *A Study Of* exercise practiced using Android’s `startActivty()` method and an explicit Intent object to start a second Activity screen.

I’ve written trivial Android applications as part of book exercises and classroom exercises where skeleton code is provided. When I attempted to write a simple application without using any reference materials and using only remembered knowledge, I found there were areas of Android development that I didn’t know as well as I thought I did.

Before identifying those areas, here is a description of the application that I attempted to build from scratch using only remembered knowledge:

*Create an application named StartActivity that displays a “Start Second Activity” button at the center of its Activity screen. Clicking the button starts a second Activity that displays “Second Activity Started” at the center of its screen.*

![startActivityGoal](/images/startActivityGoal.png)

### Areas Where I Got Stuck

I hit a roadblock at the following areas:

* Defined the LinearLayout properties incorrectly in the `activity_main.xml` file. For example, I couldn’t recall how to tell LinearLayout to center components placed on its layout. The property I couldn’t recall was `android:gravity="center"`

* Defined the `android:id` of a new Button component incorrectly in the `activity_main.xml` file. I incorrectly defined the value as `"@id/button_start"` instead of `"@+id/button_start"`

* Forgot to make my new SecondActivity class a sub-class of Activity class.

* Forgot to include `android:label="@string/app_name"` when adding the new activity tag for SecondActivity in the `AndroidManifest.xml` file.

### Areas Where I Thought I’d Get Stuck, But Didn’t

* Coding the MainActivity button’s `setOnClickListener()` method body correctly.

* Instantiating the new explicit Intent correctly.

### Concepts That I Understand Better After This Exercise

#### startActivity() method

The `startActivity()` method is used to start a new Activity. When this method is called, the current Activity is placed in the background and the called Activity is placed in the foreground.

Picture in your mind MainActivity as a plate that you eat from. Calling the `startActivity()` method to start SecondActivity is like placing the SecondActivity plate on top of the MainActivity plate. 

A collection of plates on top of each other is called a stack of plates. Likewise, a collection of Activities placed on top of each other is called a stack of Activities, or formally an “activity stack.”

Similar to [C](http://en.wikipedia.org/wiki/C_%28programming_language%29), adding a new Activity to the activity stack is pushing an Activity. Removing an Activity from the activity stack is popping an Activity.

An exercise using the `startActivityForResult()` method will be covered in a future study.

#### Explicit Intent object

You must tell the `startActivity()` method which Activity you intend it to start. You do this by passing to it an Intent object, which goes inside the method’s parentheses. Because you are explicitly identifying the target Activity to start, this Intent object is called an explicit intent.

Implicit Intents will be covered in a future study.

Here’s the `startActivity(Intent)` code used for this study.

{% highlight java %}
@Override
public void onClick(View v) {
  Intent startIntent = new Intent(MainActivity.this, SecondActivity.class);
  startActivity(startIntent);
}
{% endhighlight %}

* `Intent startIntent…` roughly translates to “create a new Intent object that identifies itself as originating from the current source class named MainActivity and has a target class named SecondActivity. Connect this new object to an Intent reference named startIntent.”

* `startActivity(startIntent);` roughly translates to “start the target activity provided by the reference named startIntent.”

# Conclusion

This exercise of creating a simple Android application from scratch without using reference materials or the Android GUI Layout Manager helped me to identify gaps in my knowledge of Android development needed for this project.

Areas where I thought I’d have no problems coding ended up blocking me. Areas where I thought I’d be blocked ended up not blocking me.

Repeated practice of coding simple applications from scratch and from memory is a good way to identify and fill knowledge gaps and to help further internalize retained knowledge.

-----

* My Android development environment consists of ADT (Android Developer Tools) IDE Build v22.3.0. Android platform is 4.3 using Google API level 18. Java version is 1.7.0_07.

* [Source code for this project](https://github.com/raywritescode/area-51-android/tree/master/StartActivityStudy) is available on GitHub.

* Below is the application in action.


<iframe width="640" height="360" src="//www.youtube.com/embed/EzObFqG3ahA?feature=player_embedded" frameborder="0" allowfullscreen></iframe>


