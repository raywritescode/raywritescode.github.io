---
layout: post
title: SICP - Mise En Place 
permalink: sicp-mise-en-place
comments: True
---

*Mise en place* is a French phrase for "putting in place." It refers to the practice followed in professional kitchens of preparing and organizing the ingredients of a recipe before the cooking work begins. This blog post describes my *mise en place* for SICP study should you too want to start the SICP journey.

## Textbook
I prefer reading from physical books so I own a physical copy of <a href="http://www.amazon.com/gp/product/0262510871/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0262510871&linkCode=as2&tag=6767151-20&linkId=IT74OVKFCMXWQNMU">Structure and Interpretation of Computer Programs - 2nd Edition (MIT Electrical Engineering and Computer Science)</a><img src="http://ir-na.amazon-adsystem.com/e/ir?t=6767151-20&l=as2&o=1&a=0262510871" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

MIT Press provides the complete text of SICP in HTML format for free online at [mitpress.mit.edu/sicp/full-text/book/book.html](http://mitpress.mit.edu/sicp/full-text/book/book.html).

You can also get a PDF version of SICP at [github.com/sarabander/sicp-pdf](https://github.com/sarabander/sicp-pdf). I haven't looked at the quality of the PDF.

## Scheme Interpreter
### MIT/GNU Scheme
I'm using [MIT/GNU Scheme](http://www.gnu.org/software/mit-scheme/) `Release 9.1 || Microcode 15.3 || Runtime 15.7 || SF 4.41 || LIAR/i386 4.118`

I installed MIT/GNU Scheme from the `mit-scheme-9.1-1(32-bit)` package that comes bundled with [Debian 7 (i386)](http://cdimage.debian.org/debian-cd/7.6.0/i386/bt-dvd/), which is the operating system that I'm using.  

The latest 9.2 version (as of this writing) of MIT/GNU Scheme is available for download at the [MIT/GNU Scheme site](http://www.gnu.org/software/mit-scheme/). 

### Racket with SICP Support
An alternative to MIT/GNU Scheme is the [Racket programming language](http://racket-lang.org/) using the third-party package [SICP Support for DrRacket](http://www.neilvandyke.org/racket-sicp/).  

I got the Racket with SICP Support combo installed and running successfully under Windows 7 and I explored the combo for about 15 minutes. 

I decided to use MIT/GNU Scheme instead of Racket with SICP Support to avoid the possibility of Scheme language implementation incompatibility problems (though I understand such problems are rare thanks to the SICP Support).

### I Don't Need No Stinkin' Scheme Interpreter
For you exceptional programmers who can run the code in your head at CPU speeds and know without a doubt that your answers are correct, a [notebook and colored pens](https://twitter.com/stevelosh/status/310487495198523393/photo/1) are probably all that you need.

## SICP Course of Study
[MIT 6.001 Structure and Interpretation of Computer Programs](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-001-structure-and-interpretation-of-computer-programs-spring-2005/index.htm).

### Study Plan
The study plan involves reading the SICP book based on [MIT 6.001's Readings sequence](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-001-structure-and-interpretation-of-computer-programs-spring-2005/readings/) before watching the [associated lecture videos](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-001-structure-and-interpretation-of-computer-programs-spring-2005/video-lectures/).

### SICP 2ed Book to Video Lectures Mapping
The MIT 6.001 video lectures are based on the first edition of SICP, which don't necessarily map one-to-one to the second edition of SICP.

Although it's not a perfect mapping between the MIT 6.001 video lectures and the second edition of SICP, [community.schemewiki.org](http://community.schemewiki.org/) provides a well thought-out [textbook-to-video-lectures map](http://community.schemewiki.org/?sicp-text-to-video-map) to follow.  

## Code Repository
Working through all of the SICP exercises is the most important activity of this project.

For all exercises I'll post my Scheme code on [github.com/raywritescode/sicp](https://github.com/raywritescode/sicp).

# Conclusion
The *SICP study* ingredients are organized and ready. 

Time to start cooking.
