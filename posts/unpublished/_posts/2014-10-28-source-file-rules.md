---
layout: post
title: 1Z0-803 Source Code File Rules 
permalink: 1Z0-803-java-source-file-rules
comments: True
published: False
---

The rules for declaring Java classes, <code>import</code> statements, and <code>package</code> statements inside a source code file are:

*  Only one <code>public</code> class per source code file.
*  Source code files can have more than one non-public class.
*  If a source code file contains a <code>public</code> class, the source file name must exactly match the class name.
*  Source code files containing no <code>public</code> classes can have a name that doesn't match any of the classes inside the file. 
*  If the class is part of a package, the <code>package</code> statement must be listed before any <code>import</code> statements inside the source code file.
*  If the class uses <code>import</code> statements, the statements must be located after the <code>package</code> statement (if used) and before the first listed class declaration.
*  <code>package</code> and <code>import</code> statements apply to all classes within the source code file. 
*  Comments are excluded from the above positioning rules. Comments can be placed at the beginning or end of a line, or on any line in the source code file.

## Java Compiler's Response to Broken Rules for Source Files

**More than one <code>public</code> class per source code file**

Contents of java file <code>twoPublic.java</code>
{% highlight java %}
public class twoPublic
{
   // first public class
}

public class secondPublic
{
   // second public class causes error
}
{% endhighlight %}

Compiler error returned

    twoPublic.java:6: error: class secondPublic is public, should be declared in a file named secondPublic.java
    public class secondPublic
           ^
**Source code's filename doesn't match the <code>public</code> class name**

Contents of java file <code>publicClass.java</code>
{% highlight java %}
public class classPublic
{
   // compile error: public class name doesn't match filename
}
{% endhighlight %}

Compiler error returned

    publicClass.java:1: error: class classPublic is public, should be declared in a file named classPublic.java
    public class classPublic
           ^
    1 error

**<code>package</code> statement listed after <code>import</code> in source code file**

Contents of java file <code>packageSecond.java</code>
{% highlight java %}
import java.util.Scanner;
package ch01;

public class packageSecond
{
   // package statement after import statement causes compiler error
}
{% endhighlight %}

Compiler error returned

    packageSecond.java:2: error: class, interface, or enum expected
    package ch01;
    ^
    1 error

**<code>import</code> statement listed after class declaration in source code file**

Contents of java file <code>importAfterClass.java</code>
{% highlight java %}
public class importAfterClass
{
   // import after class declaration causes compile error
}

import java.util.Scanner;
{% endhighlight %}

Compiler error returned

    importAfterClass.java:6: error: class, interface, or enum expected
    import java.util.Scanner;
    ^
    1 error

**More than one <code>package</code> statement in a single source code file**

Contents of java file <code>twoPackages.java</code>
{% highlight java %}
package ch01;
package 1Z0-803/ch01;

public class twoPackages
{
   // two package statements in single source file causes compile error
}
{% endhighlight %}

Compiler error returned

    twoPackages.java:2: error: class, interface, or enum expected
    package 1Z0-803/ch01;
    ^
    1 error
