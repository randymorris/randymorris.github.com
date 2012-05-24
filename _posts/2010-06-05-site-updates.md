---
title: Site Updates
layout: post
published: false
---

Today I upgraded from Django 1.1 to 1.2.1.  As far as I can tell
everything is working fine, but if you have any issues please let me
know.

I've also added syndication to the site.  Both RSS and Atom are
available, <del>but the W3C validator says the Atom feed is invalid.
Since I'm using vanilla Django feeds, I'm not going to fix it until
Django does</del> and valid.  You can find them at:

<ul class="feedlist">
    <li><a href="/feeds/rss">RSS</a></li>
    <li><a href="/feeds/atom">Atom</a></li>
</ul>

I'm not a feed user so if these don't work for you they probably won't
get fixed unless you tell me how to fix them.
