---
title: CtrlP - A Game Changer
tags: vim
layout: post
---

Recently I was searching for a fuzzy-finding plugin to make working with
projects a little easier.  I [posted a quick hack][0] that I still use
every now and then, however I've recently discovered a rather new plugin
called [CtrlP][1].

[0]: /2011/08/01/poor-mans-fuzzy-finder.html
[1]: https://github.com/kien/ctrlp.vim

For the uninitiated, fuzzy-finding plugins allow you to open a file by
only typing enough pieces of the path to uniquely identify a file.
Sometimes this is as little as one or two characters.  I wasn't really
sold on this behavior until I tried using them at work where we have
many files with similar names.  A plugin like this makes dealing with
such situations much easier to deal with than tab-completion alone.

CtrlP is written entirely in vimscript.  This is a big plus for me
because many of the machines at work aren't built with +python or +ruby
which [some][2] [of][3] [the][4] other fuzzy-finding plugins require.
Although it's written in vimscript it caches directory and filenames for
larger directories and can be configured to always use a cache. This
means it's quite slow on first launch in larger directories but is very
fast on subsequent calls.

[2]: https://github.com/jamis/fuzzyfinder_textmate/
[3]: https://github.com/sjbach/lusty/
[4]: http://wincent.com/products/command-t/

Another big plus is the configurability CtrlP offers.  There are (currently) 22
options provided to configure everything from mappings to how caching should
work.  You can even delegate the file indexing out to a faster external
mechanism if you so choose.

Couple all of this with an active and responsive developer that provides
excellent documentation and you've got my current favorite script.
