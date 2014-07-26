---
layout: post
title: Started Learning Android Development Today 
permalink: started-learning-android
comments: True
---

Today I started learning Android development at [Coursera](https://www.coursera.org/). The course is called [Programming Mobile Applications for Android Handheld Systems](https://www.coursera.org/course/android). It’s an eight-week online course that kicked-off today and ends March 18.

I completed watching and following along with all of Week 1′s lectures. At my unhurried pace It was a good six hours of work from start to finish according to the clock. To me it felt at most three hours.

## The Android Developer Tools (ADT) Bundle

The [ADT Bundle](http://developer.android.com/sdk/index.html) makes it easy for you to quickly get an [Android development environment](http://developer.android.com/tools/index.html) installed and running. It’s a single compressed file that contains the latest Android platform (KitKat 4.4.2 as of this writing), the [Eclipse IDE](http://en.wikipedia.org/wiki/Eclipse_%28software%29) with [ADT plugin](http://developer.android.com/tools/sdk/eclipse-adt.html), the latest device image for the [Android emulator](http://developer.android.com/tools/help/emulator.html), and additional development tools that you need to develop Android apps.

How easy and quick? After first making sure that at minimum [Java Development Kit 6 (JDK 6)](http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase6-419409.html#jdk-6u45-oth-JPR) is installed on your machine, uncompress the ADT Bundle .zip file to create the ADT Bundle folder, navigate to the folder’s eclipse sub-folder, and double-click the eclipse.exe file to launch the Android development environment.

## The Android Emulator

The Android Emulator lets you run a virtual version of an Android device. Unless you already own one, at the early stages of learning Android development there’s no need to buy a new Android device to test your applications on. 

You can create virtual devices and configure them to run the latest or older versions of the Android platform. The downside is that the emulator needs about a minute or two to launch to the virtual device’s Unlock screen.

I ran into two problems with the emulated Android device running KitKat 4.4.2.

First, the emulator failed to launch the device for lack of available physical memory on my machine (it has 8 GB total). 

Fixing the problem involved editing the virtual device’s settings so that the Memory Options RAM was 512 instead of 1024 and also enabling the Use Host GPU checkbox found under Emulation Options. Soon after that I created and launched my first Android application for 2014, which simply displayed “Hello world!”

![helloWorld](/images/helloWorld.png)

Second, the emulated KitKat 4.4.2 device didn’t display the telephone application. This prevented me from following along with instructor Professor Adam Porter, who demonstrated how to make one virtual Android device make a phone call to a second virtual Android device. 

## Using Telnet to Control the Virtual Device’s Behavior

Of the many topics covered in Week 1′s lectures, learning how to use [Telnet](http://en.wikipedia.org/wiki/Telnet) to modify the virtual device’s behavior interested me the most because of my work background in software testing and software quality assurance.

From a Telnet terminal window you can establish a connection into the virtual device and send commands to change the state of the device. Two examples follow.

First, suppose the Android application that you created is expected to behave in a particular way if the battery charge level falls below 10%. Let’s say the battery is currently 75% charged. To drop the battery charge level to 9% to trigger the behavior that you’re testing for, enter the command `power capacity 9` at the Telnet prompt.

Second, suppose you created an Android application that processes received text messages in a particular way. To send a text message to your application enter the command `sms send <your phone number> <your message>` at the Telnet prompt. You can test how your application handles phone numbers using different phone number formats and with message content of varying lengths.

# Conclusion

The above is a small sample of the many things that I learned just from the first lecture of the Coursera Android course. From the first minutes of the opening lecture I immediately saw that Professor Adam Porter and his team put together a first-rate Android programming course. 

It’s hard to believe that the eight-week course is offered for **free**.
	
If you’re interested in learning how to develop Android applications you owe it to yourself to take advantage of this free [Android programming](https://www.coursera.org/course/android) course at [Coursera](https://www.coursera.org/).

Here's a preview of the course.

<iframe width="640" height="360" src="//www.youtube.com/embed/nvupSyKqupo?feature=player_embedded" frameborder="0" allowfullscreen></iframe>
