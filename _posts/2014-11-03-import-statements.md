---
layout: post
title: 1Z0-803 Import Statements 
permalink: import-statements
comments: True
published: False
---

Suppose a class file named <code>Hello.java</code> is located in classpath folder <code>com.raywritescode.util</code> and contains the following code:

{% highlight java %}
package com.raywritescode.util;

public class Hello
{
   public void printHello()
   {
      System.out.println( 
         "Hello from com.raywritescode.util.Hello" );
   }
}
{% endhighlight %}

Without using *import statements* you need to specify the <code>Hello</code> class's *fully qualified name* inside your application's code to use the class.

For example, in <code>ImportTest.java</code> below

{% highlight java linenos %}
public class ImportTest
{
   public static void main( String[] args )
   {
      com.raywritescode.util.Hello myHello = 
         new com.raywritescode.util.Hello();
      myHello.printHello();
   }
}
{% endhighlight %}

lines 5 and 6 use the fully qualified name <code>com.raywritescode.util.Hello</code> in order to access class <code>Hello</code>.

That's a lot of typing of fully qualified names if you use classes from the various Java API packages and from your custom API packages.

## import Statement Shortcut

<code>import</code> statements spare you from having to type fully qualified names.

In class file <code>ImportTest2.java</code>

{% highlight java linenos %}
import com.raywritescode.util.Hello;

public class ImportTest2
{
   public static void main( String[] args )
   {
      Hello myHello =  new Hello();
      myHello.printHello();
   }
}
{% endhighlight %} 

the <code>import</code> statement on line 1 allows you to use the <code>Hello</code> class on line 7 without the fully qualified name.

The <code>import</code> statement tells the JVM "At package com.raywrites.util there's a class named 'Hello'. Whenever you see 'Hello' used in this class, use 'Hello" from com.raywritescode.util."

## importing Multiple Classes

If the <code>com.raywritescode.util</code> package contains a dozen classes and you want to use all 12 classes in your application, instead of writing 12 separate import statements you can add the wildcard character <code>*</code> to your single <code>import</code> statement as show on line 1 below:

{% highlight java linenos %}
import com.raywritescode.util.*;

public class ImportTest2
{
   public static void main( String[] args )
   {
      Hello myHello =  new Hello();
      myHello.printHello();

      Goodbye myGoodbye = new Goodbye();
      myGoodbye.printGoodbye();
   }
}
{% endhighlight %} 

## Mixing import Statements and Fully Qualified Names

It's legal in Java to use both <code>import</code> statements and fully qualified names in the same source code file.

<code>ImportTest3.java</code>
{% highlight java linenos %}
import com.raywritescode.util.Hello;

public class ImportTest3
{
   public static void main( String[] args )
   {
      Hello myHello =  new Hello();
      myHello.printHello();

      com.raywritescode.util.Hello yourHello =
         new com.raywritescode.util.Hello();
      yourHello.printHello();
   }
}
{% endhighlight %}

## How to Use Classes with Identical Names
Suppose you wrote a custom API class named <code>ArrayList</code> in <code>com.raywritescode.util</code> and include it as an <code>import</code> statement in the application you're currently writing.

<code>ImportTest4.java</code>
{% highlight java linenos %}
import com.raywritescode.util.ArrayList;

public class ImportTest4
{
   public static void main( String[] args )
   {
      ArrayList<String> myList = new ArrayList<String>();
   }
}
{% endhighlight %}

The Java API also has a class named <code>ArrayList</code>. It's located in <code>java.util</code>.

To use the Java API's <code>ArrayList</code> class in your <code>ImportTest4</code> application, use the Java API's fully qualified name.

<code>ImportTest4.java</code> (modified)
{% highlight java linenos %}
import com.raywritescode.util.ArrayList;

public class ImportTest4
{
   public static void main( String[] args )
   {
      ArrayList<String> myList = new ArrayList<String>();

      java.util.ArrayList<String> myOtherList =
         new java.util.ArrayList<String>();
   }
}
{% endhighlight %}

## If You're a C Programmer

Java's <code>import</code> statement is **NOT** similar to C's <code>#include</code> statement.

C's <code>#include</code> statement (directive) tells the C compiler to copy the identified code from the respective C header files into the program.

Java's <code>import</code> statement saves you from having to type fully qualified names. Nothing more.
