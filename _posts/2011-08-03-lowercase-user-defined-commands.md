---
title: Lowercase User Defined Commands
tags: vim
layout: post
---

I've never liked the fact that vim doesn't allow users to define
commands that start with a lowercase letter.  Every time I create one I
end up having to also make a `cnoreabbrev` that lets me use my lowercase
version.  This has the ugly side effect of having text transform as you
type.  It also will make the cursor jump around if you're doing more
than changing the case of things. For example:

{% highlight vim %}
cnoreabbrev ack ack<c-\>esubstitute(getcmdline(), '^ack\>', 'Ack!', '')<enter>
{% endhighlight %}

This allows me to type ":ack " and have it automatically change to
":Ack! " as soon as I press `<space>`.  The text changes automatically
and my cursor jumps to the right two spaces instead of just one.
Obviously this is a small inconvenience but it is an annoying one for
me.

I have come up with a bit of a hacky workaround for this that allows
more transparency and I thought I'd share in case someone out there is
as stubborn as me.  The following function will run a substitution on
the current command line:

{% highlight vim %}
function! CommandLineSubstitute()
    let cl = getcmdline()
    if exists('g:command_line_substitutes')
        for [k, v] in g:command_line_substitutes
            if match(cl, k) == 0
                let cl = substitute(cl, k, v, "")
                break
            endif
        endfor
    endif
    return cl
endfunction
{% endhighlight %}

This function reads search/replace pairs from a global variable you set
in your `.vimrc`.  That global variable looks something like this:

{% highlight vim %}
" note that line continuation is only possible without 'C' in 'cpoptions'
let g:command_line_substitutes = [
    \ ['^ack ', 'Ack! '],
    \ ['^ee \(.\+\)', 'e **/\1*'],
    \ ['^h ', 'vertical help '],
\]
{% endhighlight %}

The last thing we need to do is a single map to call this function
whenever we press `<enter>` on the command line:

{% highlight vim %}
cnoremap <enter> <c-\>eCommandLineSubstitute()<enter><enter>
{% endhighlight %}

While this configuration is a bit ugly, it saves me the inconvenience of
having a bunch of abbreviations lying around and makes the substitution
transparent to me.

I've only been using this for a few hours but I haven't hit any issues
thus far.  If you try this out and have problems or if you know of a way
to simplify it please let me know in the comments.
