---
title: Docker Networking Issues
date: 2023-01-21 
categories: [technology]
tags: [networking, linux]
---

# Docker Networking Issues 

As part of my ongoing campaign to develop marketable skills I decided to spend some time learning PostgreSQL. The simplest way to get up and running seemed like it would be to use Docker to run the database in a container, this would also let me move to running it on a different computer if my 10+ year old Ubuntu 20.04 laptop wasn't up to running the database and whatever else I end up connecting to it...  
And of course a recent update seems to have created issues for Docker, I start the container and start up the GUI client (DBeaver CE) I installed, and quickly notice that I am no longer connected to my home network. After the usual attempts to work out what is going on using Duck Duck Go and random poking at log files, I found the solution in [this post](https://stackoverflow.com/questions/62176803/docker-is-overriding-my-default-route-configuration) on stackoverflow. Apparently it is enough of a known issue that a line to prevent the issue is included in the config file /etc/connman/main.conf (commented out)  

Now, instead of SQL I am spending the rest of the day studying how Linux networking works (this issue might tie in with some of the issues getting networking on my new Proxmox server working correctly)

