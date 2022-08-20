---
title: "The Beauty and Beastie"
date: 2021-09-04T14:19:08+02:00
ShowToc: true
---
As I mentioned in my last article I have a FreeBSD box running FTP as a file
server. I use for my personal media, source codes, scripts and share it like
this between all my other computers. While this site is (as of yet) running on
Debian I have considered FreeBSD to be much more pleasant on the server side of
things.

I have however never run FreeBSD as a daily driver desktop and decided that it
was time to give that a go.

## My history with *BSD

Quite some time after using Linux, actually realising that it is GNU/Linux and
what GNU is and the entire history of UNIX-like systems have I found out about
BSD (Berkeley Software Distribution). It was an operating system which soon
spawned a number of descendant systems. FreeBSD being one of them.

There are of course many other but three others in particular I consider worth
mentioning OpenBSD, NetBSD and DragonflyBSD. Dragonfly focuses on
multi-threaded performance and was forked from FreeBSD over a dispute about it.
It also uses a modern file-system called HAMMER. I personally never used it.
Then there is NetBSD which focuses on clean code and portability to many
architectures being used in embedded devices frequently. I also have never used
it. Then there is OpenBSD which was forked from NetBSD and its first and
foremost goal is security. They make the system secure to the point of being
unusable sometimes.  Multi-threading is disabled by default, the kernel is
re-linked randomly every time to avoid exploits and so on. I did run it for a
little while on my thinkpad laptop but the lack of software and the performance
made me jump right back after about a month.

## Why FreeBSD?

I believe that it is the most supported and most suited to be used as a desktop
out of all of the *BSDs. Why use BSD over GNU/Linux? My biggest reason is
probably simplicity. Not as in user friendliness but the pure essence of UNIX.
Keeping it simple to the core.

### Init system

I don't exactly hate SystemD as some people do. It can be pretty decent for
some very intricate server stuff. But for the majority of things it is an
absolute overkill and I'll gladly take something else. FreeBSD uses a very
simple and minimalist init system called just 'init'. It uses scripts located
in the '/etc/rc.d' folder and simply starts processes as it is supposed to do.
It does very little else. There is simple script called 'service' used to
control different services and that's it.

### Directory hierarchy

The directory hierarchy in GNU/Linux can be a little messy at times. It is not
quite so bad as to interfere with work but after seeing the BSD hierarchy it
certainly leaves a bit to be desired. There is a total of 44 files in the
FreeBSD '/bin' folder. Only the absolutes necessities to keep the system
running. The rest can be found in '/usr/bin' and '/usr/local/bin' where all the
user executables are kept. Does this actually improve anything? Not by much but
it is much cleaner an everything has its place.

## It's basically like Linux, right?

Well yes and no. For the most part it will feel very familiar but it is the
little differences that can knock you out of the balance sometimes.

### Where there's a shell, there's a way

True enough as FreeBSD runs a rewrite of the original Bourne Shell. You might
be familiar with the Bourne Again Shell or bash for short. Well this is sh. The
portable POSIX shell in all its glory. There is also csh or C Shell out of the
box. While I find sh to be quite enough for me even for interactive use I can
understand some people might want more comfort. It is of course very easy to
install others: Bash, Zsh and should you want it Fish (God forbid). Speaking of
which...

### Package management

The FreeBSD package manager is called 'pkg'. To install a package you type 'pkg
install name' to search 'pkg search name' to remove 'pkg remove name'. You get
the idea. As simple as it gets. It also features the classical UNIX Ports tree.
What is it? If you ever used Gentoo or anything similar this might be a bit
familiar. There is a directory in the hierarchy called '/usr/ports'. It
contains a bunch of Makefiles and Check sums and the like. It contains recipes
on how to obtain packages ported over to FreeBSD. Let's say I want to install
neovim. I go to the '/usr/ports/editors/neovim' directory and as the root user
simply call 'make' and 'make install'. This will fetch all the source codes and
source codes for dependencies unless installed and compiles them. Prior to that
it prompts you about certain option you might want to tweak (such as whether or
not to include support for plugins written in python) and you're done. Well
after you compile it of course which might take time. But you can be sure that
there is nothing wrong with the binary since you compiled a trusted source code
yourself. It can also have other benefits such as better optimisation for your
particular architecture and excluding features you won't use anyway. Great now
you know to install software. But what is there to install?

## Software availability

I have not had any issues in this regard but then again I am not that difficult
to please. I mostly use terminal applications which are ported to just about
anything. But should you want it is possible to get GNOME or KDE Plasma running
without too much hassle. The majority of software is ported to FreeBSD and it
is usually not too difficult to port it. If well written it might be as little
as modifying some paths in Makefiles. Also FreeBSD should now be Linux binary
compatible meaning that you can run Linux binaries natively. To do that you
have to tweak a few things but is very well documented as most things in BSDs.

### How about games?

Let's address the elephant in the room. Can it run Steam? Well it should be
possible through the Linux binary compatibility layer. I haven't tried it
myself as I was not using it even under GNU/Linux as I barely play anything
anymore. If I do it is usually some (usually old) RTS or FPS and it does run
open-source quake and doom engines quite fine and for some newer stuff there is
0 A.D. and I care very little about anything else.

## My Favourite Features

### Documentation

The level of documentation on all BSD systems is something to strive for in all
software projects in my opinion. The manual pages are well written and on point
since people actually depend on them rather than searching how to do something
on the Internet. There is also the FreeBSD handbook that contains very useful
information on just about anything you might want to do. It is surprisingly
detailed and focuses on just about anything even a complete beginner to UNIXes
might be confused about. It includes a very detailed walk-through of the
installation and anything you might want to do after that.  It even includes
information about what is a shell, how to use it, file permissions and much
more. I dare say if you don't mind reading manuals FreeBSD might even be more
approachable than some of the minimalist GNU/Linux distributions. You will
learn more this way in my opinion anyway.

### Let's put VS Code where it belongs... in a jail

FreeBSD has this neat feature called jails. Those are basically containers
before everybody was using them. Or lightweight Virtual Machines. You run a
programme inside chroot environment limiting its access to the file-system. It
is a way to make programmes even more secure. I personally haven't used it yet.
But I might pretty soon. Oh and please do not run VS Code in a jail. Do not run
it period.

### The Z File-system

FreeBSD Has really good support of a very modern file system called ZFS. It
uses balanced trees and has amazing support for software raid. It contains many
very advanced methods for managing the file-system such as deduplication which
reduces the necessary space if storing more copies of the same or very similar
file (This can be for example very useful for mail servers and group e-mails).
It is very easy to work with. Do backups, hot-swap drives and so on. It is
based on the file-system originally developed by Sun Microsystems.

> Have a great day and keep computing fun.
