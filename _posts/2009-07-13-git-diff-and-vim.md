---
title: "Git Diff and Vim"
tags: git vim
layout: post
---

Now that I've seen the light and begun using git instead of subversion,
I thought I'd post a follow up to my [previous post][0] about using
vimdiff with subversion.  That has by far been the most popular post on
this site, so hopefully this will reach and help some of my fellow git
users out there.

Setting up git to use vimdiff is virtually the same as with subversion.
You need a vimdiff wrapper, and you need to tell git to use that wrapper
as the diff program.  First, the wrapper, *gitvimdiff* (anywhere in your path):

{% highlight bash %}
exec /usr/bin/vimdiff ${2} ${5}
{% endhighlight %}

After that, just need to edit your *~/.gitconfig* file:

{% highlight ini %}
[diff]
  external = gitvimdiff
[pager]
  diff =
{% endhighlight %}

Big thanks to [Jonathan Palardy][1] for the info, I've just reproduced
it here to help spread the word.

[0]: /2008/12/22/3/svn-diff-and-vim.html
[1]: http://technotales.wordpress.com/2009/05/17/git-diff-with-vimdiff/


