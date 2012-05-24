---
title: Me vs. GNU Screen
tags: gnu-screen
layout: post
---

I have beaten [gnu screen][gs] into submission.  For ages it has refused
to let me start with screen number 1 instead of 0.  Binding `c` to
`screen 1` was supposed to fix this.  The cause? My fingers were too
fast.  Turns out that I need to also bind `Ctrl+c`.  For your
convenience, copy and paste the below into your _~/.screenrc_ if you
have a similar problem.

{% highlight text %}
bind c screen 1
bind ^c screen 1
bind 0 select 10
{% endhighlight %}

[gs]: http://www.gnu.org/software/screen/

