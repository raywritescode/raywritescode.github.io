---
layout: post
title: Off-site Backup Server 
permalink: offsite-backup-server
comments: True
published: False
---

In my [Raspberry Pi NAS blog post](http://www.raywritescode.com/raspberry-pi-nas/) I wrote about how the data on my main computer at home had never been backed-up since buying the computer two years ago. 53 GB worth of data would be lost if the hard drive crashed. I decided to create a backup solution using Raspberry Pi computers.

Yesterday I completed the third and final phase of my computer data backup project. The third phase involved making a duplicate copy of my home’s NAS at an off-site location and synchronizing the off-site backup server daily to my home NAS.

## The Three Phases

1. **Use a networked hard drive to hold all data that I want to keep**. I previously kept all my computer data in a `C:\_docs` folder on the computer itself. Now the folder is on a networked hard drive named NAS01. If the computer’s hard drive crashes or if the computer gets lost or stolen then my important data isn’t lost too.

2. **Make a duplicate copy of the primary networked hard drive**. Data on the primary networked hard drive (NAS01) is duplicated on a secondary networked hard drive (named NAS02). A [cron](http://en.wikipedia.org/wiki/Cron) job runs daily on the NAS server that executes an [rsync](http://en.wikipedia.org/wiki/Rsync) command that syncs NAS02′s data to NAS01′s data. Both hard drives for NAS01 and NAS02 are located inside my home.

3. **Make a duplicate copy of the secondary networked hard drive at an off-site location**. If both the NAS01 and NAS02 hard drives are lost due to burglary of my home or to natural disaster to my home, a backup copy of NAS02 is available at an off-site location 21 miles away.

The rest of this blog post gives details about phase 3.

## Off-site Backup – Short Version

Daily at 5 AM my home NAS pushes its data changes from the last 24 hours to an off-site backup server. 

The home NAS does this by establishing a [SSH](http://en.wikipedia.org/wiki/Secure_Shell) connection to the off-site backup server, using rsync to send data changes made on NAS02 to the off-site server, closing the SSH connection after the data transfer ends, and then writing the activity results to a log file.

Skip down to the **Conclusion** section if you don’t want to read the long version.

## Off-site Backup – Long Version

### Assemble the backup server

![04_24_Apr2014_PI-Remote01](/images/04_24_Apr2014_PI-Remote01.png)

Details about the assembly of the Raspberry Pi off-site backup server are in my earlier blog post [Assembling a Raspberry Pi Server](http://www.raywritescode.com/assembling-rpi-server/).

I named the backup server PI-REMOTE.

### Install and configure the off-site backup server’s software

This involved preparing the Raspberry Pi’s SD card in the following sequence:

1. Download the Raspbian Debian Wheezy operating system image from [raspberrypi.org](http://www.raspberrypi.org/downloads/) and [write the image to the SD card](http://www.raspberrypi.org/documentation/installation/installing-images/windows.md) using raspberrypi.org’s guide for computers running Windows.

2. Configuring the Raspberry Pi’s Wheezy image by following the the “Initial Configuration” section (excluding the “Securing your Pi” sub-section) described in Matt Wilcox’s article [Setting up a (reasonably) secure home web-server with Raspberry Pi](http://mattwilcox.net/archives/setting-up-a-secure-home-web-server-with-raspberry-pi/).

3. Use howtogeek.com’s [How to Use rsync to Backup Your Data on Linux](http://www.howtogeek.com/135533/how-to-use-rsync-to-backup-your-data-on-linux/) guide to install `rsync` and to do a test run using `cron` to execute an `rsync` file transfer of several files inside a test folder from NAS01 to NAS02.

### Make an initial backup of NAS02 to the off-site server

In addition to the original 53 GB of data from my current main computer, my home NAS also holds 175 GB of data from my two previous main computers starting from 2002. 228 GB of data is a lot of data to transfer over the internet in one attempt, so I decided to rsync the initial 228 GB of data from NAS02 to PI-REMOTE over my home network.

It was a smart decision.

It took 68 hours for rsync to locally transfer all the data files from NAS02 to PI-REMOTE. The huge data transfer slowly deteriorated my home network’s ability to provide service to my other networked devices, which eventually led to the router crashing twice. 

Luckily, restarting the `rsync` command automatically continued the file transfer at the point where it was before the router crashed. 

### Configure port forwarding on the off-site location’s router

My off-site location is my parents’ house 21 miles away. I enabled forwarding of port 22 (used for SSH connections) on their home network’s router to a static IP address that I assigned to PI-REMOTE when it’s attached to their network. 

You can find a port forwarding guide for your particular router from portforward.com’s [Router Port Forwarding Guides](http://portforward.com/english/routers/port_forwarding/routerindex.htm) page.

### Sign-up for a dynamic DNS account for the off-site network

My home computer needs to know my parents’ home network’s internet-facing (or wide area network (WAN)) [IP address](http://en.wikipedia.org/wiki/IP_address) in order to establish a SSH connection. 

Their WAN IP address is assigned dynamically, which means the IP address changes ocassionally. This causes a problem for my automated off-site backup script, which requires a static (or non-changing) WAN IP address to establish a SSH connection between my home NAS and my parents’ network. 

This is where a [Dynamic DNS](http://en.wikipedia.org/wiki/Dynamic_DNS) service steps in.

Instead of connecting to a web site using the site’s IP address, a [DNS](http://en.wikipedia.org/wiki/Domain_Name_System) (domain name system) lets you instead use the site’s domain name (like www.raywritescode.com) to connect to the site. DNS servers normally handle static IP addresses.

A Dynamic DNS service handles dynamic (or non-static) IP addresses. Whenever a computer’s WAN IP address changes, the Dynamic DNS service detects the change and updates its DNS routing tables to reflect the change. 

I created a free [third-level domain name](http://en.wikipedia.org/wiki/Subdomain) for my parents’ home network through [www.dynu.com](http://www.dynu.com/).

To connect to my parents’ home network my home NAS establishes a SSH connection to `<parents’ network name>.dynu.com` instead of to their computer’s WAN IP address. 

When their computer’s WAN IP changes, a software app on PI-REMOTE detects the changes, sends the new WAN IP address to dynu.com, and dynu.com updates their DNS routing table to reflect the change. 

The software application is called [ddclient](http://sourceforge.net/p/ddclient/wiki/Home/).

### Install and configure ddclient on PI-REMOTE

[ddclient](http://sourceforge.net/p/ddclient/wiki/Home/) is a free, third-party, application that I installed on PI-REMOTE that informs the Dynamic DNS service (www.dynu.com in my case) of any WAN IP address changes. 

After downloading and installing `ddclient` you must configure `ddclient.conf` with specific info about the host computer and with specific info about your Dynamic DNS service account.

I followed ubuntugeek.com’s guide [Update IP addresses at dynamic DNS services Using ddclient](http://www.ubuntugeek.com/update-ip-addresses-at-dynamic-dns-services-using-ddclient.html) to download and install `ddclient`. 

I then downloaded an example [`ddclient.conf` file from dynu.com](http://www.dynu.com/Default.aspx?page=downloads&download=Dynamic%20DNS%20Service&id=22) and used it as a reference to update PI-REMOTE’s installed `ddclient.conf` file for my particular off-site set up.

### Create a SSH key-pair to use between the off-site backup server and the home NAS

A SSH key-pair is used by the home NAS to identify and authenticate itself to PI-REMOTE. In this step you create a private/public SSH key pair on the home NAS server and then copy the generated public key to the off-site backup server.

I followed Troy Johnson’s guide [Using Rsync and SSH](http://troy.jdmz.net/rsync/index.html) to generate the SSH key-pair, configure both the home NAS and PI-REMOTE for automatic SSH authentication, and to create the initial rsync-over-SSH command used to transfer files securely using SSH from the home NAS to PI-REMOTE.

### Run some basic rsync-over-SSH tests over the internet between the home NAS and off-site backup server

On NAS02 I created a `TEST` folder that contained a dozen text files and then I manually executed the rsync-over-SSH command (example below) to make sure that the files transferred over the internet to PI-REMOTE without error.

`rsync -avzP --delete <source computer's folder to copy> -e "ssh -i <your private SSH key>" <yourlogin@remotecomputer.dynu.com:<full pathname of target computer's folder to copy to>`

After I was satisfied that the rsync-over-SSH file transfer worked I ran several tests that made sure PI-REMOTE: 

* sync’d with new files

* sync’d with deleted files

* recovered without error from a file transfer that was disconnected mid-copy and had its file transfer restarted. 

### Create a new log file to record the results of the rsync-over-SSH event

Because I planned on running the off-site backups at 5 AM daily, I wanted the results of the event written to a log file so I could review the results during waking hours. I also wanted the log file overwritten daily.

On the NAS server I created a log file in `/var/log` named `rsync-remote-backup.log`. I gave the file read/write permission for the user account I chose to execute the `cron` job for the off-site backup `rsync` command.

### Create a final version of the rsync-over-SSH command

This involved updating the rsync command that was used for testing purposes to now use the actual source folder instead of the TEST folder.

*TIP: In the `rysnc` command add the `--dry-run` option immediately after rsync to do dry runs of the command, which won’t actually write changes to the destination folder. Remove the `--dry-run` option after you’ve updated the `rsync` command to your satisfaction*.

Below is the final version of the `rsync` command (all on one line) that I use for my off-site backup. The items inside brackets “[   ]” are generalized.

`rsync -avzP --delete /[full path to source folder]/ -e "ssh -i /home/[rsync-username]/.ssh/[home NAS's public SSH key file name]" [rsync-username]@[parents' network name].dynu.com:/[full path to destination folder] > /var/log/rsync-remote-backup.log`

* `-avzP` tells rsync to (a) do recursion on the transfer files and to save almost all file attributes, (v) output basic information about rsync’s execution, (z) compress the files, (P) to keep a file if the file’s transfer was interrupted and to display a file transfer’s progress.

* `--delete` tells rsync to delete files on the destination folder that no longer exist on the source folder.

* `- e "ssh -i`  tells rsync to execute the SSH command using the (i) identity provided by the public SSH key file name.

* `> /var/log/rsync-remote-backup.log` tells rsync to redirect its text output to the log file. The single `>` means overwrite the file. Use `>>` if you instead want to append to the file.

### Configure cron to run the rsync command at a specific time

I configured cron to execute the rync command daily at 5 AM. The cron command inside `/var/spool/cron/crontabs/[rsync-username]` is:

`0 5 * * * [followed by the full rsync command]`

### Check the status of the automated off-site backup 24 hours later

The day after installing PI-REMOTE at its off-site location I logged in to my home NAS server, navigated to folder `/var/logs`, and did the following:

1. Entered the command `ls -al rsync-remote-backup.log` and verified that the file’s time stamp shows that the file was updated shortly after the scheduled cron job’s time.
2. Viewed the contents of the `rsync-remote-backup.log` file to verify that file updates or file deletes made to PI-REMOTE were logged and that no rsync errors were logged.

For peace of mind, I manually SSH’d into PI-REMOTE and verified that it was indeed sync’d with file updates or file deletions made on NAS02.

# Conclusion

This blog post closes the third and final phase of the computer data backup project that I started four weeks ago. In addition to the 53 GB of data on my current main computer, I backup 175 GB of data (from 2002 to 2012) from my previous two main computers to the home NAS.

All 228 GB total of my data files now reside on a networked hard drive (NAS01) on my home’s private network instead of on my main computer’s hard drive. 

Changes made to NAS01 over the previous 24-hours are backed-up daily to a second networked hard drive (NAS02). The incremental backup updates made on NAS02 are then sent to an off-site backup computer (PI-REMOTE) 21 miles away. Execution of the daily back-ups are automated.

Excluding occasional system administration tasks, I interact only with NAS01 daily by using a mapped network drive on my main computer to use my data files. I don’t touch any files on both NAS02 and PI-REMOTE and instead leave that up to the automated daily back-ups.

The Raspberry Pi computer combined with a USB hard drive make a great low-powered server system that can be run 24/7 (estimated US $10/year in electricity). 

All of the software and all of the guides needed to install and configure a complete local and off-site back solution using the Raspberry Pi are available for free on the internet. 

I’ve provided links in this blog post to the resources that I used.

This is a fun project from start to finish for anyone interested in learning about computer hardware, operating systems, computer networks, system administration, and cryptography.
