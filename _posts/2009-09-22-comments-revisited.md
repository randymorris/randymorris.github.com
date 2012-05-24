---
title: Comments Revisited
published: 2009-09-22
tags: vim
layout: post
---

A while back I [posted a tip][1] about how to quickly comment out a block of
lines in vim.  Since then I've gotten even more lazy and found an even quicker
way that involves much less effort on my part.  I think this originally came
from a vim tip that I CBA to find now, so I'm reposting here to spread the
love.

First, add a simple function to do the work:

{% highlight vim %}
" Toggle comments on a visual block
function! CommentLines()
    try
            execute ":s@^".g:StartComment." @\@g"
            execute ":s@ ".g:EndComment."$@@g"
    catch
            execute ":s@^@".g:StartComment." @g"
            execute ":s@$@ ".g:EndComment."@g"
    endtry
endfunction
{% endhighlight %}

This function comments starting at the beginning of the line.  You can modify
this behavior to suit your needs by changing the regular expression.

Next you'll need to set the comment characters for the language you're working
in.  My preferred way is to use autocmds to set these based on the current
filetype.

{% highlight vim %}
" Set comment characters for common languages
autocmd FileType python,sh,bash,zsh,ruby,perl let StartComment="#" | let EndComment=""
autocmd FileType html let StartComment="<!--" | let EndComment="-->"
autocmd FileType php,cpp,javascript let StartComment="//" | let EndComment=""
autocmd FileType c,css let StartComment="/*" | let EndComment="*/"
autocmd FileType vim let StartComment="\"" | let EndComment=""
autocmd FileType ini let StartComment=";" | let EndComment="" 
{% endhighlight %}

That's it!  Optionally (do this, really it's stupid not to), you can add a
keymap to quickly call our function.

{% highlight vim %}
vmap <Leader>c :call CommentLines()<CR>
{% endhighlight %}

Now to use this function, just select a visual block and hit your keymap to
toggle comments on that block.  Voila!

Note: If you need anything more complex than what this tip provides, check out
the [NERD Commenter][2].  Everything I've read about it suggest that it's
excellent.

[1]: /2009/02/12/4/vim-tip-comments
[2]: http://www.vim.org/scripts/script.php?script_id=1218
