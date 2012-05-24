---
title: Handling Urgency Hints
tags: gnu-screen irssi
layout: post
---

Recently I found myself getting tired of [Pidgin][pg]'s multi-window
interface and began searching for alternatives.  Because I'm already on
IRC all the time anyway, I decided to take a shot at [Bitlbee][bb].
Bitlbee takes all the useful features of Pidgin and sticks them in a
familiar IRC-ish interface.  The only annoying part was that the message
notification Pidgin gave me was gone -- no more color changing
tags/taskbar.  Enter urgency hints.

I'd played with them before when hacking on dwm.  In fact, I added this
feature to my dwm because of Pidgin in the first place.  My challenge
now was to get irssi to pass the hint to gnu-screen, to pass the hint to
urxvt over an ssh session, to pass it to my window manager.  This was
suprisingly easy.  Three configs are involved: *~/.irssi/config*,
*~/.screenrc*, and *~/.Xdefaults*.  Additions are shown below.

* *~/.irssi/config*

{% highlight javascript %}
settings = {
    "fe-common/core" = {
        beep_msg_level = "NOTICE MSGS HILIGHT";
        bell_beeps = "no";
    };
};
{% endhighlight %}

* *~/.screenrc*

{% highlight text %}
vbell off
bell_msg '^G'
{% endhighlight %}

* *~/.Xdefaults*

{% highlight text %}
urxvt*urgentOnBell:    true
{% endhighlight %}

With these three settings, I now get a nice [notification][ss] when
receiving a message in Bitlbee or irssi.  This has a nice side effect
too.  Many cli apps can send a bell when they need your attention.
Mutt, for instance, can now notify you about new mail.

[pg]: http://pidgin.im
[bb]: http://www.bitlbee.org
[ss]: /static/img/screenshots/2008-11-24-211910_1680x1050_scrot.png
