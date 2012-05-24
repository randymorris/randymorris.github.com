---
title: "Emacs Update"
tags: emacs
layout: post
---

I figured it's about time I post an update regarding my emacs journey now that I've had some time to acclimate myself to a new way of thinking.  This is not so much a blog post as it is just a couple of lists showing where I am in my comfort level with emacs thus far.

## Things I like:

Modes
:   I never thought I would say it but emacs' modes have finally grown on me.  It took a while to get used to but I get it now.

package.el
:   Emacs 24 comes with a built-in package manager for adding additional features from multiple sources.  This is similar to [Vundle][1] or [vim-addon-manager][2] except it comes bundled with emacs.

elisp
:   As much as I may suck at it, I really love elisp.  As I learn more and more about lisp I'm starting to believe that elisp is the only exposure I'm going to get to lisp programming in the real world.  It helps too that vimscript is just <i>awful</i>.

The yank ring
:   There is a [plugin][6] to emulate this in vim but I never really gave it a chance. My only gripe is that it stomps all over my beloved tmux escape key.

Narrowing
:   Again, this is available in vim with a [plugin][5].  This is something I never tried at all because I thought it was useless.  Now that I'm fumbling around in emacs it's nice to be able to focus only on a small portion of code at a time if I'm making sweeping changes.  I don't have to worry about accidentally changing code I didn't mean to.  I'm sure there are better uses for this but right now that's where it's helped me out.

## Things I don't like:

Ctrl-U
:   This may just be me being stubborn.  I can't stand that for many interactive commands I can/have to change their behavior by passing a prefix argument. I'd much rather just have a different binding for the different behavior.

## What you can help me with:

Semantic blocks of text
:   I touched on this in my previous post but it's still a sore point for me.  In vim these were called text-objects and they were the number one feature for speeding me up.  The [expand-region][3] script has made this a little less of a problem but I'm still up for hearing better ways of doing things.

I've left lots of things off but I think these sum up my current status pretty well.  I'm always looking for tips on things I should try, especially on things that aid in navigating around code more quickly.  If you have any suggestions please let me know.  As always, my current configs can be found on [GitHub][4].

[1]: https://github.com/gmarik/vundle
[2]: https://github.com/MarcWeber/vim-addon-manager
[3]: https://github.com/magnars/expand-region.el
[4]: https://github.com/rson/emacs.d
[5]: https://github.com/chrisbra/NrrwRgn
[6]: http://www.vim.org/scripts/script.php?script_id=1234
