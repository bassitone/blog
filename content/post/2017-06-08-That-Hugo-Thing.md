---
categories: 
 - Programming 
 - Projects
date: "2017-06-08T22:22:07-05:00"
description: "I overhauled my blog again.  This time, to something called Hugo"
thumbnail: ""
title: "That Hugo Thing"
author: Charles

---

I've used WordPress for years.  Since back in the 2.x days, even.  I love it, still recommend it, and generally support everything they're doing, but it's quickly outgrown what I need.  Truth is, y'all, I'm really _not_ doing enough with the site to call for a dynamic php-based solution.  Fact is, WordPress plugins have a rather hilarious number of vulnerabilities; as a cybersecurity professional, minimizing my attack surface is an ongoing .  In addition, WordPress is - as mentioned previously - dynamic.  It's running a lot of code to do a lot of things that I don't really need it to do.  It is possible to run a forum, an ecommerce site, and more on WordPress.  Are there better solutions to do so?  Of course there are - and yet, I have built sites that do all of this.  Apparently, some people even put such sites into production!

Anyway, enough about WordPress.  I am now using something called **[Hugo](https://gohugo.io)**.  It's what is called a "static site generator".  That's right - the site is just good old text, html, and CSS now!  That means it's much   better at performance on the web and a bit easier to maintain once I get the hang of it.  I won't tempt fate by saying it's "hack-proof" - there is _no such thing_.  Someone, somewhere out there, would take that bold declaration as a challenge.  That said, there are some fairly big advantages to this architecture already.  Namely, there's no admin panel to try and bruteforce logins to.  Rather, I have had an opportunity to play with some interesting technology as a part of this process.

Technologies I have been curious about when talking to my software developer friends.  Specifically, Hugo is written in Golang.  I had wanted to go with _Jekyll_ for the experience with Ruby - there is a point in my career that I would like to contribute to certain projects using Ruby - but Go has been another language on my radar.  I have also gotten to finally - _finally!_ - tinker with CSS 3 on a more than superficial level.  I am using, as an astute reader of this site may notice, a premade theme for the site; however, I was able to successfully make a number of tweaks to the stylesheet that the theme's creator provided in order to better suit my preferences.  Specifically, the accent colors have been changed from a shade of red to the blue, and the title of the blog used to be in all caps.

I hate all caps outside of very specific circumstances.

Moving on, I have also gotten it set up such that I can write a post on my laptop, type a couple commands with ``git``, and see my post automatically show up on my blog with the power of SSH and a neat Continuous Integration/Continuous Delivery platform called [Wercker](http://www.wercker.com).  CI/CD is apparently all the rage these days, and I should be familiar with all the things I might come across in my line of work, shouldn't I?

There are surely some kinks to be worked out still - there always are.  In fact, **I've already found one** - CSS needs to be tweaked to show italics.  But in any case, welcome to the new site!
