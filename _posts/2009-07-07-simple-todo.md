---
title: "Simple Todo"
tags: shell
layout: post
---

[Jelly][0] in the archlinux irc channel asked for suggestions for a cli todo
app, and I offered this to him on a whim.  As it turns out, it's
actually pretty damn useful.

{% highlight bash %}
todo()
{
  if [ -z $1 ]; then
    cat $HOME/.todo
    return
  fi

  case $1 in
    "add")
      echo $2 >> $HOME/.todo
    ;;
    "del")
      todo=$(< $HOME/.todo | sed 's/'$2'//;tx;p;:x;d')
      echo $todo > $HOME/.todo
    ;;
  esac
}
{% endhighlight %}

You can also find this in my [zshrc][1] on [github][2].

Edit:  rich_o on the archlinux bbs [posted][3] a modification to this
which allows you to delete tasks by number and search for a task.  I've
began using this mod instead:

{% highlight bash %}
todo()
{
  if [ -z $1 ]; then
    awk '{ i += 1; print i": "$0 }' $HOME/.todo
    return
  fi

  case $1 in
    "add")
      echo $2 >> $HOME/.todo
    ;;
    "del")
      todo=$(< $HOME/.todo | sed "$2"'d')
      echo $todo > $HOME/.todo
    ;;
    "search")
      grep -ni --color=never $2 $HOME/.todo | sed -e 's/:/: /'
    ;;
  esac
}
{% endhighlight %}

[0]: http://vdwaa.nl/
[1]: https://github.com/rson/dotfiles/blob/master/zshrc
[2]: https://github.com/
[3]: http://bbs.archlinux.org/viewtopic.php?pid=590871#p590871
