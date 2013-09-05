---
title: "SVN Diff and Vim"
tags: vim svn
layout: post
---

Now that I'm starting to really get used to using svn for all my config
files and web dev work, I've noticed I use the command `svn diff` a lot.
By default this outputs a unified diff to stdout if any differences are
found.  While this is good information to have, it's a really sucky way
to display it -- especially when we have tools like `sdiff` and
`vimdiff` at our exposure.

`sdiff` simply takes the two input files and prints them out side by
side with changes noted as characters in between the files.  While this
is much much better than the standard output of svn diff, `vimdiff` is
still a better alternative because of it's syntax highlighting.

`vimdiff` (or `vim -d` if you so choose) opens up vim in diff mode.
This mode by default is two vertical split screens with one file in each
screen.  As usual, vim does some highlighting magic to make the output
pretty and more meaningful.  It also has a few commands to make your
life easier when merging two versions of the same file (read up on `do`,
`dp`, `:diffget` and `:diffput`).

Anyway, on to the point.  To set up svn to use vimdiff as it's default
output you've got to do a few things.  First, you need to create a
wrapper around vimdiff.  This is because of the way svn calls the diff
utility, as far as I know there is no way around it.  My vimdiff wrapper
is below.

file: `~/bin/svnvimdiff` {% highlight bash %}
exec /usr/bin/vimdiff ${6} ${7}
{% endhighlight %}

After that, you need to do one of two things:

 1. Create an alias that calls your vimdiff wrapper: {% highlight bash %}
alias svndiff="svn --diff-cmd=$HOME/bin/svnvimdiff diff"
{% endhighlight %} OR

 2. Edit `~/.subversion/config` to have the following lines: {% highlight bash %}
[helpers]
diff-cmd = /home/[username]/bin/svnvimdiff
{% endhighlight %}

