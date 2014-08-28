---
layout: post
title: SICP - Block Structure and Lexical Scoping 
permalink: sicp-block-lexical
comments: True
---

# Introduction

This blog post is about **block structures** and **lexical scoping**. The code solution that I wrote for a Chapter 1 exercise is shown and the results of sample test runs are given. 

The code solution is then refactored once using block structures and the sample tests are executed. 

The block structured code is refactored a second time using lexical scoping and the sample tests are executed again to show that the expected results are returned.

## The Problem and My Solution

Exercise 1.8, page 26, of SICP presented the following problem to solve.

    Newton's method for cube roots is based on the fact that if y is an
    approximation to the cube root of x, then a better approximation is
    given by the value
    
    x/y^2 + 2y
    ----------
        3

    Use this formula to implement a cube-root procedure analogous to the
    square-root procedure.

The square-root prodedure mentioned in the problem description is found on [SICP page 21, Section 1.1.7 Example: Square Roots by Newton's Method](http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-10.html#%_sec_1.1.7).

Here's my solution coded in Scheme.

{%highlight scheme linenos %}
(define (cube x)
   (* x x x))

(define (improve guess x)
   (/ (+ (/ x (square guess))
         (* 2 guess))
      3))

(define (good-enough? guess x)
   (< (abs (- (cube guess) x)) 0.001))

(define (cube-iter guess x)
   (if (good-enough? guess x)
      guess
      (cube-iter (improve guess x)
                 x)))

(define (cubert x)
   (cube-iter 1.0 x))
{% endhighlight %}

Here are three test runs of the code.

    1 ]=> (cubert 8)
    ;Value: 2.000004911675504

    1 ]=> (cubert 27)
    ;Value: 3.0000005410641766

    1 ]=> (cubert 125)
    ;Value: 5.000000000287929

The code solution that I wrote uses only the programming concepts introduced up through page 26 of SICP, where Exercise 1.8 is given. 

The code meets the requirements given by the problem statement, the code solution (that uses five procedure definitions) is analogous to the book's example square-root procedure, and the code correctly calculates the cube root of a given number. 

### Only One Procedure is Important to the User

A problem with the cube root's code solution is that only the `cubert` procedure is important to the user because `cubert` is what the user needs (as shown in the example runs) to calculate the cube root of a number. 

The user doesn't care about the other four procedures (cube, improve, good-enough?, and cube-iter). However, in order to use the `cubert` procedure the other four procedures must be loaded into the user's Scheme interpreter.

## Block Structure

Scheme allows procedures to have internal procedure definitions that are local (or limited in scope) to the enclosing procedure. 

Here's the original code solution for Exercise 1.8 rewritten using the `cubert` procedure definition, now better named `cube-root`, as the enclosing procedure with procedure definitions `cube`, `improve`, `good-enough?`, and `cube-iter` nested inside it.

{% highlight scheme linenos %}
define (cube-root x)

   (define (improve guess x)
      (/ (+ (/ x (square guess))
         (* 2 guess))
      3))

   (define (good-enough? guess x)
      (< (abs (- (cube guess) x)) 0.001))

   (define (cube-iter guess x)
      (if (good-enough? guess x)
      guess
      (cube-iter (improve guess x)
                 x)))

   (define (cube x) (* x x x))

   (cube-iter 1.0 x))
{% endhighlight %}

Nesting of procedure definitions inside an enclosing procedure definition is called **block structure**.

The user of `cube-root` needs only the code for the new single *block structured* procedure instead of the code for the previous five separate procedures.

Running the three test cases using the new `cube-root` *block structured* procedure gives us the same results as the original test run.

    1 ]=> (cube-root 8)
    ;Value: 2.000004911675504

    1 ]=> (cube-root 27)
    ;Value: 3.0000005410641766

    1 ]=> (cube-root 125)
    ;Value: 5.000000000287929

## Lexical Scoping

The block structured refactored code can be further simplified by having each of the nested procedure definitions with two or more arguments get whatever argument values they need from the argument list of the enclosing procedure.

{% highlight scheme linenos %}
(define (cube-root x)

   (define (improve guess)
      (/ (+ (/ x (square guess))
         (* 2 guess))
      3))

   (define (good-enough? guess)
      (< (abs (- (cube guess) x)) 0.001))

   (define (cube-iter guess)
      (if (good-enough? guess)
      guess
      (cube-iter (improve guess))))

   (define (cube x) (* x x x))

   (cube-iter 1.0))
{% endhighlight %} 

In the above code the argument **x** no longer appears in the procedure definitions on line lines 3, 8, and 11. 

The **x** is also removed from lines 12, 14, 15 (which stood alone in the block structured version), and 18 (which was line 19 in the block structured version).

The **x** in the argument list for the `cube-root` procedure definition on line 1 binds **x** to the contents of the procedure definition. This means that **x** is freely available to be used anywhere inside the procedure definition (lines 2 through 18).

This behavior is called **lexical scoping**, which the footnote on page 30 of SICP describes as

    ...free variables in a procedure are taken to refer to bindings made by enclosing procedure definitions; that is, they are looked up in the environment in which the procedure was defined.

Running the three test cases using the new `cube-root` procedure using *lexical scoping* gives us the same results as the original and the *block structured* test runs.

    1 ]=> (cube-root 8)
    ;Value: 2.000004911675504

    1 ]=> (cube-root 27)
    ;Value: 3.0000005410641766

    1 ]=> (cube-root 125)
    ;Value: 5.000000000287929

# Conclusion

Where it makes sense to do so, move supporting procedure definitions inside the supported procedure definition by using **block structures**. 

Simplify the block structured code further by using **lexical scoping**, which replaces explicitly defined argument variables used by nested procedures with argument variables implicitly available to it from the enclosing procedure's argument list. 
