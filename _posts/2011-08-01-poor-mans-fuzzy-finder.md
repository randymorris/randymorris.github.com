---
title: "Poor Man's Fuzzy Finder"
tags: vim
layout: post
---

I recently realized I have been using a very simple replacement for the
[Command-T][0]/[Fuzzy Finder][1] type plugins for quite some time,
however I had never made it convenient for myself to do so.  Today I
pushed a small change to my `.vimrc` that I think will make things a
little easier for me.

{% highlight vim %}
nnoremap <leader>ff :e **/*<left>
nnoremap <leader>fp :<c-p><left>
{% endhighlight %}

The first map allows me to quickly search for a file (by partial name)
anywhere under the current directory using `<leader>ff`.  If there are
multiple files found that match the glob, vim will throw `E77`.  If that
happens I can use `<leader>fp` to load the previous fuzzy-find on the
command line with my cursor where it needs to be for me to make the
search more specific.

Obviously this solution is nowhere near as complete as a plugin
dedicated to this task, however it's as complete as I need it to be.

[0]: https://wincent.com/products/command-t
[1]: https://bitbucket.org/ns9tks/vim-fuzzyfinder/
