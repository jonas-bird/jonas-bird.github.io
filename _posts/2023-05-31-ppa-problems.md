---
title: ppa problems   
date: 2023-05-31 21:30:00 -0500  
categories: [linux]  
tags: [administration]       # TAG names should always be lowercase
toc: false  
---

As an Ubuntu user I have access to a decent range of packages through the standard repositories, unfortunately in many cases these are not exactly the bleeding edge. As a user of a very old laptop (at least until I get hired) I also tend to avoid snaps where possible, so for some software I use PPA repositories. Up until recently this has turned out fairly ok, and certainly never prevented me from using my computer.   

Last week though I finally ran into an issue. The first issue I noticed was with zathura, my pdf reader, not being able to display pdf's. Since it had been a few days since I had rebooted, and other PDF readers were working fine I decided to ignore it until the end of the day and see if the problem persisted after a reboot. The reboot indicated that there was a bit more of an issue as it hung right before my display manager started. As a bit of background - I am running what started out as bog standard Ubuntu 20.04, while I switched to using I3, then AwesomeWM, and now have started playing around with StumpWM, and long ago stopped using Gnome (4GB memory...) I kept GDM. After poking around in logs for a bit from the TTY I decided to install LightDM and fix the underlying issue later.  

Researching the problem became a bit easier when I found that Chrome based browsers would not start, and further that they were encountering the same error as zathura - an issue with libnssutil3.so: version `NSSUTIL_3.59` not found as being requested by /usr/local/lib/libnss3.so. After reinstalling libnss3 and everything related to it I decided to run `ldconfig -p | grep libnss` and noticed that I had both a `libnss3.so (libc6,x86-64) => /usr/local/lib/libnss3.so` and a `libnss3.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libnss3.so` (as well as the copies that Firefox and Thunderbird use) but that I only had a copy of libnssutil3.so in `/usr/lib/x86_64-linux-gnu` After getting rid of `/usr/local/lib/libnss3.so` my system started working as normal. 

Next I decided to try and work out where the copy of libnss3.so that was causing the problem came from. Apparently it was installed by an update of google-chrome-stable that I got from their PPA. What is odd is that I have not found anyone else encountering similar issues.  



