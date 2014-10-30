---
layout: post
title: 1Z0-803 javac and java commands 
permalink: 1Z0-803-javac-and-java-commands
comments: True
---

## Compiling Applications with javac

The <code>javac</code> command is used to invoke the Java compiler from the command line. The structural overview for <code>javac</code> is:

<code>javac [options] [source files]</code>

The <code>[options]</code> and <code>[source files]</code> are optional and each can have multiple values.

The command <code>javac -help</code> displays a list of possible options.

    Usage: javac <options> <source files>
    where possible options include:
      -g                         Generate all debugging info
      -g:none                    Generate no debugging info
      -g:{lines,vars,source}     Generate only some debugging info
      ...
      ...
      -Werror                    Terminate compilation if warnings occur
      @<filename>                Read options and filenames from file

The command <code>javac -version</code> displays the version of the Java compiler being used.

    java version "1.7.0_65"
    OpenJDK Runtime Environment (IcedTea 2.5.1) (7u65-2.5.1-2~deb7u1)
    OpenJDK Client VM (build 24.65-b04, mixed mode, sharing)

## Launching Applications with java

The <code>java</code> command is used the invoke the Java Virtual Machine (JVM). The structural overview for <code>java</code> is:

<code>java [options] class [args]</code>

The <code>[options]</code> and <code>[args]</code> are optional and can each have multiple values.

The command <code>java -help</code> displays a list of possible options.

    Usage: java [-options] class [args...]
               (to execute a class)
       or  java [-options] -jar jarfile [args...]
               (to execute a jar file)
    where options include:
        -d32	  use a 32-bit data model if available
        -d64	  use a 64-bit data model if available
        -client	  to select the "client" VM
    ...
    ...
        -javaagent:<jarpath>[=<options>]
          load Java programming language agent, see java.lang.instrument
        -splash:<imagepath>
          show splash screen with specified image
    See http://www.oracle.com/technetwork/java/javase/documentation/index.html for more details.

Only one class file to execute must be specified. No need to specify the class filename's .class extension because <code>java</code> assumes it is receving a .class file.

### Example
The DisplayTwoArguments application is generated from compiling the following <code>DisplayTwoArguments.java</code> file.

{% highlight java %}
public class DisplayTwoArguments
{
   public static void main( String[] args )
   {
      System.out.println( args[0] + " " + args[1] );
   }
}
{% endhighlight %}

To instruct <code>java</code> to display the current version of the JVM being used and then pass String arguments <code>FOO</code> and <code>BAR</code> to the DisplayTwoArguments application, enter the command:

<code>java -showversion DisplayTwoArguments FOO BAR</code>

    java version "1.7.0_65"
    OpenJDK Runtime Environment (IcedTea 2.5.1) (7u65-2.5.1-2~deb7u1)
    OpenJDK Client VM (build 24.65-b04, mixed mode, sharing)

    FOO BAR
