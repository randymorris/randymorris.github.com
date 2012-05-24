---
title: "Shell Tip: Last Argument"
tags: shell
layout: post
---

I'm posting this because I'm tired of forgetting and having to ask this over
and over again in IRC.  Hopefully it will also help someone else speed up their
work flow.

Many people are familiar with the special `$_` parameter that is set to the
last argument of the previous command.  It makes things like the following a
little quicker:

{% highlight text %}
$ echo "foo" > foo
$ mv foo bar
$ cat $_
foo
{% endhighlight %}

I have always stumbled, however, in this case:

{% highlight text %}
$ echo "foo" > bar
$ cat $_
cat: foo: No such file or directory
{% endhighlight %}

The solution is to use the `!$` history expansion rather than the `$_`
parameter.

{% highlight text %}
$ echo "foo" > bar
$ cat !$
cat bar
bar
{% endhighlight %}
