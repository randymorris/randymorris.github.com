---
title: Irssi Setup
tags: irssi
layout: post
---

I've had a few questions recently about how I've got my irssi
configured.  Instead of typing it out every time, I'm posting it here.

For starters, I always have irssi running inside a screen session on my
server.  This obviously lets me stay online all the time and reconnect
from any computer with an ssh client.  Very convenient since people
often leave me links while I'm away.  My screen configuration can be
found [here][src].

Irssi Theme: *fear2*, modified by me.  I call it *fear3*.  I'll post it
up if anyone wants it.

Scripts:

* `screen_away.pl` - I could not go without this one -- especially
because I use bitlbee for non-irc chat.  screen_away allows me to go
away automatically whenever I detach from my screen session.  It does
some other nifty stuff too, but this is all I've used it for.

* *nm.pl* - Provides right aligned nicks and random nick colors.

* `adv_windowlist.pl` - Another absolutely necessary one if you are
going to use bitlbee.  Provides a verbose window listing rather than the
default window activity status.

* `bitlbee_*.pl` - All the bitlbee scripts from [irssi.org][sio].  They
each provide a few things that make bitlbee a little more usable.

Without urgency hints, the irssi/bitlbee combo would be useless to me.
Luckily I've taken care of this as outlined [here][urg].

I can say that this configuration is by far the most usable setup I've
ever used for day to day chat.  If you have any comments or suggestions,
feel free to [contact][con] me.

[src]: /dotfiles/screenrc
[urg]: /2008/11/17/1/handling-urgency-hints.html
[sio]: http://scripts.irssi.org/
[con]: /about/
