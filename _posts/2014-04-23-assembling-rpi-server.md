---
layout: post
title: Assembling a Raspberry Pi Server 
permalink: assembling-rpi-server
comments: True
---

Over the past three weeks I’ve completed three projects based on the Raspberry Pi (RPi) computer: a NAS (network-attached storage) server, a home entertainment media server, and a personal web server. I’m currently finishing my fourth Raspberry Pi computer project, which is a remote (or off-site) backup server for my home NAS.

Raspberry Pi computer projects that use a USB hard drive for data storage must use a powered USB hub to provide power to both the RPi and the USB hard drive. When components such as a USB hard drive is attached directly to the Raspberry Pi, the Raspberry Pi's 5 volts 1 Amp power output isn't enough to provide power to itself and to the attached USB hard drive.

Symptoms of a Raspberry Pi power output deficiency include: RPi unable to load the OS (operating system), RPi not detecting the attached hard drive, and the RPi experiencing random power brown-outs.

The powered USB hub requirement doesn’t apply if your data storage is an attached USB flash drive.

After experimenting with different components to assemble a Raspberry Pi server with a USB hard drive, and after some trial-and-error attaching all the components together to create a unified look, I came up with a specific assembly that I’ll use for future RPi projects that use a USB hard drive.

The following pictorial walks you through that assembly. 

*Tip: On most browsers right-clicking on an images will display a pop-up menu containing an option to view the image at full-size*.

## Components

![01-Components](/images/01-Components.png)

