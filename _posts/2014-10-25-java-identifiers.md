---
layout: post
title: 1Z0-803 Java Identifiers 
permalink: 1Z0-803-java-identifiers
comments: True
---

Legal identifiers are rules the Java compiler uses to check whether or not a name is legal.

## Legal Identifier Rules
*  Identifiers must start with a letter, an underscore character (_), or a currency character ($).
*  Identifiers cannot start with a digit.
*  After the first character, any combination of letters, underscore characters, currency characters, and numbers can follow.
*  There is no limit to the number of characters an identifier can contain.
*  [Java keywords] (http://docs.oracle.com/javase/tutorial/java/nutsandbolts/_keywords.html) cannot be used as an identifier.
*  Identifiers are case sensitive. Example: identifiers **FOO** and **foo** are different. 

### Examples of Legal Identifiers
{% highlight java %} 
int maxCount;
double $balance;
double _sub_total;
int this_long_identifier_name_is_legal_though_I_do_not_recommend_this_type_of_naming;
{% endhighlight %}

### Examples of Illegal Identifiers
{% highlight java %}
int 3personTeamName;
int #inPounds;
double -finalAmount;
double total_of_purchase&tax;
String class;
{% endhighlight %}

## Java Compiler's Response to Illegal Identifiers
Contents of java file <code>illegalIdentifiers.java</code>
{% highlight java %}
public class illegalIdentifiers
{
   int 3personTeamName;
   int #inPounds;
   double -finalAmount;
   double total_of_purchase&tax;
   String class;
}
{% endhighlight %}

Error messages returned by the Java compiler after running the command: 

<code>javac illegalIdentifiers.java</code>

    illegalIdentifiers.java:3: error: <identifier> expected
       int 3personTeamName;
          ^
    illegalIdentifiers.java:3: error: <identifier> expected
       int 3personTeamName;
                          ^
    illegalIdentifiers.java:4: error: illegal character: \35
       int #inPounds;
           ^
    illegalIdentifiers.java:4: error: <identifier> expected
       int #inPounds;
                    ^
    illegalIdentifiers.java:5: error: <identifier> expected
       double -finalAmount;
             ^
    illegalIdentifiers.java:5: error: <identifier> expected
       double -finalAmount;
                          ^
    illegalIdentifiers.java:6: error: ';' expected
       double total_of_purchase&tax;
                               ^
    illegalIdentifiers.java:6: error: <identifier> expected
       double total_of_purchase&tax;
                                   ^
    illegalIdentifiers.java:7: error: <identifier> expected
       String class;
             ^
    9 errors
