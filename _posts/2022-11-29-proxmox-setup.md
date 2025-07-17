---
title: Proxmox Setup  
date: 2022-11-29 13:41:00 -0500  
categories: [proxmox, linux]  
tags: [linux]       # TAG names should always be lowercase
toc: false  
---

# I installed Proxmox...

The installation went fairly smoothly, other than a 'Layer 1 issue' involving my head and my desk while plugging in the ethernet. I also ended up being a bit indecisive about my IP addressing scheme and needed to edit /etc/network/interfaces and /etc/hosts. So far so good.   
![proxmox](/assets/img/post/proxmox.png){: w="700" h="400" }
_It's alive!_

    
## ...now what?

I have been considering getting the Red Hat Certified System Administrator as a required step towards the Kubernetes and OpenShift certifications Red Hat offers. That means spending some time with yum instead of Apt so I downloaded Alma Linux to start exploring. I ran into an issue with the default CPU choice - kvm64 (an abstraction designed to facilitate moving VMs between machines) Switching to using the machines CPU cleared up the issue. Luckily this is a known issue and didn't take me long to figure out.

Playing around with the new install made me regret putting off setting up stow or some other way of quickly installing my dotfiles... 

## Containers within containers within containers....

Since I know I am going to want to run Docker containers I have a bit more setup to do. Going by the Proxmox forums there are a few ways people do this. Having the Proxmox host run Docker directly seems like a bad idea, even though my janky little birdy lab is far from a production environment I agree. Since I am trying to keep within my memory budget just setting up a VM just to run application containers is counterproductive, though this is the approach that I thought of first and is the commonly recommended way of doing things.  So it seems like I need to find a LXC container to run my application containers.  
A few minutes on DDG and I came across [TurnKey Linux](https://www.turnkeylinux.org) who used to offer a LXC container that includes a a collection of tools that might be useful. It turns out they even make a template available - that has not been updated in several years and no longer appears in the list of downloadable templates. There focus seems to be more on AWS right now so I will keep them in mind for when I am spending time on Amazon's cloud.
I also found some instructions that informed me that feline based data recovery is not ready for production, but also had [Running Docker in LXC With Proxmox 7.1](https://www.weisb.net/running-docker-in-lxc-with-proxmox-7-1/) looks simple (back when I was first getting into Linux you needed to patch your kernel by hand on punch cards uphill in the snow...) and in a few minutes everything is up and running. Almost anti-climactic.

## Final Thoughts

The temptation is just to start fooling around and once I get something that works keep it until something goes wrong.... Luckily I plan to upgrade my hardware soon enough that I know I am going to need to redo this soon, so I am going to want to document everything with an eye towards writing a script or Ansible playbook for future installs...  

*To be continued*
