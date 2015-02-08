---
layout: post
title: Contacting a Web Site  
permalink: contacting-a-web-site
comments: True
---

Last week someone asked me "What are the differences between [SOAP](http://en.wikipedia.org/wiki/SOAP) and [REST](http://en.wikipedia.org/wiki/Representational_state_transfer)?" and I wasn't able to provide an answer, which irked me for the rest of the day. I knew that SOAP originally stood for *Simple Object Access Protocol* and, after getting a reminder from the person asking me the question, that SOAP uses [XML](http://en.wikipedia.org/wiki/XML). 

I decided that evening to educate myself on SOAP and REST.  

While reading about SOAP and REST I found that I didn't have a good understanding of what happens in the background after you enter a [URL](http://en.wikipedia.org/wiki/Uniform_resource_locator) into the address box of a [web browser](http://en.wikipedia.org/wiki/Web_browser). 

* I knew that the browser used the URL to search through a bunch of [DNS servers](http://en.wikipedia.org/wiki/Name_server) in order to find the URL's matching [IP address](http://en.wikipedia.org/wiki/IP_address) which, if an associated IP address was found, would establish a connection to the computer located at the IP address.
* I also knew that behind-the-scenes the [HTML](http://en.wikipedia.org/wiki/HTML) [GET method](http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods) was involved and that the HTML [POST method](http://en.wikipedia.org/wiki/POST_%28HTTP%29) was used if the user submitted data to the [web site](http://en.wikipedia.org/wiki/Website).

That <s>is</s> was the extent of my behind-the-scenes web browser knowledge. 

Before tackling SOAP and REST I need to get an under-the-hood details understanding of what a web browser does after you enter a URL.

This blog post is my first step toward improving my knowledge about those topics.  

### The tools

* [Firefox](https://www.mozilla.org/en-US/firefox/new/): my default web browser. This exercise starts with the browser's [web content cache empty](https://support.mozilla.org/en-US/kb/how-clear-firefox-cache).
* [Fiddler2](http://www.telerik.com/fiddler): web debugger tool to view the behind-the-scenes details of the web browser's incoming and outgoing traffic.
* [www.raywritescode.net](http://www.raywritescode.net): a simple web site that I set up for this exercise.

### What happens when you enter a URL into the browser?

<center>![Entering a URL](/images/2015-02-06_01.png)</center>

1. The browser searches for the IP address that is associated to the *www.raywritescode.net* URL. It does this by scanning through a series of [DNS](http://en.wikipedia.org/wiki/Domain_Name_System) lookup tables until it finds a DNS lookup table that associates the URL to an IP address.  The DNS lookup sequence is:  
  * browser checks its [cached](http://en.wikipedia.org/wiki/Cache_%28computing%29) [DNS records](http://en.wikipedia.org/wiki/List_of_DNS_record_types). If the URL's IP address is found, go to step 2. Otherwise search the operating system's cache.
  * browser checks the operating system's cached DNS records. If the URL's IP address is found, go to step 2. Otherwise search the [router](http://en.wikipedia.org/wiki/Router_%28computing%29)'s cache.
  * browser checks the router's cached DNS records. If the URL's IP address is found, go to step 2. Otherwise search the [ISP](http://en.wikipedia.org/wiki/Internet_service_provider)'s cache.
  * browser checks the ISP's cached DNS records. If the URL's IP address is found, go to step 2. Otherwise do a recursive search for the IP starting from the top of the internet's [root nameserver](http://en.wikipedia.org/wiki/Root_name_server).
  * browser does a recursive search for the IP starting from the top of the root server and works its way down the worldwide DNS server hierarchy. If an IP address is found for the URL, go to step 2. Otherwise, the browser displays a DNS error page.
  
2. After the browser gets the IP address of the URL it uses the IP address to communicate with the [web resource](http://en.wikipedia.org/wiki/Web_resource) at the IP address. 
  * The web resource at [www.raywritescode.net](http://www.raywritescode.net) is a web server running on a [Raspberry Pi](http://www.raspberrypi.org/) computer located in my [micro data center](http://www.raywritescode.com/micro-data-center/) at home. <center>![www.raywritescode.net raspberry pi](/images/2015-02-06_02.png)</center>
  * The web browser connects to [port](http://en.wikipedia.org/wiki/Port_%28computer_networking%29#Common_port_numbers) 80 (used for [HTTP](http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) communications) on the web server using the [TCP protocol](http://en.wikipedia.org/wiki/Transmission_Control_Protocol).  

3. After the browser establishes a connection to the web server it sends an HTTP GET request.<center>![First HTTP GET request](/images/2015-02-06_03.png)</center>
  * **GET** identifies the URL to use. Note the trailing slash `/` added to `http://www.raywritescode.net`. The trailing slash tells the web server to respond with the `index.html` file located in the web site's root `/` directory.
  * **User-Agent** identifies the web browser being used. 
  * **Accept** identifies what type of responses the browser will accept, which in this case is a text file containing [HTML](http://en.wikipedia.org/wiki/HTML) code.

4. The web server handles (or responds to) the GET request by sending back to the web browser a response that contains the HTML code contained in www.raywritescode.net's `index.html` file.
  * The `index.html` file in the web site's root `/` directory on the web server contains the following HTML code.<center>![Contents of the web server's index.html file](/images/2015-02-06_04.png)</center>
  * The web server responds to the browser's initial GET request with the following:<center>![Web server's response to the browser's initial GET request](/images/2015-02-06_05.png)</center>
  * **200 OK** on the first line of the response is the [status code](http://www.w3.org/Protocols/HTTP/HTRESP.html). For each request that a web server receives from a web client (in this case, the web browser) it sends a status code that tells the client what happened to the client's request. `200 OK` means that the request (sending the HTML code shown in the response) was fulfilled successfully.  

5. The web browser converts to visual form the received HTML code into the [user interface](http://en.wikipedia.org/wiki/User_interface) (or UI) elements that will be displayed in the browser. If, while converting the HTML code, the browser encounters embedded objects in the code, the browser sends additional GET requests for those objects to the web server.
  * The `index.html` file's HTML code for www.raywritescode.net uses an image file called `raywritescode-net.png` which is located in the web site's root `/` directory on the web server. 
  * The browser needs the image file to display the image in the browser, so it sends the following second GET request to the web server.<center>![Second HTTP GET request](/images/2015-02-06_06.png)</center>
  * As in Step 3, the **GET** identifies the URL to use. The trailing `/raywritescode-net.png` tells the web server to respond with the `raywritescode-net.png` file located in the web site's root `/` directory.
  * **Accept** identifies that the type of response the browser will accept for the GET request is an image file.

6. The web server handles this second GET request by sending back to the web browser a response that contains the `raywritescode-net.png` image file.<center>![Web server's response to the browser's second GET request](/images/2015-02-06_07.png)</center>
  * The web server returns status code **200 OK** to the web browser, which indicates the browser's GET request for the [png](http://en.wikipedia.org/wiki/Portable_Network_Graphics) image file (identified by **Content-Type**) was fulfilled successfully.
  * Attached to the response is the `raywritescode-net.png` file, which contains the following image:<center>![raywritescode-net image](/images/2015-02-06_08.png)</center>

7. The web browser received **200 OK** status codes from the web server for all the GET requests it sent. It has everything it needs to display the web server's home page content in the browser:
  * The web site's title of `ray.writes.code( )`, taken from the HTML `<title>` tag in the received `index.html` file.
  * The web site's home page image file.

<center>![www.raywritescode.net home page](/images/2015-02-06_09.png)</center>

### Conclusion

From the user's point of view, entering `www.raywritescode.net` in the address bar of the web browser displays the web site's home page in less than one second. However, as this exercise demonstrated, even for simple web site a lot of behind-the-scenes communication and procecesses happens in that short period of time between the web browser and the web server.

Although I've used web browsers since 1993 to explore the internet and although I've worked professionally in several [QA roles](http://en.wikipedia.org/wiki/Software_quality_assurance) that involved testing web-based software applications at the UI level, I never had the need to understand in detail what happens behind-the-scenes when a web browser communicates with a web server resource. This knowledge gap in understanding HTTP network request-response transactions, as well knowledge gaps in understanding how to access web services using SOAP and REST, resulted in my recently not getting an interesting QA job that does web services testing at the [web API-level](http://en.wikipedia.org/wiki/Application_programming_interface#Web_APIs).

This blog post focused on the HTTP GET [request method](http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods). HTTP has other request methods that I plan to study and to write about: POST, PUT, DELETE, TRACE, OPTIONS, CONNECT, and PATCH.

-----

### Notes

Links to online sources that I referenced to write this blog post are provided in the body of the main text. 

Additional online sources and miscellaneous items that I referenced or used to prepare for this blog post are listed below.

* [HTTP Made Really Easy: A Practical Guide to Writing Clients and Servers](http://www.jmarshall.com/easy/http/)
* [What Happens When](https://github.com/alex/what-happens-when) - An attempt to answer the age old interview question "What happens when you type google.com into your browser and press enter?"
* [HTTP Tool v0.2.2](https://github.com/bobbyrne01/http-tool-firefox) - A Firefox add-on that I used as an alternative to [Fiddler2](http://www.telerik.com/fiddler) to send GET requests to the web server and to view web server response header, body content, status, and status text.
* `ipconfig /displaydns` - Entered at the Windows command prompt. Displays the contents of the DNS Resolver Cache.
* `ipconfig /flushdns` - Entered at the Windows command prompt. Purges the DNS Resolver cache.
* The first web browser that I used was a text-based browser called [Lynx](http://en.wikipedia.org/wiki/Lynx_%28web_browser%29), which I ran on a home-built [Slackware Linux](http://en.wikipedia.org/wiki/Slackware) machine in late 1993.
