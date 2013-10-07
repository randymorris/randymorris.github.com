---
title: I Made a Thing
tags: ideas
layout: post
---

I wanted to dig into some new (to me) front end web technologies and
tools so I made [a thing][0].

Have you ever happened across a new library or an interesting blog
post and wanted to know what other people think?  I seem to do this
all the time and finding discussions about a random website isn't
always as quick as I'd like.  I wanted something that would search
both [Hacker News][1] and [Reddit][2] for me and give me links to the
latest discussions about whatever it is I'm reading.  Now I have it.

## Introducting Spoolio

The whole thing is ridiculously simple.  Paste in a url, it returns
links to discussions.  It does everything in JavaScript and stores the
results in localstorage so there is no server portion.  This means
there is no login, no users, not much of anything really.
Unfortunatley using only JavaScript also means that the title shown is
just a title from one of the submissions rather than the actual title
(damn you security).

I tried out [Yeoman][3], [Grunt][4], and [Bower][5] for the first
time.  Right now I think it's a little much for me but if I took a
little more time I think I could get more used to it.  Don't look at
the source if you're familiar with these tools.  I got really lazy and
didn't finish making things work properly so there are artifacts
everywhere.

One thing I would be interested in is any feedback on the tiny bit of
[Angular][6] code.  This is my first foray into the wonderful world of
JavaScript frameworks as well and at this point it feels a little
awkward.  I like it, I just feel like I'm doing something incredibly
wrong.

Either way, [give it a try][0].  I don't really expect anyone to use
it but it's there if it helps anyone.

[0]: http://spoolio.bitbucket.org/
[1]: http://news.ycombinator.org/
[2]: http://reddit.com/
[3]: http://yeoman.io/
[4]: http://gruntjs.com/
[5]: http://bower.io/
[6]: http://angularjs.org/
