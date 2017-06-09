---
author: Charles
categories:
- Projects
comments: true
date: 2016-10-24T03:35:53Z
link: http://www.bassitone.com/2016/10/23/lessons-learned-from-my-first-site-move/
slug: lessons-learned-from-my-first-site-move
title: Lessons Learned from my First Site Move
url: /2016/10/24/lessons-learned-from-my-first-site-move/
wordpress_id: 4317
---

Good evening, y'all.  Notice anything different?  Anything at all?  About 90% of the changes this weekend were behind the scenes, but the more savvy of y'all - or those with a good eye - might notice a thing or two.  (NB: those of you who get these posts in a feed reader might need to visit the site itself to find them)

My main project this weekend, other than forensics homework of course, was moving this site to a new web host.  Nothing's wrong with the other one, they're good for what they are, and I still like them, but quite simply I was outgrowing what they could give me.  Namely, I have started building some interactive webapps that I'd like to put out there - after all, if I'm going to spend time coding something, might as well use it, right?  Quite simply, I doubt they would have allowed me to upload and run my own code.  Doing so requires a far greater level of access than should be typical for a standard shared web host.

At least, I wouldn't be comfortable letting random people put arbitrary things on my server for $10/month.  Since practicing what I preach is a thing I'd like to do more of, let's go with it.  Of course, unless either this blog or one of my little webapps takes off and becomes the Next Big Thing, it's also cheaper.  That helps too.

The price of this increased freedom?  Well, as _Spiderman_ put it so eloquently, "With great power comes great responsibility".  And so it is now - unlike before, where the server was run entirely by the company and ultimately shared and parceled out among who knows how many others, this one is _mine_. Okay, well, technically it's owned by the company I pay for the privilege and still exists more or less at their whim, I have that far greater degree of control over it that I'll need going forward.

As far as this particular server goes, I am God.

And I am responsible for whatever happens on it.  For securing it, making sure it keeps running, all that stuff.  That prospect kinda scares me, to be honest.  I'm still very new to this whole profession.  In theory I know what to do...but this is really the first I'm putting it into practice.  Should be fun!

Anyway, I decided on Friday to "freeze" the site as it was and begin the process of moving it to this new server.  Today, after watching it for a full 24 hours, I can say that the process is done.  As done as any of my websites ever are, anyway.  I did notice that Safari on the iPhone might not like the LetsEncrypt certificate quite yet (it's a new authority that has surged in popularity over the past year, really makes this whole SSL thing easy), but other than that it feels rock solid.  The move operation wasn't quite so solid...but I did learn some things!

**1.  No matter how well you plan, things will happen.**  As it turns out, flipping the switch on redirecting DNS queries for bassitone.com and my test domain bassitone.net to the new server when the Internet is on fire isn't such a good thing.  Yeah, that big Distributed Denial of Service (DDoS) attack that knocked a good portion of the Internet off on Friday affected me too.  That was interesting.  And it pushed the timeline back.  Fortunately, this is probably the easiest project I'll ever manage.

**2.  fail2ban works.  Unrelated: Make sure your SSH keys are where you think they are.**  You sysadmin veterans know where I'm going with this...  Yep, locked myself out of my shiny new server just as I was trying to get set up to bring in the content of the site.  Damn it.  Ah well, bonus of this particular solution is that this server is just a virtual machine on a server somewhere in the Bay Area.  As such, it's super easy to wipe and start again.  It's also faster than driving to campus to get a fresh IP address to fix it.  So I did.  RIP server 1.

**3.  Is it really a backup if you've never tried restoring it?**  NO!  No it's not!  Back in July or so (when I finally started caring about this site) I bought a subscription to VaultPress, an awesome service for keeping blogs like this safe and sound.  As it turns out, though, I've never had occasion to actually restore it.  Backing up works just fine, but I ended up just doing the manual process of exporting my stuff from the old site and importing it onto this one.  Not much to it, really, though I did have to set up all my plugins again.  That's annoying, anyway.

**4.  Keep It Simple...**  I've written before about how I use that intermediary service to protect and secure traffic to and from the site.  Just when I thought I was done, that I was out of the woods, loading the site gave me weird HTTP errors.  Specifically, it was error 521.  Lovely.  The 5xx series of HTTP errors generally mean there's something wrong with the server itself.  The specifics though were new to me.  Google to the rescue!  Apparently, that's the code given by that intermediary provider when it gets a "forbidden" response.

Hey Cloudflare, why not just pass the [403 status](https://en.wikipedia.org/wiki/HTTP_403) like the rest of the Internet?  I'm sure they have their reasons, but that would have been helpful...  As it turns out, when I flipped the switch on moving the primary bassitone.com URL over, I needed to add a few lines to the Apache web server's configuration file in order to have things resolve correctly.  First time actually touching Apache2 configuration files, so that was interesting.  Part of the reason I got this server was to learn.

Resolved it...and still error 521.  Again, thank you Cloudflare.  This time, though, the error from CF's side was actually useful.  Disabling the protection momentarily allowed the site to load as expected.  End result was that the CloudFlare network was expecting SSL to be up on the site's side, but it wasn't yet.  For some reason I had put off setting up LetsEncrypt.  Fixed that, re-enabled the protection, and green lights across the board!

My web presence is no longer in the beer leagues.  This will be a hell of a learning experience.
