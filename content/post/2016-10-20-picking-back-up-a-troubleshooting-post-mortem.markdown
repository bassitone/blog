---
author: Charles
categories:
- Projects
comments: true
date: 2016-10-20T04:23:12Z
link: http://www.bassitone.com/2016/10/19/picking-back-up-a-troubleshooting-post-mortem/
slug: picking-back-up-a-troubleshooting-post-mortem
title: 'Picking Back Up: A Troubleshooting Post-Mortem'
url: /2016/10/20/picking-back-up-a-troubleshooting-post-mortem/
wordpress_id: 4311
---

Well that was annoying.  Spent my writing time yesterday evening and then today sorting out what I thought was a weird DNS forwarding issue that made it look like the site was down for the count.  After an email to my web host I thought maybe it was something with the settings - technically, I've got three potential sources for DNS to be screwy on this site.

I should explain first.  You know how you can type in actual words to go to websites?  That's really just a label for the actual physical address where the website can be found (well, more properly, the computer hosting the website, but I'm trying to keep this as simple as possible).  Mapped to the physical world, it's not dissimilar to calling the White House another name for the address 1600 Pennsylvania Avenue, Washington, DC, etc etc.  DNS is the way these friendly labels are tracked and matched to the Internet Protocol address of the machine hosting whatever can be found at it.  It gets a lot more complicated than that - I've had no fewer than two courses on the topic while here at grad school - but that's the general gist.

Anyway, I've got three different places that this matching can get screwed up.  The hosting company I pay for the space to keep this thing up and running has their own addresses.  The company I buy the domain name (that "friendly" label) from has their own as well.  Finally, I use a popular infrastructure service to beef up the security of this site by routing all traffic to it through their network; they have a much better security organization than I could ever run on my own.  All three places have their own addresses, and guess what - they all must correspond.

Again, trying to keep this simple enough to explain how I've spent my day.  In short, all this complexity is added because we like to use names for things instead of just sets of numbers.  One could even enter the particular set of numbers corresponding to the web server and get there directly, bypassing the need for DNS entirely (although God help us all if we ever go full IPv6 - remembering and typing those addresses in is a pain I wouldn't wish on my worst enemy).  And so it was that I determined that there wasn't actually anything wrong with the site itself.  Not really, from a "I'm a system administrator" angle anyway.

Next step was to check those three different places that it could've gotten messed up - site was still up, so it _had_ to be a DNS issue...right?  I was mystified to find that, to the best of my knowledge, the settings were correct!  Just as I was about to get on three different support chats at the same time, it hit me that I missed a step.

The whole time, I was using the same browser - Vivaldi on <del>OS X</del> macOS Sierra.  In theory, it's based on the same engine that Google Chrome and the like use, or so I've read.  Something in it though was causing it to believe that it was right and the internet was wrong when it came to the address of my website!  Testing in other browsers revealed this issue.

Huh.  I had always considered the browser to be strictly for layers 5-7 in the OSI model (that is, your user session, how information is presented, and how you actually use it).  DNS and actually getting pages works at a lower level than all of that.  As it turns out, I guess the Chromium engine does some caching anyway.  Why?  You'll have to ask the devs.

You learn something new every day!
