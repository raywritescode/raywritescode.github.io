---
layout: post
title: Algorithm - Exchange the Values of Two Variables 
permalink: algorithm-exchange-two
comments: True
---

The Problem

Given two variables, a and b, exchange the values assigned to them.

An Example:

If variable a contains the value 19 and variable b contains the variable 67, here’s a graphical representation of what the starting point looks like.

       a              b
    ------          ------
    | 19 |          | 67 |
    ------          ------

Here’s what the algorithm solution produces.

      a               b
    ------          ------
    | 67 |          | 19 |
    ------          ------

Initial Thoughts

At first glance the solution seems obvious. Assign the value of b to a and assign the value of a to b. Here’s a graphical walk-through of this initial solution.

The starting point.

      a               b
    ------          ------
    | 19 |          | 67 |
    ------          ------

Step 1: Assign the value of b to a.

      a               b
    ------          ------
    | 67 |          | 67 |
    ------          ------

Step 2: Assign the value of a to b.

      a               b
    ------          ------
    | 67 |          | 67 |
    ------          ------

The result is value 67 assigned to variables a and b. This is not the desired outcome.

      a               b
    ------          ------
    | 67 |          | 67 |
    ------          ------

What Happened?

In Step 1, assigning the original value of b into a overwrote the original value of a. Instead of exchanging the original values assigned to variables a and b, the initial solution made the new value of a equal to the original value of b.
How to Fix the Overwrite Problem?

If this were a physical world problem where you had two containers, each containing unique objects, and you could only exchange the containers’ objects by moving only one object at a time, one solution involves introducing a third container to temporarily hold an object.

Here’s the graphical representation of the problem’s starting point, including a temporary variable named temp.

      a              temp             b
    ------          ------          ------
    | 19 |          |    |          | 67 | 
    ------          ------          ------

The steps for the revised solution are:

Step 1: Assign the original value of a to temp.

      a              temp             b
    ------          ------          ------
    | 19 |          | 19 |          | 67 | 
    ------          ------          ------

Step 2: Assign the original value of b to a.

      a              temp             b
    ------          ------          ------
    | 67 |          | 19 |          | 67 | 
    ------          ------          ------

Step 3: Assign the original value of a in temp to b.

      a              temp             b
    ------          ------          ------
    | 67 |          | 19 |          | 19 | 
    ------          ------          ------

The end result is the desired outcome.

      a               b
    ------          ------
    | 67 |          | 19 |
    ------          ------

Algorithm Pseudocode for Exchanging the Value of Two Variables

Assign the original value of a to temp.
Assign the original value of b to a.
Assign the original value of a in temp to b.

Algorithm Applied using C

{% highlight c linenos %}
#include <stdio.h>

int main(void) {

   int a;
   int b;
   int temp;

   printf("Enter an integer value for a: ");
   scanf("%d", &a);

   printf("Enter an integer value for b: ");
   scanf("%d", &b);

   printf("\nOriginal values:\n");
   printf("Variable a = %d\n", a);
   printf("Variable b = %d\n", b);

   /* Exchange the values of a and b */
   temp = a;
   a = b;
   b = temp;

   printf("\nExchanged values:\n");
   printf("Variable a = %d\n", a);
   printf("Variable b = %d\n", b);

   return 0;
}

{% endhighlight %}

Enter an integer value for a: 19
Enter an integer value for b: 67

Original values:
Variable a = 19
Variable b = 67

Exchanged values:
Variable a = 67
Variable b = 19

Conclusion

Exchanging the values associated with two variables is a fundamental algorithm that is used in many larger algorithms to sort and manipulate data.

Exchanging the values of two variables (a and b) requires the use of a temporary third variable (temp) to hold the original value of a. After a is assigned the original value of b, the original value of a in temp is assigned to b.

This study provided graphical representations of both an incorrect and a correct algorithm solution. The study closed with the correct algorithm applied in a simple C program.
