---
title: "Changing My Work Flow: Adding Emacs"
published: 2012-03-07
tags: emacs
layout: post
---

<p class="alert alert-warning">
   <b>Disclaimer:</b>
   I'm new to the Emacs community so some of the following terminology
   may be incorrect.  Please correct me if there is a more proper way to
   describe anything I've mentioned here.
</p>

Over the past few months I've realized that I am far too easily
distracted from my tasks at work.  After a little thinking I came to
the conclusion that part of my problem was my work flow.  I generally
had two or three terminals up bouncing around virtual machines and
servers so I could test as I worked and inevitably I would end up on
my home server chatting away on IRC for large chunks of time.  While
most people may be able to correct this with a little discipline, I've
decided to try something different.  One of my coworkers recently made
the switch to Emacs and since I've always been curious about the
features touted by Emacs users I thought I'd give it a try too.  I
instantly saw a huge difference in my focus and concentration.

Because the driving force behind this change was focus, I have tried
to stay away from the typical "Emacs can and should do everything"
point of view.  There are really only two main features that I've been
using that go above and beyond a text editor: *ansi-term* and *TRAMP*.

# ansi-term

As the name suggests, ansi-term is a terminal emulator that can be run
inside Emacs.  It works almost like any other buffer so moving between
normal buffers and the terminal is virtually seamless.  This is
something I wanted in vim for ages, I even [ranted about it][10] here
once before.

While it's possible to open multiple instances of ansi-term, I have
limited myself to only having one running at a time.  This has helped
me concentrate on one task because I am no longer hopping between
different terminals with different ssh sessions running.  One
terminal, one task.  Having a terminal in the editor also allows me to
do all my scm tasks without leaving Emacs as well, without having to
use some fancy git/svn/whatever mode.  I just use the normal command
line interface I'm used to.

# TRAMP

TRAMP is a really poorly constructed acronym for "Transparent Remote
(file) Access, Multiple Protocol".  Where the acronym lacks, the
execution excels.  For you vim users, TRAMP is what netrw really
should be.  I am able to "transparently" edit files on servers without
being nagged about passwords or temp files every time I make a change.
This is very convenient for me as I do my development almost
exclusively on one of our dev servers.  I no longer have to choose
between opening an ssh session and editing with the remote editor or
using sshfs to mount the remote filesystem locally to get a decent
editing experience.

The most important part about TRAMP and ansi-term is that it's rather
easy to make them work together.  Using a tip from the [EmacsWiki][20]
I added a few lines to my bashrc to allow `C-x C-f` to automatically
open up in TRAMP format in the `$PWD` of the remote machine I'm
connected to in ansi-term.  This speeds up the process of opening
files considerably and is pretty much on par with how I worked with
vim previously.  The stripped version I use is below.

{% highlight bash %}
function set-eterm-dir {
    echo -e "\033AnSiTu" "$LOGNAME"
    echo -e "\033AnSiTc" "$(pwd)"
    echo -e "\033AnSiTh" "$(hostname -f)"
    history -a
}

if [ "$TERM" = "eterm-color" ]; then
    PROMPT_COMMAND=set-eterm-dir
fi
{% endhighlight %}

Adding this to the remote machine's bashrc will enable TRAMP to follow
the working directory in ansi-term.

# Other benefits

There are a couple of features that I would like to dive in to
eventually but haven't looked too much at yet.  Having a true
programming language at my disposal ([elisp][40]) when customizing my
editor is **very** appealing after spending years of dealing with
vimscript.  I also would like to look in to Org-mode as it may be
another tool to help keep me on track at work.

# Moving forward

Adding Emacs to my work flow has been great for my development tasks
but I'm not ready to move on completely.  I fully intend to continue
using vim when I'm logged on to a test or production machine, and
really any time I'm not doing development.  I have been using this
work flow for the past couple of weeks and it seems pretty natural to
me now other than the occasional `C-x s` or `C-x f` while in vim.

If you have any questions or suggestions feel free to ping me in the
comments or in the usual places.  Feel free to watch my [.emacs.d][30]
grow as I continue to go through this process.


[10]: /2010/05/07/help-shell-window.html
[20]: http://www.emacswiki.org/emacs/AnsiTermHints#toc4
[30]: https://github.com/rson/emacs.d
[40]: http://en.wikipedia.org/wiki/Emacs_Lisp
