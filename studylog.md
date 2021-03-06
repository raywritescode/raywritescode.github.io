---
layout: page
title: Study Log
---

### January 2016

This month continues my refresher study of the C programming language that was started last month. I originally planned on switching to learning Objective-C starting at the beginning of this new year. Studying the C language has been fun and I want to continue to pointers and to file I/O.

The book that I'm studying from is [C Programming: A Modern Approach, Second Edition](http://amzn.to/1O2vzz7) by K.N. King.

The C source code written during these study sessions are available at [github.com/raywritescode/cpma2](https://github.com/raywritescode/cpma2)

**Total study hours this month:** 3.5

* **TODO** next study session
   - Continue reviewing Chapter 9 - Functions
      * Section 9.3 Arguments
         - Variable-Length Array Parameters (two dimensional arrays)
         - Using static in Array Parameter Declarations
         - Compound Literals
      * Section 9.4 The return Statement

* **07 - Thursday** (Time invested: 1.5 hours)
   - Chapter 9 - Functions
      * Section 9.3 Arguments
         - Argument Conversions
         - Array Arguments
         - Variable-Length Array Parameters. [variable-length-array.c](https://github.com/raywritescode/cpma2/blob/97d041b921807863af92460d262988179a390ac1/ch09/review/variable_length_array.c)

* **06 - Wednesday** (Time invested: 2 hours)
   - Chapter 9 - Functions
      * I started reviewing chapter 9 from the beginning because my last study session was 12 days ago. Today's study session ended at *Section 9.3 Arguments*, before sub-section *Argument Conversions* on page 194.
      * I learned that the printf function returns the number of characters that it prints. [numprint.c](https://github.com/raywritescode/cpma2/blob/master/ch09/review/numprint.c)
      * I also gained a better understanding of C passing arguments to functions by value.
         - [raise1.c](https://github.com/raywritescode/cpma2/blob/74a9122cc9c0ec5848adeff570016845d0484d2c/ch09/review/raise1.c)
         - [raise2.c](https://github.com/raywritescode/cpma2/blob/45e914475dedcbc3b286df9d4be7481aad7bd11c/ch09/review/raise2.c)
   - My new [Objective-C programming book](http://www.amazon.com/gp/product/0321967607/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0321967607&linkCode=as2&tag=6767151-20&linkId=4Q5HULKJNBJI4WYB) arrived today.  

-----

### December 2015

This month continues my refresher study of the C programming language to prepare for learning Objective-C starting January 1, 2016. 

The book that I'm studying from is [C Programming: A Modern Approach, Second Edition](http://amzn.to/1O2vzz7) by K.N. King. 

The C source code written during these study sessions are available at [github.com/raywritescode/cpma2](https://github.com/raywritescode/cpma2)

**Total study hours this month:** 29 

* **TODO** next study session
   - Continue reviewing Chapter 9 - Functions     
      * Finish reading the remaining chapter and execute the code examples.

* **25 - Friday** (Christmas Day coding holiday)

* **24 - Thursday** (Time invested: 30 minutes)
   - Chapter 9 - Functions
      * Section 9.3 Arguments, sub-section Array Elements
         - Exploring using a multidimensional array as a function parameter.
         - [multi-dim-array_arg.c](https://github.com/raywritescode/cpma2/blob/183734364152c954e01c9708c45b0697cb76a0ab/ch09/review/multi_dim_array_arg.c)

* **23 - Wednesday** (Time invested: 30 minutes)
   - Chapter 9 - Functions
      * Section 9.3 Arguments, sub-section Array Elements
         - Exploring how a function is allowed to change the elements of an array parameter.
         - [change_array.c](https://github.com/raywritescode/cpma2/blob/39401b0ec868bd8198287deea091178d91f59288/ch09/review/change_array.c)

* **22 - Tuesday** (Time invested: 30 minutes)
   - Chapter 9 - Functions
      * Section 9.3 Arguments, sub-section Array Elements
         - Examined modified versions of the code that I wrote yesterday:
         * Function is told that its [array elements size is less than it really is](https://github.com/raywritescode/cpma2/blob/90680c67d7336f50d08b8b9961eda6666c6f7bce/ch09/review/one_dim_array_arg_smaller.c).
         * Function is told that its [array elements size is larger than it really is](https://github.com/raywritescode/cpma2/blob/8c5240094334c61e03c304e85ea936b4219a4b3c/ch09/review/one_dim_array_arg_larger.c).

* **21 - Monday** (Time invested: 1 hour)
   - Chapter 9 - Functions
      * Section 9.3 Arguments, sub-section Array Arguments
         - Further examining the code snippet given on page 196 illustrating the use of one-dimensional arrays.
         - I wrote a [working example of the code snippet](https://github.com/raywritescode/cpma2/blob/632582ed35bba4ceb595812b1e5fa75457d5288f/ch09/review/one_dim_array_arg.c) to practice writing code that uses a one-dimensional array in a function.

* **20 - Sunday** (Time invested: 30 minutes)
   - Chapter 9 - Functions
      * Section 9.3 Arguments, sub-sections:
         - Array Arguments
         - Variable-Length Array Parameters
         - Using static in Array Parameter Declarations
         - Compound Literals

* **19 - Saturday** (Time invested: 30 minutes)
   - Chapter 9 - Functions
      * Section 9.3 Arguments, sub-section Argument Conversions

* **18 - Friday** (Time invested: 1 hour)
   - Chapter 9 - Functions
      * Section 9.1 Defining and Calling Functions
      * Section 9.2 Function Declarations 

* **17 - Thursday** (Time invested: 1 hour)
   - Chapter 8 - Arrays
      * Programming Project 9, page 179 ([Code complete](https://github.com/raywritescode/cpma2/blob/dadd8e5b2f54e5246f911b8e89858fa579b88ba2/ch08/c8p09.c))
      * Refactored the code to make it more correct. Also, for each move the program does, the chosen direction and next letter are displayed. 

* **16 - Wednesday** (Time invested: 2.5 hours)
   - Chapter 8 - Arrays
      * Programming Project 9, page 179 ([Code complete](https://github.com/raywritescode/cpma2/blob/158446d0e4613d8ad70b0a08ec95bc775f31bd74/ch08/c8p09.c))
      * Code now solves the programming project. However, I'm thinking about refactoring the code at the next study session.

* **15 - Tuesday** (Time invested: 3 hours)
   - Chapter 8 - Arrays
      * Programming Project 9, page 179 (Code in progress - [rewrote the code, which made the program less correct](https://github.com/raywritescode/cpma2/commit/571e3c929eba06e35a8e9c59f978fd90c9bba7aa).
      * If I don't get the program running correctly by end of next study session, then I'm going stop work on Project 9 and move to *Chapter 9*.

* **14 - Monday** (Time invested: 2 hours)
   - Chapter 8 - Arrays
      * Programming Project 9, page 179 (Code in progress - [almost walks A through Z in connected cells sequence](https://github.com/raywritescode/cpma2/commit/40dcac2fd327ca42efca7e00168f445e4d623ca5))

* **13 - Sunday** (Time invested: 30 minutes)
   - Chapter 8 - Arrays
      * Programming Project 9, page 179 (Code in progress - [puts A through Z in random cells](https://github.com/raywritescode/cpma2/commit/9bdc3a6fbecbde540c96404c24b77a701e7532f1))

* **12 - Saturday** (Time invested: 30 minutes)
   - Chapter 8 - Arrays
      * Programming Project 9, page 179 (Code in progress - [populates and displays 10x10 matrix of '.' character](https://github.com/raywritescode/cpma2/commit/a733f298569faae97769abf016ca16a01284df20))

* **11 - Friday** (Time invested: 1 hour)
   - Chapter 8 - Arrays
      * Programming Project 9, page 179 (Code in progress - [added pseudocode](https://github.com/raywritescode/cpma2/commit/64c5f3678ea1db89356d88f78e4e35b0ff3c702d))

* **10 - Thursday** (Time invested: 2 hours)
   - Chapter 8 - Arrays
      * Programming Project 8, page 179 ([Code complete](https://github.com/raywritescode/cpma2/blob/c69a4f42c02f48ead60bba4225a353b8341ff463/ch08/c8p08.c))
      * Programming Project 9, page 179 (Code in progress - [problem statement and initial code](https://github.com/raywritescode/cpma2/commit/71e6650367a1e49dae5444efcfea8846ca80deba))

* **09 - Wednesday** (Time invested: 1.5 hours)
   - Chapter 8 - Arrays
      * Programming Project 8, page 179 ([Code in progress](https://github.com/raywritescode/cpma2/blob/2b8d48a5e8cf07e6247712b162645cac5540b524/ch08/c8p08.c))

* **08 - Tuesday** (Time invested: 1 hour)
  - Chapter 8 - Arrays
      * Section 8.2 Multidimensional Arrays
      * Section 8.3 Variable-Length Arrays (C99)

* **07 - Monday** (Time invested: 1.5 hours)
  - Chapter 8 - Arrays
      * Section 8.1 One-Dimensional Arrays

* **06 - Sunday** (Time invested: 2.5 hours)
  - Chapter 7 - Basic Types (**Completed**) [[github code repository for Chapter 7](https://github.com/raywritescode/cpma2/tree/master/ch07)]
      * [Programming Project 15a (short variable)](https://github.com/raywritescode/cpma2/blob/master/ch07/c7p15a.c)
      * Decided to skip sub-projects 15b through 15g.

* **05 - Saturday** (Time invested: 1.5 hours)
  - Chapter 7 - Basic Types
      * [Programming Project 14](https://github.com/raywritescode/cpma2/blob/master/ch07/c7p14.c)

* **04 - Friday** (Time invested: 1 hour)
  - Chapter 7 - Basic Types
      * Section 7.3 Character Types
      * Section 7.4 Type Conversion
      * Section 7.5 Type Definitions

* **03 - Thursday** (Time invested: 2 hours)
  - Chapter 7 - Basic Types 
      * Section 7.1 Integer Types 
      * Section 7.2 Floating Types
          * Recommended reading: [What Every Computer Scientist Should Know About Floating-Point Arithmetic](https://docs.oracle.com/cd/E19957-01/806-3568/ncg_goldberg.html)
  - Chapter 6 - Loops (**Completed**) [[github code repository for Chapter 6](https://github.com/raywritescode/cpma2/tree/master/ch06)]
      * Section 6.4 Exiting from a Loop
      * Section 6.5 The Null Statement

* **02 - Wednesday** (Time invested: 1 hour)
  - Chapter 6 - Loops 
      * Section 6.2 The do Statement
      * Section 6.3 The for Statement
