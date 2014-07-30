---
layout: post
title: My First Interactive Android App for 2014 
permalink: first-interactive-android-app
comments: True
---

Last night I wrote my first interactive Android app for 2014. It’s a simple app that displays a question and two answer buttons, and pops-up a message based on the button the user clicks. 

It’s based on the GeoQuiz exercise presented in Chapter 1 of [Android Programming: The Big Nerd Ranch Guide (Big Nerd Ranch Guides)](http://www.amazon.com/gp/product/0321804333/ref=as_li_tf_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0321804333&linkCode=as2&tag=6767151-20).

The video below is a short demo of the app.

<iframe width="640" height="360" src="//www.youtube.com/embed/2xHVxPOoE58?feature=player_embedded" frameborder="0" allowfullscreen></iframe>
<br>
Unique for me about this app is that it’s the first Android app I’ve ever written in which I hand-coded the user interface or UI components (question, buttons, and pop-up message) instead of using the Android Graphical Layout tool.

It wasn’t until I completed this exercise of hand-coding the UI components did I get the “aha” moment of understanding the behind-the-scenes work done by the Android Graphical Layout tool when it’s used to build an app’s user interface. Hand-coding the UI components forced me to:

* learn which Android classes to import in order to give the app button, text view, and pop-up messaging functionality.

* understand how to create UI objects and where to find the object’s methods needed to do specific actions.

* learn how to create listener events that wait for the user’s input and triggers the appropriate action when the event is activated.

* understand how to properly layer the code so that the UI components are built in the correct order when the user launches the app.

In my mind the GeoQuiz application looks like a deflated silver helium balloon, similar to those ballons that you see displayed at party supply stores, before it’s launched. Launching the application causes the balloon to be quickly filled with helium. 

For my GeoQuiz app “balloon” the first thing that I see take shape is the main background area (LinearLayout). Next, the area that displays the question (TextView) inflates out from the center of the LinearLayout area. Immediately below the TextView I see a blank area (another LinearLayout but smaller) also inflate out from the main LinearLayout area. Finally, two buttons (Buttons) inflate out left-to-right from the smaller LinearLayout area.

And then I see a giant silver hot-air balloon rabbit.

![hot+air+balloon](/images/hot+air+balloon.jpg)
