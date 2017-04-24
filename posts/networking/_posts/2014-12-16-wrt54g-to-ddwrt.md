---
layout: post
title: Linksys WRT54G to DD-WRT  
permalink: wrt54g-to-ddwrt
comments: True
published: False
---
Last weekend while decluttering my home I found an unused 2006 Linksys WRT54G router. The router came from my parents' house where, until March 2014, it provided nearly flawless wired and wireless routing service for three years.

![2006_Linksys_WRT54G_v6.0](/images/2014-12-16_01.png)

## The Problem

In March 2014 the WRT54G's performance had become sluggish, deteriorating to the point where the router stopped provided routing services. The WRT54G needed to be reset every four days to get it working again. 

In addition to the frequent deteriorating of routing services, the WRT54G's built-in web GUI stopped displaying its GUI objects correctly, which made it impossible to reconfigure the router's settings. 

Resetting the WRT54G to its factory settings didn't fix the web GUI display problems.

Shown below is what a correctly displayed WRT54G web GUI main screen looks like: 

![WRT54G_GUI_correct_display](/images/2014-12-16_02.png)

Shown below is what the web GUI main screen of my 2006 WRT54G displayed:

![WRT54G_GUI_incorrect_display](/images/2014-12-16_03.png)

Luckily for my parents I had an unused and fully functional WRT54G (also 2006) router available. In April 2014 I had replaced my home network's fully functioning Linksys WRT54G router with a new Linksys E1200 N300 router. 

I traded my fully functional WRT54G for my parents' non-functional WRT54G. 

## The Plan

