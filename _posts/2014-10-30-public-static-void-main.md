---
layout: post
title: 1Z0-803 public static void main(String[ ] args) 
permalink: 1Z0-803-public-static-void-main
comments: True
---

<code>main()</code> is the method used by the Java Virtual Machine (JVM) to start execution of a Java application.

The <code>main()</code> method must be defined using this specific signature:

<code>public static void main( String[] args )</code>

### Exceptions to the Specific Signature Requirement

* The order of the modifiers <code>public</code> and  <code>static</code> can be swapped.
* The String array <code>args</code> doesn't have to be named <code>args</code>.
* The String array can be declared using [varargs] (http://docs.oracle.com/javase/1.5.0/docs/guide/language/varargs.html) syntax.

The following examples are legal <code>main()</code> signatures that the JVM will accept to start execution of a Java application.

<code>static public void main( String[] args )</code>

<code>public static void main( String[] theArgumentsStringArray )</code>

<code>public static void main( String... theVarArgs )</code>

### The <code>main()</code> Method Can Be Overloaded

A single Java source code file may contain other versions of <code>main()</code> with different signatures. The JVM treats those other versions of <code>main()</code> as normal methods. The JVM will not use those versions to start execution of a Java application.

**Example**

Code inside file <code>OverloadedMain.java</code> is
{% highlight java %}
public class OverloadedMain
{
   public static void main( String args )
   {
      System.out.println(
       "public static void main( String args ) NO start" );
   }

   public static void main( String[] args )
   {
      System.out.println(
       "public static void main( String[] args ) STARTS" );
   }

   public static void main( String a1, String a2 )
   {
      System.out.println(
       "public static void main( String a1, String a2 ) NO start");
   }
}
{% endhighlight %}

After compiling the source code and starting the application with the command

<code>java OverloadedMain</code>

the second defined <code>main()</code> method listed in the source code file is executed, which prints

    public static void main( String[] args ) STARTS
