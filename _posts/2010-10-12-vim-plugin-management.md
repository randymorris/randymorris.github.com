---
title: "Vim Plugin Management"
tags: vim
layout: post
---

Anyone who as looked at my [vim config][0] knows I rely on quite a list of
plugins.  While vim has an excellent plugin system, it fails to have an
excellent plugin management system.  There are a few scripts out there that
attempt to fill this void.  I have not used them all, but these are the ones
I've heard of:

 * [vim-addon-manager][3] ([github][4])

 * [vimana][5] ([github][6])

 * [pathogen][1] ([github][2])

Being the stubborn ass that I am, I refused to use these types of scripts for a
long time.  I had my own home-baked solution of putting every plugin in it's
own subfolder and manipulating the `runtimepath` to include these folders.
This kept my vimdir rather clean and allowed me to do a few fancy things such
as keeping git-hosted plugins as submodules of my dotfiles repo.  Doing so
allowed me to update all git plugins from their origin with one easy command.

As it turns out, this is essentially how pathogen works.  An added bonus with
pathogen is that it provides a few functions to generate helptags for all
plugins that include a `doc` directory.  This is something my manual method
never did and was always a pain in the ass to do.  As a result, I have now
switched to pathogen, and I recommend anyone looking for a clean solution to
vim plugins to do the same.

However, I have found a downside to pathogen for those of us stuck in the stone
ages.  In order to use it, you must be running vim7.  This means that when
running vim6 pathogen will fail, and any plugins you have that should be loaded
for vim6 will not be loaded, unless you manually load them.  This wasn't a
problem previously as I was already appending to `rtp` for every plugin and had
version tests around each plugin's settings.  Below are a couple of snippets
from my [vimrc][8] that show how I have configured pathogen and [TagList][7] to
play well together in both vim6 and vim7.

Set up pathogen (update)

{% highlight vim %}
silent! call pathogen#runtime_append_all_bundles()
filetype off
{% endhighlight %}

Configure TagList

{% highlight vim %}
if v:version >= 600
    " Taglist
    if v:version < 700
        " Pathogen doesn't work with
        " vim 6 but Taglist does
        set rtp+=~/.vim/plugin-git/taglist
    endif

    " TagList options
endif
{% endhighlight %}

If anyone knows of a cleaner way to deal with this sort of setup on both vim6
and vim7 I'd love to hear it.  I personally find this two part solution
atrocious.

[0]: http://github.com/rson/dotfiles/blob/master/vim/
[1]: http://www.vim.org/scripts/script.php?script_id=2332
[2]: http://github.com/tpope/vim-pathogen
[3]: http://www.vim.org/scripts/script.php?script_id=2905
[4]: http://github.com/MarcWeber/vim-addon-manager
[5]: http://search.cpan.org/dist/Vimana/
[6]: http://github.com/c9s/Vimana
[7]: http://www.vim.org/scripts/script.php?script_id=273
[8]: http://github.com/rson/dotfiles/blob/master/vim/vimrc
