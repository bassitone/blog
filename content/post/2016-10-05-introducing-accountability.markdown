---
author: Charles
categories:
- Programming
- Projects
comments: true
date: 2016-10-05T01:34:56Z
link: http://www.bassitone.com/2016/10/04/introducing-accountability/
slug: introducing-accountability
title: Introducing Accountability
url: /2016/10/05/introducing-accountability/
wordpress_id: 4265
---

And now for something completely different: I promised y'all yesterday that I'd talk a little about the program I'm writing to help keep myself on track as well.  Accountability is your binary accountability buddy.  I'm building it using Flask and Python 3.  Really, it's a small thing and Flask is probably overkill for it, but email is hard.

Yes, email.  Sure, it's just SMTP and MIME under the hood, but getting it to be reliably delivered is a big problem.  It's also more or less a solved problem if you've got the money, but who wants to fund email-as-a-service for a dinky little webapp with a user count of 1?  Not me!

Why even make it a webapp?  <del>For the memes, of course!</del>  Because I might as well stretch myself all the way, and this'll be running on a server somewhere anyway in order to get around the "oops, I turned off my computer" problem.  Might as well make my own terrible webapp, because why not?  If it goes well, I might have something bigger in the works...

But what does this thing even do?  Well, in short, it will wait, patiently, for me to do something - post on here, another place, click a button, what have you.  If I don't on a given day, it'll send a gentle email to remind me to do it.  If I happen to ignore it and skip **another** day?  A slightly stronger email reminder.  Miss a third time?  Strongly-worded email to me **and** to a designated accountability buddy (IRL) to get me back in shape.

And that's just the 1.0 target!