The non-functioning WRT54G sat in a pile of donation items intended for a local thrift store when I remembered reading a *lifehacker.com* article called [How to Supercharge Your Router with DD-WRT](http://lifehacker.com/how-to-supercharge-your-router-with-dd-wrt-508138224). 

[DD-WRT](http://www.dd-wrt.com/wiki/index.php/What_is_DD-WRT%3F) is open-source firmware for routers based on Broadcom chips, like the Linksys WRT54G. DD-WRT adds [extra features](http://www.dd-wrt.com/wiki/index.php/What_is_DD-WRT%3F#Features) not found on the original WRT54G firmware such as bandwidth usage monitoring and the ability to setup the router as a client bridge.

I had never done a firmware upgrade on computer hardware so I decided to give the DD-WRT firmware upgrade a shot. 

If the DD-WRT firmware upgrade on the WRT54G failed, then no problem since the router was going to be donated anyway. 

If the firmware upgrade succeeded, then not only would I have brought a non-functioning router back to life, I would have given it more functionality than when it was new. I'd also learn about doing firmware upgrades on network routers, the knowledge which could be applied to doing firmware upgrades on other kinds of hardware devices.

I used *dd-wrt.com*'s [How to Flash](http://dd-wrt.com/wiki/index.php/Linksys_WRT54G_v5.0_%26_5.1_%26_6.0#How_To_Flash) page for *Linksys WRT54G v5.0 & 5.1 & 6.0* as my guide. 

The rest of this blog post documents the steps I did for the DD-WRT firmware upgrade, and the one problem that I ran into and its solution.

## The Steps

### Check if the router's firmware can be upgraded to DD-WRT

The *dd-wrt.com* site has a [Supported Devices](http://www.dd-wrt.com/wiki/index.php/Supported_Devices) page that made it easy to verify that my [Linksys WRT54G v6.0 router is a supported device](http://www.dd-wrt.com/wiki/index.php/Supported_Devices#Linksys_.28Wireless_a.2Fb.2Fg.29). 

![WRT54G_supported_by_DD-WRT](/images/2014-12-16_04.png)

### Download DD-WRT installer and configuration files for WRT54G v6.0

Different routers and hardware versions of those routers have specific DD-WRT configuration files that must be used during the firmware upgrade. You can find those files by clicking the *Install Inst.* link in the DD-WRT Supported Devices table, as shown at the right column in the image above.

The DD-WRT installer and configuration files for the Linksys WRT54G v6.0 are available in a single <code>Gv5Flash.zip</code> file at [http://www.dd-wrt.com/phpBB2/viewtopic.php?t=58231](http://www.dd-wrt.com/phpBB2/viewtopic.php?t=58231).

In case the <code>Gv5Flash.zip</code> file is no longer available at the URL given above, you can also download the file from my Github site at [https://github.com/raywritescode/raywritescode.github.io/blob/master/_fileDownloads/Gv5Flash.zip](https://github.com/raywritescode/raywritescode.github.io/blob/master/_fileDownloads/Gv5Flash.zip).

Unzip the <code>Gv5Flash.zip</code> file to a temporary folder on the computer that will be used to upgrade the WRT54G's firmware.

The extracted <code>Gv5Flash.zip</code> file contains the following items:

![Gv5Flash-Contents01](/images/2014-12-16_04b.png)

The <code>vximgtoolgui</code> folder contains the following items:

![Gv5Flash-Contents02](/images/2014-12-16_04c.png)

### Read dd-wrt.com's Peacock Thread FAQ for Broadcom Only

This step applies only if your router runs the Broadcom chip, like the WRT54G does. The page is [http://www.dd-wrt.com/phpBB2/viewtopic.php?t=51486](http://www.dd-wrt.com/phpBB2/viewtopic.php?t=51486).

I recommend that at minimum you read the details of *Note 1* and *Note 5*.

*Note 1* describes how to do a Hard-reset on the router by using the 30-30-30 reset method. You'll need to do the 30-30-30 Hard-reset procedure before and after the DD-WRT firmware upgrade. 

Should the page containing *Note 1* not be available at the given URL, below are screenshots of what I think are the important parts of *Note 1*

![DD-WRT_WRT54G_v6_Note1a](/images/2014-12-16_05a.png)
![DD-WRT_WRT54G_v6_Note1b](/images/2014-12-16_05b.png)

*Note 5* emphasizes that you must follow the DD-WRT firmware upgrade steps exactly as given on *dd-wrt.com*'s web site for your particular router and router hardware version. 

Should the page containing *Note 5* not be available at the given URL, below is a screenshot of what I think is the important part of *Note 5*

![DD-WRT_WRT54G_v6_Note5](/images/2014-12-16_05c.png)

### Follow the steps exactly as given for your router

Except for steps that I wasn't able to follow because the WRT54G's non-functioning web GUI prevented me from doing so, I followed every step listed on *dd-wrt.com*'s [How to Flash](http://dd-wrt.com/wiki/index.php/Linksys_WRT54G_v5.0_%26_5.1_%26_6.0#How_To_Flash) page for *Linksys WRT54G v5.0 & 5.1 & 6.0*.

Should *dd-wrt.com*'s *How to Flash* page for *Linksys WRT54G v5.0 & 5.1 & 6.0* not be available at the given URL, below is a screenshot of all 25 steps.

![DD-WRT_WRT54G_v6_HowToFlash](/images/2014-12-16_06.png)

## Problem and Solution

### Problem - No access to WRT54G's web GUI Upgrade button

Steps 10 through 14 of the *How to Flash* guide instruct you to open the WRT54G's web GUI Firmware Upgrade screen, select the <code>.bin</code> image file for upgrade, and then click the Upgrade button.

The problem was that my WRT54G's web GUI didn't display its GUI objects, which prevented me having GUI tabs and buttons available to navigate to the Firmware Upgrade screen. 

After some research on the internet I discovered that I could display the WRT54G's Firmware Upgrade screen by manually entering the screen's HTML name in the browser's address bar.

Entering <code>http://192.168.1.1/upgrade.htm</code> in the browser's address bar took me to the Firmware Upgrade screen, which gave me access to the Browse button to select the <code>.bin</code> file. 

Unfortunately, the screen didn't display the Upgrade button needed to execute the upgrade. 

The orange oval in the screenshot below shows where the missing Upgrade button should be.

![WRT54G_MissingUpgradeButton](/images/2014-12-16_07.png)

#### Solution

After multiple failed attempts using various free firmware upgrade tools downloaded from the internet to complete steps 10 through 14 of the *How to Flash* guide, I found through experimentation that the <code>tftp.exe</code> tool (*Upgrade Firmware Version 1.255*), used for step 20, could also be used to complete steps 10 through 14.

The screenshot below shows success for steps 10 through 14.

![Step-14-success](/images/2014-12-16_10b.png)

## Conclusion

After finally getting past step 14, I completed steps 15 through 25 of the *How to Flash* guide without any problems.

I successfully upgraded the non-functioning original firmware my 2006 Linksys WRT54G v6.0 router to the more feature-rich DD-WRT firmware. 

![DD-WRT-success](/images/2014-12-16_11.png)

I spent about 15 minutes exploring all of the new router features that the DD-WRT firmware provides. I'm looking forward to testing many of those features on a separate personal test network.

Upgrading the WRT54G's firmware to use DD-WRT was a fun project and I'm glad that I gave it a shot. 

I'll now be on the lookout for discarded and non-functioning Linksys WRT54G routers to see if I can make them functional again with a DD-WRT firmware upgrade.
