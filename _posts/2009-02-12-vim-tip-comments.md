---
title: "Vim Tip: Comments"
tags: vim
layout: post
---

<p class="alert alert-warning">
<b>Heads up!</b> I've posted a follow up to this tip that details a
quicker way to comment in vim by using a simple function.  Check it
out <a href="/2009/09/22/comments-revisited.html">here</a>.
</p>

From the "holy crap why didn't I find this before" category...

When editing in vim, if you find you need to comment out a block of
code, try the following:


1.  Jump to the start of the line at the top or bottom of the block
2.  Press `Ctrl+v` to enter Visual Block mode
3.  Navigate to the end of the block.  You'll notice only the first column is highlighted (for the most part)
4.  Press `I` to enter Insert mode before the first non-blank character on the line
5.  Type whatever the comment syntax is for your language, eg. "//"
6.  Press `Esc` to get back to Normal mode.


You can follow similar steps to uncomment the same block,`Ctrl+v` to
highlight the comment characters followed by `x` or any deletion command
to remove the comment.
