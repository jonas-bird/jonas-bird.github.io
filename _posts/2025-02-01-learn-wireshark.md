---
title: Learn Wireshark
date: 2025-02-01 01:01:01 -05:00
categories: [networking]
tags: [networking cybersecurity]     # TAG names should always be lowercase
---

## Note 

There are way to many 'Wireshark Deep Dive' articles that cover the same introductory material (how to capture from your ethernet port, a basic explanation of display filters, and how to follow a conversation). I have no intention of adding to the noise, and am not at the point where I can offer anything better than the current experts. What I am providing is a list of some resources I found helpful, and some advice to people getting started working with Wireshark. 


## Intro 

After spending several months focused on reverse engineering and binary exploitation I decided to dive into 'blue team' topics. While taking on [TryHackMe's](https://tryhackme.com) Advent of Cyber side quests I decided that I while I could use Wireshark, I could also be better with it. 


## Advice 

1. Learn the basics of networking first. While Wireshark can be a useful tool to learn how a protocol works, if you are going to use it in a meaningful way I would expect you to already have a decent amount of theoretical knowledge. By a decent amount I mean Network+/CCNA level. I am sure that with cybersecurity being a hyped field there are people hoping that it is not that hard and they can just 'learn where to click' - I used to teach basic computer skills classes, it didn't work for Excel then and it REALLY can't work for cybersecurity. If you are trying to use Wireshark to get a better grasp of networking, get a copy of a CCNA study guide (it does not need to be the current one, unless you are planning on taking the CCNA), or [TCP IP Illustrated](https://archive.org/details/TCPIPIllustratedVol.1TheProtocols1stEdition)
2. Read RFCs... A good place to start might be [DNS Protocol Related Documents](http://www.faqs.org/rfcs/dns-rfcs.html) since the problem is 'always DNS'
3. Look at a lot of pcaps. Collect pcaps! Healthy traffic, malware generated/C2/IOC filled traffic, your homelab's baseline traffic, Windows traffic, Linux traffic... Especially spend time on boring pcaps. One of the more difficult things to learn through self-study is what business as usual is supposed to look like!  
   Some of the sources for pcaps I have come across:
    + [Netresec links to PCAP Files](https://www.netresec.com/?page=PcapFiles) 
    + https://weberblog.net/the-ultimate-pcap/
    + [Unit 42 from PaloAlto](https://unit42.paloaltonetworks.com/tag/wireshark-tutorial/) put up Wireshark related material with useful pcaps to study 
   **Important: if you are working with a pcap of malware being transferred and extract the file you now have that malware on your computer... Best bet is to use a VM of an OS other than the target one. Unless you know what you are doing and want to detonate the malware and observe its traffic. If you are a malware analyst you are probably not reading this post though.**
4. Use a tool like [Scapy](https://scapy.net) to write scripts that generate packets. You can also try running various exploit in a safely isolated environment (see warning above) to see what the traffic looks like.
5. Take the time to adjust coloring rules, column layout, etc. Most of the books and courses I have gone through start with a guide on setting up Wireshark the way the instructor likes. I found that fairly shortly I started wanting to adjust things (starting with making the coloring rules darkmode friendly) Spending some time building profiles will make using Wireshark a lot faster down the road!

## Youtube Videos

[Chris Greer](https://www.youtube.com/@ChrisGreer) is an expert. He coined the term **Packet Head** and has a huge amount of experience working with Wireshark. His knowledge, enthusiasm (for the topic, and for teaching), and earnest delivery help make the technical topic approachable. 

Unit 42 of Palo Alto has a [video](https://www.youtube.com/watch?v=wNEzfe9RI-I) series that covers some of the basics as well as looking at examples of malware/c2 traffic.

There are probably other great resources out there, but they are hard to find in the sea of bite-sized introductory material 

## Books 

Always [RTFM](https://www.wireshark.org/docs/wsug_html_chunked/) beyond that -  
I can personally recommend [Practical Packet Analysis](https://nostarch.com/packetanalysis3) I have the 2'nd edition and read it cover-to-cover while referring to Chris Greer's videos on each topic for additional information. Conversely I can say Mastering Wireshark put me off buying IT related books. There are a bunch of older books out there, as well as other current books that seem to cover the same basic material. There are also a few security focused books focused on Wireshark that I am still working through - Wireshark for Security Professionals looks good (it includes a lab environment setup), and Tactical Wireshark is also on my list of books to try and find a copy of. 


## Courses 

If you learn from online classes effectively you could do worse than take one of Chris Greer's [courses](https://packetpioneer.com/#section-9-224)
I tend to learn better from books, so I have not surveyed the options available extensively. I have taken David Bombal's [course](https://courses.davidbombal.com), it was decent. If you really need some proof that you have studied the material, than you are probably best off figuring out what will be viewed as the most likely to impress and focus on getting that. 


## Final Thoughts 

Wireshark is one of the most powerful diagnostic tools available to network engineers, security analysts, basically anyone working with a network. 
