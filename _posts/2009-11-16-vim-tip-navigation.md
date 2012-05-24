---
title: "Vim Tip: Navigation"
tags: vim
layout: post
---

Have you ever used vim to edit a large file and found yourself setting
marks in a few areas to quickly jump between them?  I have, and I find
it highly annoying to have to remember those marks.  Luckily, vim has a
few tricks up it's sleeve that make jumping around a little faster.

Firstly, see `:help changelist` and `:help jumplist`.  

The changelist (obviously?) stores a list of recent changes to the file.
You can even browse the list with `:changes`.  You can jump back and
forth through the changelist with `g;` and `g,`.

Similarly, the jumplist stores a list of jumps (`:jumps`) that you can
navigate around using `Ctrl+o` and `Ctrl+i`.  

The biggest difference I've noticed here is that the jumplist stores
jumps across files whereas the changelist does not.  Both of these
features may be influenced by viminfo settings, but the default behavior
is quite comfortable.

Have any other tips about jumping between sections of a file?  If so,
[let me know][1].

[1]: /about

