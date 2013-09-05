---
title: "Ctrl-C is not Escape"
tags: rant vim
layout: post
---

I'd like to think I'm not one to be pedantic about things, but there's
one common misconception that has been making the rounds that annoys
me to no end.  `Ctrl-c` is not equivalent to `Escape`.  There are two
key differences that can be demonstrated by the following two
snippets.

<p class="text-danger"><strong>Ctrl-c skips any pending insert mode abbreviations.</strong></p>

In a vim session type the following:

{% highlight vim %}
:iabbrev teh the
{% endhighlight %}

This is a common misspelling and an oft used abbreviation.  Now enter
insert mode and type `teh<Space>`.  Notice that the space completed
the abbreviation and it now says `the` instead of `teh`.  Now do the
same but instead insert `teh<Esc>`.  The abbreviation still happens.
Do the same with `teh<Ctrl-c>`.  The abbreviation is not completed.

<p class="text-danger"><strong>Ctrl-c does not fire the InsertLeave autocmd event.</strong></p>

Dump the following snipped into "cursorline.vim" and launch vim with
"vim -u cursorline.vim".

{% highlight vim %}
augroup CursorLine     
    autocmd!
    autocmd InsertEnter * set nocursorline
    autocmd InsertLeave * set cursorline
augroup END
set cursorline
{% endhighlight %}

This snippet enables 'cursorline' while in normal mode and disables it
in insert mode.  If you go into insert mode and exit with `Esc` you'll
notice that the cursorline is re-enabled, however, if you enter insert
mode and exit with `Ctrl-c` you'll see that it is never re-enabled.

These two things probably don't seem that important to you, but what
about the developers of the plugins you use?  If you're using a plugin
that relies on either of these two features you're risking some
functionality breaking by using `Ctrl-c`.  If you must use something
other than `Escape`, use `Ctrl-[` instead as these <i>are</i>
equivalent.
