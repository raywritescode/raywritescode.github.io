---
layout: post
title: Raspberry Pi NAS 
comments: True
permalink: raspberry-pi-nas 
published: False
---

At a lunch get-together three weeks ago with my friends J and H, J told us that the hard drive on his home laptop computer had recently crashed. 

Luckily, J had made a back-up of his computer one week before the crash. He said it was a hassle getting his computer back to its pre-crash state and that having the back-up to restore from made the task less painful.

J's story got me thinking about the last time I made a back-up of my current home computer's data, which was never. If my computer crashed that afternoon I'd lose two years (or 53 GB) worth of documents, pictures, and video files.

It wasn't until last weekend when I pulled out a one-year old [Raspberry Pi](http://www.raspberrypi.org/help/what-is-a-raspberry-pi/) (RPi) computer from a closet shelf did I decide to put a computer back-up solution into place.

I decided to make a Raspberry Pi NAS (Network-attached Storage).

## Raspberry Pi

If you aren’t already familiar with it, a Raspberry Pi is a low cost ($35), credit-card sized computer that plugs into a computer monitor or TV, and uses a standard keyboard and mouse.

I have the Raspberry Pi Model B, which has:

* 700MHz ARM11 MPU and 512 MB RAM.
* integrated graphics adapter and a Broadcom VideoCore IV GPU.
* one SD card reader.
* one each HDMI and RCA video outputs and one 3.5mm audio output.
* one 10/100 Fast Ethernet port.
* two USB 2.0 ports.
* one GPIO (general purpose input/output) interface.
* one microUSB power port.

