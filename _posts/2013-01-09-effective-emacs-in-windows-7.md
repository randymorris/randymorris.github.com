---
title: Effective Emacs in Windows 7
tags: emacs windows
layout: post
---

There are many posts around the web about how to run Emacs in Windows.  While
many of these suggest building and running a native version of Emacs, many
others suggest running the version available through [Cygwin][].  I tried both
approaches many times but always ran into problems with the packages that I use
most often.  On top of that I was plagued with slowness that just isn't there on
other platforms.  The good news is I've found a happy medium that works quite
well for me and this post documents that monster I've created.

## What I wanted

My goals for this setup were to make Emacs run on a "remote" machine
and display on my local Windows install.  I also wanted this to be as
seamless as possible so that it felt as if I was running a native
application.  To do this I needed quite a bit of supporting software.

## An Emacs host

I used a Linux host, specifically a VirtualBox VM running a minimal Ubuntu
server install.  Your host is going to need to have an opensshd and X11
installed, with X11 forwarding enabled in `sshd_config`.  Anyone
reading this guide is probably already very familiar with these steps
so I'll leave out the details.

I wrote a couple of scripts help make running a VM more bearable.  This
is VirtualBox specific, but I'm sure it can be adapted to other
virtualization solutions.

file: `EmacsHost.bat` {% highlight bat %}
@echo off
"C:\Program Files\Oracle\VirtualBox\VBoxHeadless.exe" -s EmacsHost
{% endhighlight %}

This batch file launches the VM named "EmacsHost" in headless mode.
This means the only access to the machine is through remote services
like ssh or vnc.  Unfortunately, because it's batch, this leaves a
command prompt hanging around.  To get rid of that I used a bit of
VBScript.

file: `EmacsHost.vbs` {% highlight vbnet %}
set WshShell = WScript.CreateObject("WScript.Shell")
obj = WshShell.Run("c:\path\to\EmacsHost.bat", 0)
set WshShell = Nothing
{% endhighlight %}

Running `Emacs.vbs` runs `EmacsHost.bat` in a subprocess and kills off
the parent shell.

I finished off the VM setup by having `EmacsHost.vbs` run on boot so
it is always running whenever I attempt to run Emacs.  The VM is tiny
so it starts up immediately and I don't worry about powering it off as
there isn't much to lose on the machine itself.

## PuTTY and friends

The [PuTTY][] project is a set of Windows applications that allow you
to connect to remote machines via a number of protocols.  You can
download the two specific applications you'll need directly but I
strongly suggest downloading the installer for simplicity's sake. From
this project I used `PuTTYgen` to set up the ssh certificates and
`plink` to make the connection to launch Emacs.

Unfortunately PuTTY's certificates are incompatible with openssh and
there is some work that needs to be done to make a private/public key
pair that will work between the machines.  There are many resources on
setting up these certificates so I won't go into details here.  Later
I reference the private key on Windows as "EmacsHostKey.ppk".

## An X11 server

In order to have Emacs display on your Windows machine you will need
to be running an X11 server.  I chose [Cygwin/X][] since I had
Cygwin installed for other reasons already.  I also chose to launch
the X server on startup at the same time as my VM, for the same
reasons.

## Putting it all together

To wrap things up I wrote a couple of scripts to make launching Emacs
convenient.

file: `Emacs.bat` {% highlight bat %}
@echo off
plink -l user -X -i c:\path\to\EmacsHostKey.ppk localhost "emacsclient -c -a ''"
{% endhighlight %}

file: `Emacs.vbs` {% highlight vbnet %}
set WshShell = WScript.CreateObject("WScript.Shell")
obj = WshShell.Run("c:\path\to\Emacs.bat", 0)
set WshShell = Nothing
{% endhighlight %}

With a running X server and a running VM, double clicking on
`Emacs.vbs` in an Explorer window will launch emacsclient on the VM
and display it on the Windows machine..

## What's left?

One slight annoyance is that pinning Emacs to the taskbar doesn't work
as expected.  With Cygwin/X, pinning it actually pins an Xwin instance
to the taskbar and clicking this doesn't launch Emacs.  To fix this I
found an odd workaround somewhere on the [Emacs Wiki][]:

1. Right click on the pinned XWin icon on the taskbar.
2. Right click on the Xwin entry at the top of the popup menu.
3. Select properties option.
4. Modify the "Target" field to point to `Emacs.vbs`.
5. Optional: Select the "Change Icon" button and select an Emacs icon file.
6. Optional: Select the "General" tab.
7. Optional: Modify the first field to be "Emacs" instead of "Xwin".

After a reboot (or restart of explorer.exe) the pinned Emacs icon
functions just as any other pinned application.

## The result

After following these steps I'm left with is an Emacs that behaves as
though it is a native Windows application without the slowness or
incompatibilities I ran into with a native Emacs build.

## Notes

* I haven't done anything new here.  This is the result of smashing
  ideas together that I found through months of searching for
  solutions for my frustrations.  I intend on attempting to credit
  peices of this as I have time to try to find the original sources.
  I would be very surprised if all of this information can't be found
  on [StackOverflow][] or [the wiki][Emacs Wiki]

* I chose to run Emacs in daemon/client mode but that's totally
  optional.  Just change "emacsclient" to "emacs" if you don't want
  this behavior.

* You don't really need to run a VM if you have access to a unix
  host. Theoretically, running a VM greatly reduces network lag and
  makes Emacs feel much more snappy but I have yet to try a true host
  in practice.

* I actually have taken this a step further and set up a folder that
  is shared between EmacsHost and my Windows installation.  This
  allows me to access my files from other applications in Windows if
  need be.  I'll leave this as an exercise for the reader.

If you have any questions or suggestions on how I could improve either this
setup or the guide itself speak up.

[Cygwin]: http://www.cygwin.com/
[PuTTy]: http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html
[Cygwin/X]: http://x.cygwin.com/
[StackOverflow]: http://stackoverflow.com/
[Emacs Wiki]: http://emacswiki.org/
