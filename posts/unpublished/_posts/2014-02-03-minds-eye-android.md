---
layout: post
title: The Mind's Eye - Android Activity Lifecycle 
permalink: minds-eye-android
comments: True
published: False
---

The first thing you need to understand when learning Android development is the Android Activity Lifecycle. The Android Activity Lifecycle are sequences of activities that the Android platform does to manage applications for you. 

The Android platform performs specific actions, in a specific order, based on whether you want to start, pause, restart, or stop an application. 

Having a good understanding of the Android Development Lifecycle early in your study of the Android platform is important because it will help you know the proper section inside the program’s source code files to write your code for the action that you want performed.

Below is a conceptual model of the Android Activity Lifecycle. The image and others like it that follow came from [developer.android.com](http://developer.android.com/training/basics/activity-lifecycle/starting.html#lifecycle-states).

![basic-lifecycle](/images/basic-lifecycle.png)

As is probably the case for many new Android developers, the above image helped me to easily visualize the Android Development Lifecycle. 

However, in order to help me better understand and remember the lifecycle, I imagine my interactions with the Android Activity Lifecycle inside of my mind as an in-person visit to the Android Application Store located inside the Android device.

I’m not crazy… really.

## The Android Application Store

I recently wrote a GeoQuiz application that displays a random question and three buttons for True, False, and Next. The True and False buttons each display a pop-up message appropriate for the question. The Next button displays a new question. 

I stopped by the Android Application Store to get the application running on my device.

At the Android Application Store I was greeted at the *Order Here* window by a young lady wearing a green polo shirt. She wore a belt of shiny tools around her waist and attached to her eyeglasses was a jeweler’s loupe.  The name tag on her shirt read “onCreate.” 

I told onCreate that I submitted a program named GeoQuiz to the store and that I wanted to run the program on my mobile device. She checked the in-box on her desk, found my program, and told me that the application would be ready in a second or two.

I sat down and watched onCreate start the application launch process.

### Launching the application

![basic-lifecycle-create](/images/basic-lifecycle-create.png)

onCreate followed the code in my GeoQuiz program as if it were a recipe card. She pulled a flat, rectangular, and white LinearLayout item from a components drawer and laid it on her workbench.  

The LinearLayout item reminded me of a deflated balloon.  

onCreate again reached into her components drawer and retrieved a TextView item and a smaller LinearLayout item, both which she attached to the first LinearLayout. onCreate reached into the components drawer a third time and retrieved the True, False, and Next buttons, which she attached to the smaller LinearLayout. She flipped down the jeweler’s loupe over her eyeglasses, pulled several tools from her belt, and began the wiring process. 

After onCreate finished attaching all the underlying code to get the components working together as a unit, she attached the GeoQuiz application to a compressed air machine and inflated GeoQuiz ready for use. She called out “created!” and then handed the GeoQuiz application to a fellow named “onStart” who stood by waiting for the hand-off.

onStart was a thin and bearded fellow who wore skinny jeans and a green plaid long-sleeved shirt. The two-antenna green Android beanie cap on onStart’s head made the oversized blacked-rimmed glasses look bigger on his face than they really were. onStart flipped a couple of switches on the GeoQuiz application to give it power. 

After he verified the GeoQuiz application was running, onStart placed the application inside a transparent holding box and then called out “started!” Although I could see the GeoQuiz application running, I couldn’t yet use it.  I had to wait for the next step in the process to complete, which was handled by a dark-haired woman named “onResume.”

On hearing “started!” onResume rose from her desk at the other side of the transparent box. She wore a proper woman’s business suit, in green. onResume retrieved the GeoQuiz application from the transparent box, walked up to the *Pick Up* window next to the *Order Here* window, and announced “GeoQuiz resumed for raywritescode.”

After onResume handed the running GeoQuiz application to me she said, “When you’re finished using the application please return to this window and ask for onPause.” She then pointed behind her to another woman wearing the same styled green business suit, only her hair was blonde.

### Pausing the application

![basic-lifecycle-paused](/images/basic-lifecycle-paused.png)

I finished using the GeoQuiz application. At the *Pick Up* window I asked to see onPause. Before saying a word to me, onPause took the GeoQuiz application from me, placed it inside a partially transparent box, and called out “paused!” She then returned to the *Pick Up* window and properly greeted me. I immediately noticed the braces on her teeth. Before I finished telling onPause that I was finished using the GeoQuiz application, she immediately replied.

Contrary to her name, onPause spoke quickly and with barely a pause.

“Do you want us to stop the GeoQuiz application and hold it out of view while you run a new application or do you not want to run additional applications and stop using the GeoQuiz application that’s currently paused, because if you want to run a second application then you’ll need to request it from onCreate at the next window, but if you want to continue running the GeoQuiz application then I’ll pass it to onResume who’ll hand it back to you, otherwise I’ll give the GeoQuiz application to onStop who will terminate the application and have it destroyed by onDestroy.”

“No, thank you,” I said, “I’m finished using the app.”

![basic-lifecycle-savestate](/images/basic-lifecycle-savestate.png)

“Sounds good,” said onPause, “I’ll make sure that the current state of GeoQuiz is saved if needed before it’s destroyed, that way we can restore GeoQuiz to its last saved state when you ask us run the application again.”

“That’s much appreciated,” I said.

onPause said goodbye to me and then she turned around and walked toward a tall and heavily muscled man. They high-fived their hands together and the man called out “stop!” The partially transparent box holding the GeoQuiz application turned solid black, hiding the application from view.

The man walked to the window where I stood. The name tag on his green polo shirt, which looked two sizes too small, identified him as “onStop.” onStop’s smile revealed a large gap between his two front teeth which complemented his crewcut hair. After onStop greeted me he said, “Are you sure you want me to terminate GeoQuiz?” I resisted the temptation of asking onStop about his accent.

“Yes, I’m sure.”

“I’ll be back,” he said.

###  Stopping the application

onStop stepped away from the window and returned accompanied by an unusually short and full-bellied man whose hair grew only on the lower half of the sides and back of his head.

“This is my brother, onRestart,” said onStop. “He’s here to pass your GeoQuiz application to onStart in case you change your mind.”

“Thanks for the final check,” I said, “I’m sure I want to stop it.” Then, “You and onRestart are brothers?”

onStop put one arm around onRestart’s shoulders. Both men smiled at me and onStop said, “Yes, he’s my brother. We’re [twins](http://www.imdb.com/title/tt0096320/?ref_=fn_al_tt_1)!”

I looked downward at onRestart and then upward at onStop. “I see it.”

“Looks like I’m not needed here,” said onRestart, followed by, “Well, nice meeting you” to me followed by, “Catch you at lunchtime bro” to onStop.

“OK. Everything looks good,” said onStop. “I’ll terminate GeoQuiz and onDestroy will destroy it.”

I looked around and said to onStop, “Where’s onDestroy?”

onStop donned a pair of [dark sunglasses](http://www.imdb.com/title/tt0088247/?ref_=nv_sr_1) and lifted a [broadsword](http://www.imdb.com/title/tt0087078/?ref_=nv_sr_1) from behind the window.

“Got it,” I said.

## Conclusion

Yes, I really do run scenes like the above in my mind to help me better understand, remember, and recall concepts, information, and stories. 

I covered the main Android Activity Lifecycle use cases. There are a couple of use cases that I didn’t cover. For example, when an application is running and an incoming phone call is received. 

You can learn more about the Android Activity Lifecycle at the Android developer’s [Managing the Activity Lifecycle](http://developer.android.com/training/basics/activity-lifecycle/index.html) page.

If this view into my mind’s eye didn’t help you to better understand and remember the different activities of the Android Activity Lifecycle, then I hope you were at least entertained.
