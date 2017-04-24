---
layout: post
title: Coursera's Programming Mobile Applications for Android Handheld Systems 
permalink: coursera-pma-android
comments: True
published: False
---

Last week I completed the University of Maryland’s eight-week [Programming Mobile Applications for Android Handheld Systems](https://www.coursera.org/course/android) course through [Coursera](https://www.coursera.org/). 

This is my review of the course.

## Course Format

Course instructions consisted of three parts: Lecture, Lab, and Quiz. You also had access to a very active online discussion forum.

### Lecture

Lectures consisted of about a half-dozen videos of 10- to 20-minutes each, depending on the topics covered for the week. 

The lecture material was professionally presented by [Dr. Adam Porter](https://www.coursera.org/instructor/android), professor of computer science at the University of Maryland.

![drPorterAndroid](/images/drPorterAndroid.png)

Dr. Porter followed each sub-topic discussion with an example application that showed the sub-topic in action. After demonstrating the application’s functionality, Dr. Porter then showed the application’s code and stepped through and explained the key lines of code. Where appropriate, Dr. Porter displayed URLs in the PowerPoint presentation that led to additional information about the sub-topic.

Finally, each video lecture included several breaks for short non-graded quizzes to help students reinforce what was discussed. The quizzes were only available if you watched the lectures online.

You also had the option of downloading both the video files and the accompanying PowerPoint slides in PDF format for offline viewing.

### Lab

The week’s lab assignments involved importing skeleton files for both the application project and the application project’s test code into the Android ADT and then writing code for sections inside the application project identified by `TODO` statements.

Lines 24 and 34 in graphic below show examples of the `TODO` statements and their accompanied coding instructions. Your job is writing the missing code, which I did as shown on lines 29 – 32 and lines 36 – 39.

![labExample](/images/labExample.png)

The number of `TODO` statements ranged from 10 to almost 25 depending on the week’s subjects. As the course progressed the instructions provided by the `TODO` statements purposely became less descriptive, which encouraged (some might say “forced”) students to figure out on their own what needed to be coded.

The course requested that students *not* post their weekly assignment’s code online or to share their code with others. 

*[My code snippet is from a non-graded assignment.]*

After writing code for all the `TODO` statements you then used the provided Robotium test programs to execute a series of tests cases against the main application. 

After saving a filtered Logcat version of the each test run’s results to local individual text files, you uploaded the text files to an online lab assignment grader tool that checked the contents of your test files for the correct output.

![labCheck](/images/labCheck.png)

You received a score of `1.00 / 1` if your test results passed the grader, otherwise you received a partial score (for example `0.33 / 1`) and you could click the associated View button to see which line of your uploaded file failed. You could then use the information to help you find the associated problem area in your code.

There was no limit to how many times you could resubmit test result files to the online grader. Also, you did not incur any late penalties as long as you submitted your final version of the test results file before the assignment’s Due Date.

### Quiz

Unlike the quizzes given while watching the lecture videos online which did not count towards your course grade, the week’s assignment quiz was graded. 

The assignment quizzes consisted of eight to around 15 questions depending on the week’s topics. The questions were a mix of true/false, one choice from several, two or more choices from several, and write-in answers.

![quizExample](/images/quizExample.png)

Answering the questions required you to either review lecture notes, review code examples, or read [API documentation on developer.android.com](http://developer.android.com/reference/packages.html). 

After submitting your quiz the online grader informed you immediately of your quiz results. You had the opportunity to retake the quiz if you answered questions incorrectly. You also didn’t incur any late penalties as long as your submitted your final attempt of the quiz before the Due Date.

### Discussion Forums

Course discussion forums for each week’s lectures and labs were available and were very active. A core set of forum “regulars” developed within the first two weeks of the course starting.

![forums](/images/forums.png)

## My Thoughts About the Course

### Lecture

I liked that the week’s lecture topic was broken into several sub-topic videos that averaged 15 minutes each. For my level of programming experience, Dr. Porter gave me enough information about each sub-topic to get a general overview and to guide me to other resources for more information.

I liked Dr. Porter’s easy-going presentation style, which was neither wooden nor spastic. I also liked that Dr. Porter demonstrated the example applications and then immediately followed the demos by walking through the code. I’d follow along and run the example applications locally on my computer.

To watch the video lectures in less time I watched the lectures online at 1.5x normal speed. At 1.5x normal speed I found the lectures still easy to understand and soon it was normal to me watching and hearing Dr. Porter present the information at 1.5x speed.

### Lab

I liked that the lab assignment skeleton files came with `TODO` statements that explained what coding work was needed. I especially liked that the `TODO` statements became less descriptive as the course progressed.

I would have preferred to write the lab assignments from scratch instead of adding code to skeleton applications. However, I understand why the method of adding code to skeleton applications was used. Imagine having to manually grade the lab submissions of 100,000+ students each week. 

Having students update skeleton code made it easier for the course staff to write Robotium test cases for the lab applications, which in turn generated test results output that could be easily graded using automated methods.

### Quiz

The weekly assignment quizzes were my least favorite of the required work. Because I signed-up for the course’s Certificate of Completion option, for every quiz submission I had to first do a typing pattern recognition validation followed by having to submit a web-cam photograph of myself.

### Discussion Forums

Up until around Week 6 my involvement in the discussion forums consisted of providing hints to other students who had questions about the week’s lab assignment. 

For the Week 7 and Week 8 lab assignments I found myself on the other side of the fence and scanning the week’s forum discussions for clues to help me complete the week’s coding assignment.

## Things That I Learned

I now have a better understanding of how to code Android intents, permissions, and fragments. I also learned how to create Android UI components using code instead of using the Android’s UI Layout Manager. In fact, I now prefer creating UI components programmatically and avoid using the UI Layout Manager.

I also learned that despite having invested up to 15 hours each week for eight weeks to complete the work for this course, I’m still a beginner-level Android developer.

This course helped me to quickly identify areas of Android development that I need to study further on my own, such as such as graphics and animation, using fragments, broadcast receivers, threading, sensors, networking, and data management.

# Conclusion

I enjoyed the [Programming Mobile Applications for Android Handheld Systems](https://www.coursera.org/course/android) course. 

The course gave me a better understanding and appreciation of how to develop simple Android applications that make use of permissions, fragments, basic graphics and animation, and the basics of Android UI components. I also became much more comfortable creating Android UI components using code instead of relying on the UI Layout Manager.

The course also helped me quickly identify areas of Android development that I need to study more on my own, such as graphics and animation, using fragments, broadcast receivers, threading, sensors, networking, and data management.

The course’s format of video lectures, lab assignments, and weekly quizzes fit my learning style. I felt that Dr. Adam Porter gave me enough information each week to understand the week’s topics enough to complete the week’s lab assignments and to complete the week’s quiz both at 100%. 

I wouldn’t hesitate to enroll in future programming courses that Dr. Porter develops and makes available on Coursera.

If you decide to take the [Programming Mobile Applications for Android Handheld Systems](https://www.coursera.org/course/android) course then expect to invest up to 15 hours each week to complete each week’s assigned lectures, lab, and quiz. 

If you are comfortable coding with Java, if you understand basic object-oriented programming concepts, and if you want a great introduction to Android development, then I highly recommend you take the course the next time it’s offered by [Coursera](http://www.coursera.org).
