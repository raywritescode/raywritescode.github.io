---
layout: post
title: Hello World!  
permalink: hello-world
comments: False
published: True 
---

This is the first post of this refocused blog. 

*Refocused* because from July 19, 2014 until this past weekend the majority of what I posted on this site was about Raspberry Pi computers, computer networking and other computer-related topics, and not very much about about coding.

I've unpublished from this site all of my blog posts dated before today. If you're interested in browsing through those past blog posts you can find them on my github repository at [github.com/raywritescode/raywritescode.github.io/tree/master/posts](https://github.com/raywritescode/raywritescode.github.io/tree/master/posts) 

This blog is named *Ray.writes.code()* so the focus of this site is appropriately now about code and the thought process that went into writing it. 

## The Problem
Last weekend I installed VMWare Workstation 12 Player on my computer. In a new VMWare virtual machine I installed Debian 8 Linux.

I've decided to refresh my knowledge of C so I installed the latest version of the GNU C Compiler on my Debian virtual machine.

To test that my C compiler works I want my computer to display the text *Hello, World!*, which is the classic first C program. 

## How to Solve It?
I used the vi editor to create a new file named *hello.c*

I'm familiar with C and the problem to solve is trivial so I coded my solution in about 20 seconds, which worked on first compile.

Not much thought process involved. 

## My Solution

~~~ 
/* hello.c */
#include <stdio.h>

int main(void) {
    printf( "Hello, World!\n" );
    return 0;
}
~~~

**Example run**
~~~
$ gcc hello.c
$ ./a.out
Hello, World!
~~~