* **Belkin USB 2.0 7-Port Hub F5U237v1** comes with a 5 volts, 3.9 Amps power adapter and a 5-pin mini USB cable. I purchased it from my local [Frys Electronics](http://www.frys.com/) store for this project. Only a small subset of powered USB hubs work without problems with the Raspberry Pi. I’ve tested two other powered USB hubs and experienced RPi problems with them. The Belkin F5U237v1 is my preferred powered USB hub for RPi projects. I later found a list of powered USB hubs verified working with the RPi. The list is at [elinux.org](http://elinux.org/RPi_Powered_USB_Hubs).
    
* **Raspberry Pi Model B computer** purchased online from [Newark/Element14](http://www.element14.com/community/community/raspberry-pi) in December 2012. I purchased four RPi computers at that time.
    
* **Pibow Rainbow Raspberry Pi case** purchased online from [Adafruit](http://www.adafruit.com/categories/159) in December 2012. Other Pibow cases that I purchased at that time were Clear, Toxic, Ninja, and Adafruit.
    
* **Toshiba Canvio Slim II USB 3.0 1 TB hard drive** purchased from my local [Best Buy](http://www.bestbuy.com/) store for this project. I originally chose a two-year old 320 GB My Passport Western Digital USB hard drive from my shelf of spare electronics parts for this project. I decided to instead use the same hard drive make, model, and capacity used for my home NAS.
    
* **Sony 16GB SDHC Memory Card Class 10 SF16NX/TQM** came from my shelf of spare electronics parts.
    
* **6 ft. CAT 5e network cable** from my shelf of spare electronics parts.
    
* **3 ft. USB cable – A/MicroB** purchased from [Frys Electronics](http://www.frys.com/) for this project.
    
* **7-inch black zip ties**, eight of them from my shelf of spare electronics parts. Not all will be used.
    
* **Black foam board supports** for the RPi case and hard drive, cut from scrap pieces of black foam board.

## Assembly

### Place the hard drive on the USB hub

![02-HardDriveBase](/images/02-HardDriveBase.png)

The Belkin hub’s design is great for stacking multiple hubs of the same model or design. The wide area on top of the hub is also the perfect place for an external USB hard drive to sit on. Use the two strips of cut foam board between the hub and hard drive to allow for air flow.

![03-HardDriveRaised](/images/03-HardDriveRaised.png)

The two foam board strips raise the hard drive off the hub the perfect height while the hub’s top housing for two of its USB ports prevent the hard drive from sliding forward. Make sure the hard drive’s activity light is facing the same direction as the front of the hub.

### Place the Raspberry Pi on the hard drive

![04-RPi_base01](/images/04-RPi_base01.png)

The RPi’s Pibow case has plastic feet at the corners that cause the case to slip around on top of the hard drive’s brushed aluminum surface. A foam board placed between the case and hard drive provides a secure non-slip surface for the case.

![05-RPi_base02](/images/05-RPi_base02.png)

Position the Raspberry Pi so the video and audio output jacks are facing the same direction as the front of the hub. The Pibow case sits more securely on the foam board after pressing the four corners of the case into the board.

![06-RPi_base03](/images/06-RPi_base03.png)

I discovered that pressing the four corners into the board reduces the amount of open air space between the case and the hard drive. I decided to cut the foam board into two small strips and place them between the case and hard drive as shown below.

### Secure the RPi case and hard drive to the USB hub

Take four of the zip ties and connect them together to make two long zip ties. Be careful to attach the zip ties together so the zip tie heads are oriented the same direction. Connect the zip ties together until you hear two or three clicks at the connection point.

Route the two long zip ties through the hub’s center opening and connect each zip tie’s unattached ends together, making sure to connect the ends until you hear two or three clicks at the connection point.

You’ll need to adjust the tightness of the zip ties incrementally and evenly at the four adjustment points until the zip tie heads sit firmly at the locations where you want the zip tie heads to rest. You can’t loosen a zip tie if you over-tighten it before the zip tie heads are where you want them to be. You’ll need to cut the zip tie and start again. That’s why you have extra zip ties.

![07-RPi_ZipTied](/images/07-RPi_ZipTied.png)

I chose to rest the zip ties heads at the points shown in the picture above. I also intentionally angled the zip tie heads on the bottom of the USB hub as shown to act like the heel of your foot. 

The angle raises the back of the hub enough to prevent the top-heavy rear of the hub from tipping backwards and lifting the front of the hub. Unless you like the look of the zip tie pulls sticking out, cut them off close to the zip tie heads.

The picture also gives you a clear view of the foam board’s thickness under the Pibow case and why I decided to use two foam board strips instead of the original single piece to preserve the open air space between the case and hard drive.

### Insert the SD card

![08-SD_card_installed](/images/08-SD_card_installed.png)

Make sure the SD card’s lock switch is in the unlocked position. Insert the SD card label-side facing down.

### Connect the hard drive to the USB hub

![09-HardDrive_to_USB](/images/09-HardDrive_to_USB.png)

The hard drive’s USB cable is short so I plugged it into the nearest rear USB port. A zip tie manages the extra cable length.

### Connect the RPi’s lower USB port to the USB hub

![10-RPi_to_USB](/images/10-RPi_to_USB.png)

This connection allows communication between the Raspberry Pi and any device connected to the USB hub. I chose the RPi’s lower USB port because it makes more visual sense than using the RPi’s upper USB port. Use the USB hub’s supplied 5-pin mini USB cable for this connection.

The hub’s mini USB socket is at the far left on back of the hub. Snake the cable through the open space under the two zip ties for cleaner cable management.

### Connect the RPi’s power socket to the USB hub

![11-RPi_Power_to_USB](/images/11-RPi_Power_to_USB.png)

This connection uses the 3 ft. A/MicroB USB cable, which connects the RPi’s power socket to the middle USB port at the back of the hub. 

For cleaner cable management route the standard USB plug through the loop made by the mini USB cable and zip tie the coiled excess cabling to one of the zip ties used to secure the RPi and hard drive to the hub.

## Assembly Completed

Other than attaching the power supply, the main assembly for this configuration of a Raspberry Pi server is completed.

### Front

![12-RPi_assembled_front](/images/12-RPi_assembled_front.png)

### Right

![13-RPi_assembled_right](/images/13-RPi_assembled_right.png)

### Left

![15-RPi_assembled_left](/images/15-RPi_assembled_left.png)

### Back

![14-RPi_assembled_back](/images/14-RPi_assembled_back.png)

# Conclusion

This blog post walked you through the components and the assembly sequence that I’ve chosen to use as the standard configuration for future single-unit Raspberry Pi projects that use a USB hard drive.

The main components are attached together in a secure manner, the cables are managed for a clean appearance, the assembled unit is compact, and to me it looks aesthetically pleasing.

I like Belkin’s design of having two of its seven USB ports accessible from the top of the hub. The design feature is handy when you want to connect a USB keyboard (beige cable) and a USB mouse to the RPi.

![18-RPi_quarter_scale](/images/18-RPi_quarter_scale.png)

The Raspberry Pi server shown in this pictorial will be used as a remote (or off-site) backup server for my home NAS. It will be installed at a location 21 miles from my home.

I’m currently testing two different remote backup solutions, one open-source and the other proprietary and free. I’ll write about my selection after I get the remote backup server running live in production.
