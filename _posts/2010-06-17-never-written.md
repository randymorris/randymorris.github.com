---
title: Never Written
tags: ideas window-management
layout: post
---

Over the past few years I have been exclusively running a tiling window
manager of some flavor.  I've tried just about every major player out there for
at least a week or two before moving on but I still feel there is a niche that
has yet to be filled.  As any hobbiest would do, I drafted a rough plan
for a new window manager based on some major principles found elsewhere
and vowed that one day I would write this perfect window manager and share it with the
world.

Today I present to you -- *the best window manager never written*.

For a bit of background, there were four major influences on my idea.
Each of these window managers played a key role in deciding what the
perfect setup would be.

 1. [Ratpoison][1] - Ratpoison is a manual tiler that handles windows more or less
    like vim handles them.  If you haven't used it before but are familiar with
    vim's window vs. buffers paradigm, you'd be very comfortable with the way
    Ratpoison works.  Ratpoison also has a command line interface that allows you
    to send arbitrary [commands][11] to it at runtime though any scripting language of
    your choice.  This is huge.

    The downside with Ratpoison is that it's keybinds are modeled after
    gnu-screen.  Every command dealing with widow management has an escape key
    that must precede it.

 2. [Dwm][2] - The main concept that should be ripped from Dwm is tagging.  This
    might not have been a new feature with Dwm, but it was my first exposure to
    this concept.  Windows are 'tagged' rather than placed into 'groups'
    or 'workspaces'.  Any set of tags can then be selected, displaying all windows with any 
    of these tags.

    My main gripe with Dwm is that it's not a manual tiler.  Any time I use Dwm
    nowadays I feel like I get lost because my windows are shuffling around all
    over the place on their own.  Manual tiling just suits me better.

 3. [Xmonad][3] - This window manager gets one thing incredibly right:
    extensibility.  I have yet to find a window manager that makes it this easy
    to write new layouts and plugins for.  By far Xmonad users seem the most
    content with their window manager out of all the communities I've interfaced
    with.

    Xmonad is also an automatic tiler.  There was [one][31] attempt at writing a
    manual layout (that I've found), but the author never got it to a fully
    functional state.

 4. [Musca][4] - This window manager is the closest I've used to one that Gets It Right&#0153;.  Musca
    has the same manual tiling paradigm as Ratpoison, but it throws in a few
    special types of frames as well, such as [dedicated frames][41] to catch all new
    windows in.  It also has a scripting interface to send [commands][42] in the same vein 
    as Ratpoison.

    There are currently a few outstanding major bugs with Musca according to the
    [Arch Musca thread][43].  This isn't a big deal, however
    development has slowed considerably in the past six months or so.  My other
    issue with Musca is that it uses dmenu for every command rather than
    implementing it's own command entry system.  This is normally a concept I
    agree with, however in this case I feel having a Ratpoison-esque command bar
    with command history et al. is the better solution.

From my experience with the above, I came up with a set of features my
ideal window manager would have.  They were chosen mainly for my own
purposes but I feel that this specific feature set gives the user the
most control while not sacrificing flexibility.  The overall concept can
be summed up in a few major points:

 * Written in Python.  I am most comfortable writing larger applications in Python and I feel Python is one of the easiest languages to read and follow.  I do have some speed concerns that would need
   to be properly tested before really standing behind this decision, but there is at least [one][100] window manager out there written in Python already.

 * Manual tiling.  Vim gets this right.  Ratpoison gets this right.  Stick with
   what works well.  Even the navigation is similar between the two.

    To put it into vim terms, the entire screen is manually split into a series of frames (windows in vim).  X clients are handled as buffers.  You navigate to the frame you want to be in, then swap to the specific window you want to see.  Simple and very effective.

 * Tags, not groups.  Tags allow you to group windows more efficiently without
   losing the ability to have 'workspaces' if that's what you'd rather that have.

 * Extensibility.  Adding layouts and other simple features should not be
   difficult and should not affect the core window management.  End users should
   be able to do this rather easily.

 * Command bar with history.  Basically mimic Ratpoison here.  Having a command
   history makes working with your window manager so much easier.

 * Special frame types.  Extend on Musca's concept of catchall
   frames.  These are very convenient, especially in a multi-monitor
   environment.  Also provide a tabbed frame type for use with minimalist
   browsers and/or terminals that don't provide tab functionality within them.

 * Multi-monitor support.  A window manager without *good* multiple monitor
   support is useless these days.  Allow monitors to have exclusive sets of tags
   such that one can move a window from one screen to another simply by changing
   it's tags.

 * Optional floating layer.  Everyone has that one application that doesn't play
   well with tiling window managers.  Personally, I just deal with it.  That's
   not how it should be handled.

In my opinion, this is a great idea.  Of course it's a great idea, it's
my idea.  But then again, it's not.  It's just a collection of the best
ideas that have already been implemented elsewhere.  For me, these
specific features are the coreutils of the window manager world.

If you feel the same way and you have the time, please take this idea
and run with it.  If you do, **get me involved** so I can help design
and test with you.  Unfortunately the reason it is still a concept is
because I have almost no free time these days and the last thing I want
to do in my free time is frustrate myself with such a large undertaking.

If you don't feel the same way, leave a comment and let me know why I'm
wrong.  Maybe our ideas can merge together and form some super mutant
window manager that will never be written.  Maybe not.

[1]: http://www.nongnu.org/ratpoison/
[11]:  http://nongnu.org/ratpoison/doc/Command-Index.html
[2]: http://dwm.suckless.org/
[3]: http://xmonad.org/
[31]: http://hpaste.org/fastcgi/hpaste.fcgi/view?id=11526
[4]: http://aerosuidae.net/musca/
[41]: http://aerosuidae.net/musca/Commands#catchall
[42]: http://aerosuidae.net/musca/Commands
[43]: http://bbs.archlinux.org/viewtopic.php?id=67104
[100]: http://www.qtile.org/
