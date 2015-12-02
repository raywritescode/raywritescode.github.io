---
layout: post
title: Generating Random Numbers 
permalink: generate-random-numbers
comments: True
published: False
---

While studying the code for various processing tasks typically handled with arrays, I found myself needing a quick way to generate a random set of integers to feed into the Java array applications that I'm writing.

The creation of this simple program provided an opportunity to document the process I use to write my experimental Java applications, which is:

* create an example of how my mind sees the finished program
* write pseudocode
* add Java code to the pseudocode 

## What I Have in Mind

The command-line utility program is called <code>GenerateInts</code>. 

The program reads an integer argument from the command line. The integer's value determines how many random numbers are generated. 

The numbers generated are integer values ranging from 0 to 2147483646 (Integer.MAX_VALUE - 1).

The program outputs the random integers on separate lines to the console.

    % java GenerateInts 10
    422638819
    2000056941
    1251386323
    1014497361
    1399914501
    564649065
    1763898227
    445962818
    1279765299
    534471203

I will use the UNIX redirection metacharacter for output ( > ) to send the console output to a text file.

Example: <code>java GenerateInts 10 > tenRandomInts.txt</code>

## Pseudocode
 
    Initialize a random number generator
    Initialize an integer variable to the value of the integer argument 

    Repeat until the number of integers to generate is reached
       Generate a random integer
       Print the random integer to the console on a new line  

## Pseudocode with Java Code Added 
<code>GenerateInts.java</code>

{% highlight java %}
import java.util.Random;

public class GenerateInts
{
   public static void main( String[] args )
   {   
      // Initialize a random number generator
      Random randomNumbers = new Random();

      // Initialize an integer variable to the value 
      // of the integer argument
      int number = Integer.parseInt( args[ 0 ] );

      // Repeat until the number of integers to generate is reached
      for ( int i = 1; i <= number; i++ )
      {   
         // Generate a random integer
         int randomNumber = 
            randomNumbers.nextInt( Integer.MAX_VALUE );

         // Print the random integer to the console on a new line
         System.out.println( randomNumber );
      }   
   }   
}
{% endhighlight %}

## Pseudocode Removed
<code>GenerateInts.java</code>

{% highlight java %}
import java.util.Random;

public class GenerateInts
{
   public static void main( String[] args )
   {   
      Random randomNumbers = new Random();
      int number = Integer.parseInt( args[ 0 ] );

      for ( int i = 1; i <= number; i++ )
      {   
         int randomNumber = 
            randomNumbers.nextInt( Integer.MAX_VALUE );
         
         System.out.println( randomNumber );
      }   
   }   
}
{% endhighlight %}

## Program Execution
    $ java GenerateInts 10
    808009253
    1348540046
    1868658628
    2010017401
    351587961
    1849121357
    2138349439
    1574390509
    746273709
    666153257