I bought the Raspberry Pi computer on December 4, 2012 from [Newark/Element14](http://www.element14.com/community/community/raspberry-pi) after reading various hardware tech articles about the many interesting projects you can make with the RPi.

## NAS (Network-attached Storage)

From [wikipedia](https://en.wikipedia.org/wiki/Network-attached_storage), "a NAS unit is a computer connected to a network that provides only file-based data storage services to other devices on the network."

Up until the Raspberry Pi NAS project idea came to mind, I've always kept all of my data files on my main computer (current and previous) in various sub-folders inside folder `C:\_docs\Documents YYYY`, where `YYYY` is the current year.

Instead of making a backup of the entire hard drive I backed-up only the `_docs` folder to CDs. I never saw the need to back-up the entire hard disk to include non-data or application program files. I have a CD folder of dozens of `_docs` folder back-ups starting from 2001 of my previous two main computers.

## The Raspberry Pi NAS Plan

Last weekend I decided to continue using the same data folder naming convention and start saving all my data to the Raspberry Pi NAS instead of on my main computer’s hard drive.

The Raspberry Pi NAS will have two 1 TB hard drives. The first hard drive will be the NAS location where I store my data files. The second hard drive will be a backup of the first.

## The Raspberry Pi NAS Components

*Tip: On most browsers right-clicking on the following images will display a pop-up menu containing an option to view each image at full-size.*

![componentsNAS](/images/componentsNAS.png)

Except for the two USB hard drives, all the other components for this project I already owned and those components weren’t being used for other purposes.

## Computer: Raspberry Pi (RPi)

When you buy a RPi you literally receive a bare-bones computer. The first thing my RPi needed was a case, which I made out of Lego blocks. I named the computer pi-lego.

Below is what pi-lego looks like underneath the hood of its Lego case.

![pi-legoOpen](/images/pi-legoOpen.png)


Below is what pi-lego looks like enclosed in its case.

![pi-legoEnclosed](/images/pi-legoEnclosed.png)


Referring to the lower-left picture above, I designed the center area of the case to store a couple of extra SD cards. At one point I had three SD cards each configured with Linux images to use the RPi for different purposes.  

There is enough room in the center area to also hold a small USB memory stick. The blue and white Lego blocks on top of the case mimic the design of the stackable powered USB hub that I’m using to power pi-lego.

## Power Source: Belkin USB 2.0 7-Port Hub

![belkin](/images/belkin.png)

The Raspberry Pi needs 5 volts, 700mA of power minimum to operate. The max power it can take is 5 volts, 1 Amp. However, even when running at 5 volts, 1 Amp the Raspberry Pi doesn’t have enough power output to operate itself and two external USB hard drives attached to it.

You need a powered USB hub. The Belkin USB 2.0 7-Port hub provides 5 volts, 3.9 Amps of power, which provides full and steady power to pi-lego and to its two external USB hard drives.

The open area on the Belkin USB hub allows you to stack another same-model or similarly designed hub on top of it. I designed the top of pi-lego’s case to stack the Belkin hub on top of it.

## Storage: Toshiba Canvio Slim II USB 3.0 1 TB Hard Drive (x2)

![toshiba](/images/toshiba.png)

The Toshiba Canvio Slim II USB 1 TB hard drives were on discounted sale ($64.99, normally $79) at my local Best Buy store last weekend. None were available on the shelves the day I visited the store so I picked up two Seagate USB 1 TB hard drives, which each cost $5 more than the Toshibas on discounted sale. Seconds before paying for the Seagates I asked if more of the Toshiba 1 TB hard drives were available in their stock room. Two were available.

Although the Toshiba Canvio USB hard drive can operate at USB 3.0 speed, it will be operating at USB 2.0 because USB 2.0 is what the Raspberry Pi supports.

I originally planned to buy two 500 GB hard drives because I only amassed 53 GB worth of data over the past two years and 500 GB is overkill for my storage needs. For an extra $10 I could get two 1 TB hard drives, so I did (super overkill).

I named the hard drives NAS01 and NAS02.

## Operating System: Raspbian Debian Wheezy on Sony 16GB SD Card

I downloaded pi-lego’s Linux operating system image from the official [Raspberry Pi website](http://www.raspberrypi.org/downloads/) and put the image on a high-speed 16 GB Sony SD card. I labeled the card “pi-lego.”

As with the 1 TB hard drives, the 16 GB SD card was overkill for this project. Only 20 MB of the 16 GB SD card is being used by the Raspbian operating system. I used a 16 GB SD card because it was the only unused Class 10 (high speed) SD card I had available at home.

If you plan on building a Raspberry Pi NAS of your own, a 2 GB SD card at most is all you need. For faster operating system performance make sure that the SD card you use is Class 10 rated.

## Internet: Ethernet Cable

![nasAssembled](/images/nasAssembled.png)

In the micro data center where I eventually housed pi-lego it sits next to the wireless router which it uses to connect to my home network. The day after pi-lego went “live to production” I replaced the six-foot gray Ethernet cable shown in the set of pictures above with a one-foot blue Ethernet patch cable.

## Other Components Needed Temporarily

![buildingNAS](/images/buildingNAS.png)

The Raspberry Pi NAS run as a headless server, which means that in normal operation it doesn’t have a monitor, keyboard, and mouse physically attached to it. Instead, you [ssh](http://en.wikipedia.org/wiki/Secure_Shell) into the Raspberry Pi NAS from another computer to control it. However, while building the Raspberry Pi NAS I had to temporarily attach my main computer’s second monitor and a spare keyboard and mouse to the RPi to install and configure its operating system and software.

## Installing and Configuring Software for the NAS

There are many tutorials and HOW-TOs available online for free that walk you step-by-step on building a Raspberry Pi NAS, so I won’t write about those details here. Instead, here are the seven high-level steps that I did, along with links to the main online resources that I used.

1. Download the Raspbian Wheezy bootable OS image and flash (write) the image to the SD card.

2. Attach all components (minus power supply) to the Raspberry Pi and insert the SD card into the RPi. Attach the power supply to boot the RPi. You attach the power supply last because the RPi  intentionally doesn’t have an on/off switch.

3. Configure the RPi with basic system settings and update and upgrade the operating system software. Make sure to enable ssh functionality so you can login to the RPi from a remote computer.

4. Prepare and mount the external USB hard drives.

5. Install and configure Samba to access the hard drives from another computer on your home network.

6. Configure the RPi so that during reboots it automatically mounts the external hard drives.

7. Configure the RPi for data redundancy by installing rsync and using cron to automate the process of copying files from one hard drive to the other. I created a cron job that runs rsync daily at 3 AM to synchronize the data on NAS02 with data changes made to NAS01 since the previous day's rsync.

For steps 1 through 3, I referenced [How-To Geek's - The HTG Guide to Getting Started with Raspberry Pi](http://www.howtogeek.com/138281/the-htg-guide-to-getting-started-with-raspberry-pi/).

For steps 4 through 7, I referenced [How-To Geek's - How to Turn a Raspberry Pi into a Low-Power Network Storage Device](http://www.howtogeek.com/139433/how-to-turn-a-raspberry-pi-into-a-low-power-network-storage-device/).

## Find a Home for the NAS

The final step is installing your working Raspberry Pi NAS at its new home location. This turned out to be a project of its own. I'll write about pi-lego's new home location and about my new micro data center in a future blog post.

## Raspberry Pi NAS Performance

The [SmallNetBuilder website](http://www.smallnetbuilder.com/nas/nas-charts/view) has a chart that displays the File Copy Write Performance benchmarked throughputs (in MB/s) of around 65 different commercial NAS. Speeds range from 18.1 MB/s for the low-end NAS to 108.3 MB/s for the high-end NAS.

With those commercial NAS benchmarked speeds in mind, I did some File Copy Write Performance testing of the pi-lego Raspberry Pi NAS.

The test consisted of copying all 53 GB of my data files from my main computer to pi-lego over the wireless home network. 

*[side note: If I were running network performance tests in a commercial environment I'd run tests consisting of various file transfer sizes and with various file type combinations.]* 

I ran the test five times. Here's a screenshot from one of the test runs.

![56GB-file-copy-to-NAS-over-WirelessEthernet](/images/56GB-file-copy-to-NAS-over-WirelessEthernet.png)

pi-lego's File Copy Write Performance speed ranged from 2.3 MB/s to 2.6 MB/s. This averages to 2.45 MB/s, which is consistent with what I observed.

pi-lego's average 2.45 MB/s File Copy Write Performance is pitiful when compared to the 18.1 MB/s of the low-end commercial NAS. However, I'm pleased with pi-lego's performance because I read in various Raspberry Pi NAS tutorials, such as [ZEDT's - Raspberry Pi as NAS](http://www.zedt.eu/tech/linux/raspberry-pi-as-nas/), to expect File Copy Write Performance speeds in the 2.X MB/s range when using NTFS formatted USB hard drives. 

pi-lego uses NTFS formatted USB hard drives.

In ZEDT's tutorial, ZED increased the File Copy Write Performance of his Raspberry Pi NAS from 2.8 MB/s to 8.5 MB/s by reformatting his NAS storage hard drive from NTFS to FAT32. That's a dramatic increase in speed and I'm tempted to reformat pi-lego's hard drives to also get that speed increase.

I'll run pi-lego as-is for a month and see if its current 2.45 MB/s average performance is fast enough for my home network's needs.

## Raspberry Pi NAS CPU Load and Memory Usage

![cpuLoad](/images/cpuLoad.png)

pi-lego has an easy job. It spends the majority of its day sitting 100% idle. Look at its low CPU load and CPU usage numbers. It also uses only 59 MB of it 512 MB of RAM.

# Conclusion

This project was extremely fun to do and it automated the task of making daily backups of my important data files. 

After first gathering all of the components needed for the project, it took me about six hours working at a leisurely pace to build pi-lego from pieces to running “live in production” inside my new micro data center.
