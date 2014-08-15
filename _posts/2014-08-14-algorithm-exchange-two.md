---
layout: post
title: Algorithm - Exchange the Values of Two Variables
permalink: algorithm-exchange-two
comments: True
---
I am currently taking a course on [Coursera](http://www.coursera.org) called [Learning How to Learn - Powerful Mental Tools to Help You Master Tough Subjects.](https://www.coursera.org/course/learning) This week's lecture is about [chunking](http://en.wikipedia.org/wiki/Chunking_%28psychology%29), which is a study technique of reducing large amounts of information into compact packages of information that your mind can easily access. I decided to study algorithms using chunking.

Instead of tackling binary search or fibonnaci algorithms at the start, this blog post begins the algorithms journey by analyzing the simpler algorithm of exchanging the value of two variables.

## The Problem
Given two variables, *numOne* and *numTwo*, exchange the values assigned to them.

### Example:

    numOne          numTwo
    ------          ------
    | 19 |          | 67 |
    ------          ------

If *numOne* holds the value 19 and *numTwo* holds the variable 67, the graphical representation above shows what the starting point looks like.

    numOne          numTwo
    ------          ------
    | 67 |          | 19 |
    ------          ------

Here’s the expected result after applying the algorithm.

### Initial Thoughts

At first glance the solution seems obvious. Assign the value of *numOne* to *numTwo* and assign the value of *numTwo* to *numOne*.

Here’s a graphical walk-through of this initial solution.

    numOne          numTwo
    ------          ------
    | 19 |          | 67 |
    ------          ------

The starting point.

    numOne          numTwo 
    ------          ------
    | 19 |          | 19 |
    ------          ------

Step 1: Assign the value of *numOne* (19) to *numTwo*.

    numOne          numTwo
    ------          ------
    | 19 |          | 19 |
    ------          ------

Step 2: Assign the value of *numTwo* (19) to *numOne*.

    numOne          numTwo
    ------          ------
    | 19 |          | 19 |
    ------          ------

The result is value 19 assigned to both *numOne* and *numTwo*.

This is not the desired outcome.

### What Happened?

In Step 1, assigning the original value (19) of *numOne* overwrote the original value (67) of *numTwo* with 19.

From a human's point of view, the algorithm "assign the value of numOne to numTwo and assign the value of numTwo to numOne" should have produced the correct outcome.

From a computer's point of view, the given algorithm results in both variables holding value 19.

### How to Fix the Problem?

If this were a physical world problem where you had two containers, each containing unique objects, and you could only exchange the containers’ objects by moving only one object at a time, one solution involves introducing a third container to temporarily hold an object.

    numOne          origOne         numTwo
    ------          ------          ------
    | 19 |          |    |          | 67 |
    ------          ------          ------

Above is the graphical representation of the problem’s starting point, which now includes a temporary variable named *origOne*.

The steps of the revised solution are:

    numOne          origOne         numTwo
    ------          ------          ------
    | 19 |          | 19 |          | 67 |
    ------          ------          ------

Step 1: Assign the original value of *numOne* to *origOne*.

    numOne          origOne         numTwo
    ------          ------          ------
    | 67 |          | 19 |          | 67 |
    ------          ------          ------

Step 2: Assign the value of *numTwo* to *numOne*.

    numOne          origOne         numTwo
    ------          ------          ------
    | 67 |          | 19 |          | 19 |
    ------          ------          ------

Step 3: Assign the value of *origOne* to *numTwo*.

    numOne          numTwo
    ------          ------
    | 67 |          | 19 |
    ------          ------

The end result is the desired outcome.

### Algorithm Pseudocode for Exchanging the Value of Two Variables

    Assign the value of the first variable to a temporary variable.
    Assign the value of the second variable to the first variable.
    Assign the value of the temporary variable to the second variable.

### Algorithm Applied using C

{% highlight c linenos %}
#include <stdio.h>

int main(void) {

   int numOne;
   int numTwo;
   int origOne;

   printf("Enter an integer value for numOne: ");
   scanf("%d", &numOne);

   printf("Enter an integer value for numTwo: ");
   scanf("%d", &numTwo);

   printf("\nOriginal values:\n");
   printf("numOne = %d\n", numOne);
   printf("numTwo = %d\n", numTwo);

   /* Exchange the values of numOne and numTwo */
   origOne = numOne;
   numOne = numTwo;
   numTwo = origOne;

   printf("\nExchanged values:\n");
   printf("numOne = %d\n", numOne);
   printf("numTwo = %d\n", numTwo);

   return 0;
}

{% endhighlight %}

### Sample Run

    Enter an integer value for numOne: 19
    Enter an integer value for numTwo: 67
         
    Original values:
    numOne = 19
    numTwo = 67
         
    Exchanged values:
    numOne = 67
    numTwo = 19

## Conclusion

Exchanging the values associated with two variables is a fundamental algorithm that is used in many larger algorithms to sort and manipulate data.

Exchanging the values of two variables (*numOne* and *numTwo*) requires the use of a temporary third variable (*origOne*) to hold the original value of *numOne*.

After *origOne* gets the value of *numOne*, *numOne* gets the value of *numTwo* and *numTwo* gets the value of *origOne*).

This study provided graphical representations of both an incorrect and a correct algorithm solution. The study closed with the correct algorithm applied in a simple C program.
