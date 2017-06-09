---
author: Charles
categories:
- Fun Stuff
comments: true
date: 2016-10-13T04:43:52Z
link: http://www.bassitone.com/2016/10/12/breaking-out/
slug: breaking-out
title: Breaking Out
url: /2016/10/13/breaking-out/
wordpress_id: 4289
---

Welp, massively overslept again today (even for me it was bad...), but I was able to deconstruct the root cause of it or so I think, hopefully tomorrow will be better.  On a completely unrelated note, are 20 foot lightning cables a thing?  I might need to get one...  As I mentioned yesterday, I did manage to get back into the technical swing of things today even despite the setback.  After who even knows how many months, I finally have my VCSA set up again.  I had it last spring and worked perfectly, but somehow between then and now it stopped working.

What's a VCSA?

In short, it's a server that controls other servers at the hardware level.  Except none of the servers it controls are physically _there_; in fact, they all live on the same actual server I've got here and share resources and all that.  Yeah, even the VCSA is virtual.  So I have a virtual machine controlling other virtual machines and the hardware they all run on and now my head is spinning from going in circles.

Weird, isn't it?

Come to think of it, maybe having the vCenter server as a virtual machine on the same host it's managing isn't such a good idea...  Until I can find something with the resources to hold it and only it (and not destroy my power bill) it's the best I can do though.  Virtualization as a thing is weird, but it's incredibly useful.  Namely I can now spin up all the test machines I want, be they for hosting a wiki where I document all I've done (make it publicly internet-facing?  That'd be an interesting challenge), machines to administer as I become a modern-day master of puppets...or serve as a target range where I can harmlessly hone my hacking abilities whenever I want!

If I'm not breaking something (or trying to break something), I'm not learning.  After all, break things now so I know what **not** to do when I'm getting paid to do this stuff and people care about uptime.



* * *



Speaking of breaking things, I got to do a bit of that tonight as well!  The Computer Security Association here at UTSA decided to host their first CTF of the semester on short notice tonight.  For the uninitiated, a CTF is basically a real-life video game.  You compete against a field of others to solve various challenges, technical or otherwise.  Tonight was the classic version of a CTF where the goal was to claim ownership over a machine that the leaders of the club set up for the purpose.

How do you claim ownership?  **By hacking in of course!**  And then putting your handle in a designated file somewhere on the machine.  Technically, this wasn't my first ctf...but it was the first one where I knew even an inkling of what I was doing.

I even managed to completely own two of the servers they had set up, giving myself NT/SYSTEM (the absolute highest level of access you can possibly have on a Windows machine) and grabbing hashes...but I couldn't find the "flag" file to put my handle in it!

Face, meet palm.

As I was packing up, I was discussing with one of the admins what I had missed.  Turns out I was looking for an IIS web root (because hey, it's Windows after all), when the machines were running Apache httpd.

On Windows 2000.

_WHY?!_

Lesson numero uno tonight: **you know what they say about assumptions...**  Aka nmap does service discovery for a reason.

La deuxième leçon:  (YEAH, FRENCH.  DEAL WITH IT) **ms08_067_netapi is a handy exploit... but maybe not when your competitors keep crashing the smb service**.  True story.  I'd kinda like to see how many concurrent attempts at that particular exploit there were tonight.  All I know is, my sessions kept dying with the smb service.  There are other ways to get in.  Leave the easy mode for the guys even newer than you.

Die dritte Lektion: (German, too!) **always carry a decently-long Cat 5 (6?) cable that you know is good.**  They can have all the switches and virtual machines they want, but it doesn't matter if you keep pulling bad cables from their crate of them.
