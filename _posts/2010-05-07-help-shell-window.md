---
title: ":help shell-window"
tags: shell vim
layout: post
---

Run this in vim.  The help docs clearly state that vim will never have
this feature.  That sucks.

But, you say, "vim is an editor! Why should vim include a terminal
emulator too?  After all, vim is not emacs."  Here's why:  Because
developing over ssh with vim is currently a pain in the ass.  Sure,
there are plenty of workarounds.  Using gnu-screen to split the ssh
session into multiple shells and/or multiple windows seems to be the
most logical since I already use screen.  Sounds good but it is horrible
in practice...

Consider this situation: I have an ssh session to a server and am
running screen in that session.  

* I have five screens running: irssi, mutt, ipython, zsh, and vim.

* I select vim's screen.

* I split the screen and select ipython's screen.

* I want to read my email so I select mutt's screen.. but mutt can only take up half the window because I've split the window using screen. 

* I close the split screen and read my mail.  

* I want to continue coding so I select vim's screen.

* I also have to split the screen and select ipython's screen. 

That's too many keystrokes for such a small convenience.  I could remedy the split problem by nesting screen sessions, but that only makes the keystroke problem worse, and that's only counting what I'd have to do to view the things I want.  I'm not sure I even know how to resize or move splits with screen without looking it up.

Now consider the same situation if vim had a shell-window. 

* I have four screens running at full size: irssi, mutt, zsh, and vim.

* Inside vim's screen, I create a vim split with my code in one window and the shell running ipython in the other.

* I want to read my mail so I select mutt's screen and get a full screen mutt.

* I want to continue coding, so I select vim's screen and get vim+ipython.

Not only does this simplify the number of keystrokes I have to issue to
jump between a full screen mail client and split vim+ipython, it also
reduces the number of keybinds I have to remember.  I'm already fluent
in selecting, moving, and resizing vim splits.. I shouldn't need to
fumble with two sets of keybinds  to accomplish the same task in screen.

The good news is I'm not the only one who wants this functionality.   In
fact, this is one of the [most popular features that vim sponsors vote
for](http://www.vim.org/sponsor/vote_results.php) (along with other IDE
like features).  There was even [an unofficial
patch](http://www.wana.at/vimshell/) for vim 7.0 that implemented this.
Unfortunately I like to keep my software up to date and am not willing
to run an old vim and lose features I use to get a feature I want.

So what can I do?  There are multiple scripts out there that emulate a
shell inside a vim buffer, [conque](http://code.google.com/p/conque/)
and [vimshell](http://github.com/Shougo/vimshell) to name a few.  These
are OK, but not great.  I applaud the effort put forth by the authors
and hope they can continue to move forward with their projects, however
I don't think these solutions are the answer.

Looks like I need to man up and get my hands dirty -- someone does
anyway.  A native vim solution is the only acceptable solution in my
opinion.  Until I can muster up the guts to dig into the vim source, I
guess I'll just complain to myself.

<div class="alert alert-info">
<b>Update:</b> The author of conque sent an excellent comparison of the
available shell options to the vim_use mailing list.  You can find it
<a href="http://groups.google.com/group/vim_use/msg/22c97ebfd6a978eb">here</a>.
I highly suggest subscribing to both vim_use and vim_dev to find out
tips and tricks you wouldn't otherwise know (if you can handle that
volume of email).
</div>
